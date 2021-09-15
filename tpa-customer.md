# TPA Customer Batch

TPA Customer will extract changed insureds and generate document insert into db.

## Basic Info

- Job ID: `1468`
- FES Job ID: `4`
- Main Entrance: `com.ebao.ls.fes.interfaceFile.TPACustomerAutoUploadBatch.mainProcess`

## Parameters

Batch has 2 parameters: `startTime`, `endTime`. Batch will extract related insured by these two time.

For production, `endTime` is batch process date (dd-MM-yyyy), `startTime` is last batch execute time(dd-MM-yyyy). For
example, today is 2020/1/5, startTime will be 04/01/2020 and endTime will be 05/01/2020. However, the actual logic is
not as simple as it is(it should be), the logic is very stupid and cannot explain. Please check source
code`com.ebao.ls.fes.interfaceFile.TPACustomerAutoUploadDAO` for detail.

## Main Workflow

1. Get last batch process time
2. Query db, generate file and insert into db.
3. Update last batch process time to current time.
4. Update `T_TPA_CUSTOMER_EXTRA` extracted flag. See [GLS_CLM_02](#gls_clm_02-add-new-tpa-customer-extraction-rule) for
   detail.

The extraction logic is:

1. Query policies which is inforcing and policy change that meet the condition.
2. Query all insureds for these policies
3. If a policy has a policy change, then only insureds changed in policy change will be extract. If a policy has no
   policy change, all insureds in the policy will be extracted (NB).

## Change Requests

### GLS_CLM_02 Add New TPA Customer Extraction Rule

DLA Request to extract customer and all inforcing policies when add/delete/modify a customer's payment method. Check CR
Form for more detail.

## Potential Defect

As extraction logic described in [Main Workflow](#main-workflow), if a policy has a policy change, then only insureds
changed in policy change will be extract. So if a policy inforced and in the same day, a insured is changed by policy
change or change insured payment method, only this insured will be extracted and all other insureds in the policy will
not be extract.

Solution:
Treat NB insureds as same as cs insureds.

## Future

To prevent mud code goes on, we add a new column for future use. For further extraction rules, please insert the table
instead of adding more conditions to sql in `com.ebao.ls.fes.interfaceFile.TPACustomerAutoUploadDAO`.