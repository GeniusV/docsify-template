## Log

For a normal log, use slf4j logger is ok.

GLS can also record log into table `T_BATCH_LOG` with a run id `0`.  


To insert logs into the table, use PLSQL: `pkg_pub_scd_ci.p_log_info()`.  
Also in java:  `com.ebao.pub.batch.util.BatchLogUtils.addLog(java.lang.Integer, java.lang.Integer, java.lang.String)`.
```java 
BatchLogUtils.addLog(LogLevel.DEBUG, null, "TPA down start...");
```


## Handle Exception
## Test

### Unit Test

GLS does not include unit test by default. It is recommended to create another project and put gls in classpath to do
unit test.

### Integration Test

GLS seem has no way to do Integration test outside project. Solution is to create test servlet to do the test.  
However, self-created will be blocked by access control, so a modification is required.  
Modify `com.ebao.life.bean.system.access.AccessControl.getAccessType` to return `2` as follows.

``` java 
private static int getAccessType(String sUrl) {
if (!sUrl.equals("")){
  return 2;
}
int accessType = 1;
try{
  UrlTypeCacheAll cache = UrlTypeCacheAll.getInstance();
  Object value = cache.get(sUrl);
  if (value!=null){
  accessType = Integer.parseInt((String)value);
}

}catch(Exception e){
  e.printStackTrace();
}


return accessType;
}
```











