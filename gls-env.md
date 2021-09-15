<!-- MarkdownTOC -->

- [External Env](#external-env)
    - [VPN Info](#vpn-info)
    - [DLA SFTP](#dla-sftp)
    - [GLS Pre-production External](#gls-pre-production-external)
    - [GLS UAT External](#gls-uat-external)
    - [GLS SIT External](#gls-sit-external)
    - [GLS Production](#gls-production)
    - [DR SIT](#dr-sit)
    - [DR SIT \(Deprecated Before 2021-08-06\)](#dr-sit-deprecated-before-2021-08-06)
- [Internal Env](#internal-env)
    - [GLS Package SFTP](#gls-package-sftp)
- [Quick Commands](#quick-commands)

<!-- /MarkdownTOC -->

# SVN Branch

|Branch Name|BranchAddress|
|-----------|------------|
|DLA_GLS_DEV|http://svnedgemercury.ebaotech.com/svn/seg_gls/branches/DLA_GLS_DEV|
|DLA_GLS_UAT|http://svnedgemercury.ebaotech.com/svn/seg_gls/branches/DLA_GLS_UAT|
|DLA_GLS_PROD|http://svnedgemercury.ebaotech.com/svn/seg_gls/branches/DLA_GLS_PROD|
|DLA_GLS_Front|http://svnedgemercury.ebaotech.com/svn/seg_gls/branches/DLA_GLS_Front|

# External Env

## VPN Info

- IP：110.170.202.114
- Normal, for external preprod, uat, sit.
    + username: `ebao10`
    + password: `ux?uv8XB&Y`
- GLS Production only
    + username: `ebaoprod2`
    + password: `C0re!n$urance`

- GLS Production Cyberark
    + username: `ebaopam1`
    + password: `CyberarkEba01`

| |GLS|Production|    
|---|---|---|
|username|ebao10|ebaoprod2|
|password|ux?uv8XB&Y|C0re!n$urance|

## DLA SFTP

- ip: `192.168.112.181`
- username: `ebaoftp`
- password: `csKQg7zh`

## GLS Pre-production External

- App Server
    - ip: `192.168.111.13`
    - username: `oracle`
    - password: `P@ssw0rd`
    - path: `/u01/oracle/Middleware/Oracle_Home/user_projects/domains/base_domain`
    - App url: `http://192.168.111.13/life/index.jsp`
- Oracle
    - Oracle Info
        - url: `jdbc:oracle:thin:@192.168.111.51:1521:glspre`
        - username: `dla_gls_pre`
        - password: `dla_gls_prepwd`

## GLS UAT External

- App Server
    - ip: `192.168.111.23`
    - username: `oracle`
    - password: `P@ssw0rd`
    - deploy app path: `/u01/oracle/Middleware/Oracle_Home/user_projects/domains/base_domain/deploy`
- Oracle
    - jdbc: `jdbc:oracle:thin:@192.168.111.51:1521:glsuat`
        + username: `dla_gls_uat`
        + password: `8twxkdKp`
    - ssh: `192.168.111.51`
        + username: `oracle`
        + password: `P@ssw0rd`
        + db package deploy path: `/u01/ebao/db-deploy`
        + backup scrpt path: `u01/ebao/expdp/backup_gls_uat.sh`

## GLS SIT External

- App Server
    + ip: `192.168.112.12`
    + username: `oracle`
    + password: `P@ssw0rd`
    + deploy path: `/u01/oracle/Middleware/Oracle_Home/user_projects/domains/base_domain/deploy`
- Oracle
    - jdbc: `jdbc:oracle:thin:@192.168.112.51:1521:sitdb`
        + username: `dla_gls_sit`
        + password: `dla_gls_sitpwd`
    - ssh: `192.168.112.51`
        + username: `oracle`
        + password: `P@ssw0rd`
        + db package deploy path: `/u01/ebao/db-deploy`
- Print Server
    - ip: `192.168.111.61`
    - username: `Administrator`
    - password: `P@ssw0rd`

## GLS Production

- App 33: `192.168.3.33`
    - username: `oracle`
    - password: `M#165red@@`
- App 34: `192.168.3.34`
    - username: `oracle`
    - password: `M#165red@@`
- JDBC: `jdbc:oracle:thin:@192.168.3.51:1521:glsdb`
    - username: `dla_gls_prod_read`
    - password: `dla_gls_prod_read_only`

## DR SIT

- ESXi Test Server
    - IP: `172.28.130.210`
    - OS Admin
        + Username: `root`
        + Password: `P@ssw0rd`
- GLS (VM) - SUCGL001
    - IP: `172.28.130.211`
    - Oracle Web Logic Console
        + Username: `Weblogic`
        + Password: `welcome1`
- FTP (VM) - uftpebao.dhipayalife.co.th
    - IP: `172.28.130.213`
    - Username: `ebaoftp`
    - Password: `csKQg7zh`
- DB Server (VM) - SUCDB001
    - IP: `172.28.130.214`
    - Username: `oracle`
    - Password: `P@ssw0rd`
    - JDBC: `jdbc:oracle:thin:@172.28.130.214:1521:sitdb`
        + Username: `dla_gls_sit`
        + Password: `dla_gls_sitpwd`
- Output Server (VM) - SUCOP001
    - IP: `172.28.130.215`
    - Username: `administrator`
    - Password: `P@ssw0rd`

## DR SIT (Deprecated Before 2021-08-06)

- GLS (VM) - DSCGL001 DSCGL001
    - ip: `10.2.1.113`
    - username: `root`
    - username: `oracle`
    - password: `P@ssw0rd`
- DR Site - App Server (GLS (VM) - DSCGL002)  DSCGL002
    - ip: `10.2.1.123`
    - username: `root`
    - username: `oracle`
    - password: `P@ssw0rd`
- DR Site - DB Server DSCDB001
    - ip: `10.2.1.131`
    - username: `root`
    - username: `oracle`
    - password: `P@ssw0rd`
- Database name:glsdb DSCDB001
    - url: `jdbc:oracle:thin:@10.2.1.131:1521:glsdb`
    - username: `dla_gls_prod_app`
    - password: `dla_gls_prod_app_only`
- DR Site - Output Server DSCOP001
    - ip: `10.2.1.151`
    - password: `administrator`
    - usename:` P@ssw0rd`

# Internal Env

## GLS Package SFTP

- ip: `172.25.32.60`
- username: `dlals_ftp`
- password: `dlals_ftp`

## GLS Prod Test

- ip: `172.25.15.154`
    - username: `dla_gls_prod_test`
    - password: `dla_gls_prod_test`
- jdbc: `jdbc:oracle:thin:@172.25.14.29:1521:c29u1`
    - username: `dla_gls_prod_test`
    - password: `dla_gls_prod_testpwd`

# Quick Commands

``` bash
cd EBAO_HOME/batch/
sh EBAO_HOME/batch/restart_batch.sh
tail EBAO_HOME/batch/agent1.out -f
```