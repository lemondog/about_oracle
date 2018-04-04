## oracle基础 
SQL语句，执行计划以及解析树都放在共享池的库缓冲区中，如果库缓存过小，sql执行计划和解析树转储到缓存外面，导致频繁的将sql语句重新加载到库缓存中。

重做日志缓冲区使用1/3或者间隔3秒刷新到重做日志。从10G开始，只要缓冲区使用到1MB时LGWR就开始刷新。

默认最大sessions数量：```<1.1*processes+5>```

truncate表后，表object_id不变，但data_object_id会变化，即段的id会发生变化。

删除后的回滚不改变原来行的位置

- logminer使用流程：
```
execute dbms_logmnr_d.build('dic.ora','/tmp'); 
execute dbms_logmnr.add_logfile('/u01/app/oracle/log_3_3.log');
execute dbms_logmnr.start_logmnr('/tmp/dic.ora');
execute dbms_logmnr.add_logfile('/u01/app/oracle/log_3_3.log',options=>dbms_logmnr.removefile);
```
- oracle启动参数文件寻找顺序:`spfileSID->SPFILE->initSID->默认PFILE`
