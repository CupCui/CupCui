---
layout: post
title: 问题 查询数据时数据量过大导致GC内存泄漏日志, java.lang.OutOfMemoryError GC overhead limit exceeded
categories: ERROR
description: 问题 查询数据时数据量过大导致GC内存泄漏日志, java.lang.OutOfMemoryError GC overhead limit exceeded
keywords: ERROR, OutOfMemoryError, GC
---


#### 问题: 查询数据时数据量过大导致GC内存泄漏日志, java.lang.OutOfMemoryError: GC overhead limit exceeded

**[GC]** **[OutOfMemoryError]** **[ERROR]**

问题: 使用fastjson解析时内存泄漏,java.lang.OutOfMemoryError: GC overhead limit exceeded

原因: 单次查询ES中数据量过大,使用fastjson解析时内存泄漏

解决: 1. 修改单次查询分页大小 2. 增加heap堆内存

```json
// GC异常内存泄漏日志
2022-12-07 14:25:19.783 [33mINFO [0;39m -- [ttp-nio-45560-exec-5] [32mnV01ResFullTextQueryController[0;39m [34m       getResCascade: 102[0;39m: 根据条件获取资源====query/allRes参数为：start getResCascade param=={"accurateParams":{},"includeSubRegionRes":false,"includeSubSysRes":false,"mateParams":{"resTypeId":["USER","MOD_IPV4","MOD_ADDRESS_SEGMENT_DICTIONARY","MOD_HWC_MO6_NETPORT","MOD_HWC_MO6_ELCARD","MOD_VMWARE_VM","MOD_ROUTER","MOD_5GC_CLOUDONE","MOD_HWC_MO6_ELVOL","MOD_HWC_MO6_OPTPORT","MOD_HOST_PC","MOD_HWC_MO6_MEM","MOD_FC_VIRTUAL_DISK","MOD_NET_INTERFACE","MOD_HWC_MO6_LUN","MOD_LISTENPORT","MOD_KFK_LAG","MOD_DEV_MODEL","MOD_TENCENTCLOUD_CVM","MOD_HWC_MO6_ELSVR","MOD_HWC_MO6_FAN","MOD_HWC_MO6_DISK","MOD_TENCENTCLOUD_SECURITYGROUP","MOD_COTS_SOFTWARE","MOD_FC_VSP","MOD_FC_VIRTUAL_HOST","MOD_MIS_CLOUDHOST","MOD_H3CiMC_SWITCHIF","IPResPoolNum","MOD_CABINET","MOD_RES_SWITCH","MOD_FLINK_TASKMNG","MOD_BUSI_SYS","MOD_HWC_MO6_CPU","MOD_UNIX_LINUX","MOD_VIMSCLOUD_ZHONGXINGNUOJIYA","MOD_TEMPE_SERSOR","MOD_APP_SERV","MOD_APP_CLUS","MOD_HWC_MO6_DEVBOARD","MOD_FLINK_JOB_VERT","MOD_HWC_MO6_POWER","MOD_HWC_MO6_LINK","MOD_NET_SLOT","MOD_SWITCH","MOD_HOST_PORT","MOD_HWC_MO6_FCZONE","MOD_BUS_ADDRESS","MOD_RACK_SERV","MOD_CLOUDTWO_ZHONGXINGNUOJIYA","MOD_DES_DATA","MOD_HWC_MO6_VMSPECIFIC","MOD_HWC_MO6_NETCARD","MOD_MEC_VM","MOD_TENCENTCLOUD_CLB","MOD_HWC_MO6_VM","MOD_HOST_MIN","MOD_FILE_SYS","MOD_HWC_MO6_FCPORT","MOD_HWC_MO6_PHYHOST","MOD_MYSQL_DB","MOD_ORG_DATA","MOD_ORACLE_TABLE_SPACE","MOD_BUSI_ALERT","MOD_K8S_POD","MOD_CARD","MOD_TENCENTCLOUD","MOD_HWC_MO6_SVR","MOD_HWC_MO6_BOARD","MOD_H3CiMC_SAFEIF","MOD_HWC_MO6_VMIMAGE","MOD_HWC_MO6_VMNETCARD","MOD_CPU_NM","MOD_DISK_ARRAY","MOD_VLAN_INFO","MOD_BLADE_BOX","MOD_TENCENTCLOUD_MYSQL","MOD_FLINK_JOB_VERT_SUB","MOD_PROCESS","MOD_DIM_VENDORS","MOD_IPV6","MOD_HWC_MO6_PORT","MOD_LOGICAL_HOST","MOD_CATEGORY","MOD_NET_OPTICAL","MOD_IP_POOL","MOD_REDIS_NODE","MOD_LINK","MOD_ACC_PRN_DEVICE","MOD_FC_PORTGROUP","MOD_TENCENTCLOUD_CKAFKA_TOPIC","MOD_VMWARE_VDISK","MOD_TENCENTCLOUD_CLB_LIS","MOD_K8S_SERVICE","MOD_IPV4_ADDRESS","MOD_TENCENTCLOUD_REDIS","MOD_SAFETY_DEVICES","MOD_FLINK_JOB","MOD_VMWARE_VIRNETCARD"]},"mustExists":[],"needExt":false,"notExists":[],"pageNo":1,"pageSize":100000,"rangeParams":[],"sortStr":"","userAcc":"root"}
2022-12-07 14:31:17.696 [33mERROR[0;39m -- [ttp-nio-45560-exec-5] [32mra.cmdb.common.util.es.ES7Util[0;39m [34m  searchTotalAndData: 515[0;39m: 查询数据失败：com.alibaba.fastjson.JSONException: GC overhead limit exceeded
	at com.alibaba.fastjson.parser.DefaultJSONParser.parseObject(DefaultJSONParser.java:710)
	at com.alibaba.fastjson.parser.deserializer.MapDeserializer.parseMap(MapDeserializer.java:231)
	at com.alibaba.fastjson.parser.deserializer.MapDeserializer.deserialze(MapDeserializer.java:69)
	at com.alibaba.fastjson.parser.deserializer.MapDeserializer.deserialze(MapDeserializer.java:43)
	at com.alibaba.fastjson.parser.deserializer.ContextObjectDeserializer.deserialze(ContextObjectDeserializer.java:9)
	at com.alibaba.fastjson.parser.deserializer.DefaultFieldDeserializer.parseField(DefaultFieldDeserializer.java:88)
	at com.alibaba.fastjson.parser.deserializer.JavaBeanDeserializer.deserialze(JavaBeanDeserializer.java:858)
	at com.alibaba.fastjson.parser.deserializer.JavaBeanDeserializer.parseRest(JavaBeanDeserializer.java:1624)
	at com.alibaba.fastjson.parser.deserializer.FastjsonASMDeserializer_19_InnerHit.deserialze(Unknown Source)
	at com.alibaba.fastjson.parser.deserializer.JavaBeanDeserializer.deserialze(JavaBeanDeserializer.java:287)
	at com.alibaba.fastjson.parser.deserializer.ArrayListTypeFieldDeserializer.parseArray(ArrayListTypeFieldDeserializer.java:185)
	at com.alibaba.fastjson.parser.deserializer.ArrayListTypeFieldDeserializer.parseField(ArrayListTypeFieldDeserializer.java:71)
	at com.alibaba.fastjson.parser.deserializer.JavaBeanDeserializer.parseField(JavaBeanDeserializer.java:1278)
	at com.alibaba.fastjson.parser.deserializer.JavaBeanDeserializer.deserialze(JavaBeanDeserializer.java:893)
	at com.alibaba.fastjson.parser.deserializer.JavaBeanDeserializer.parseRest(JavaBeanDeserializer.java:1624)
	at com.alibaba.fastjson.parser.deserializer.FastjsonASMDeserializer_18_Hits.deserialze(Unknown Source)
	at com.alibaba.fastjson.parser.deserializer.JavaBeanDeserializer.deserialze(JavaBeanDeserializer.java:287)
	at com.alibaba.fastjson.parser.deserializer.DefaultFieldDeserializer.parseField(DefaultFieldDeserializer.java:88)
	at com.alibaba.fastjson.parser.deserializer.JavaBeanDeserializer.parseField(JavaBeanDeserializer.java:1278)
	at com.alibaba.fastjson.parser.deserializer.JavaBeanDeserializer.deserialze(JavaBeanDeserializer.java:893)
	at com.alibaba.fastjson.parser.deserializer.JavaBeanDeserializer.parseRest(JavaBeanDeserializer.java:1624)
	at com.alibaba.fastjson.parser.deserializer.FastjsonASMDeserializer_17_QueryResp.deserialze(Unknown Source)
	at com.alibaba.fastjson.parser.deserializer.JavaBeanDeserializer.deserialze(JavaBeanDeserializer.java:287)
	at com.alibaba.fastjson.parser.DefaultJSONParser.parseObject(DefaultJSONParser.java:705)
	at com.alibaba.fastjson.JSON.parseObject(JSON.java:394)
	at com.alibaba.fastjson.JSON.parseObject(JSON.java:298)
	at com.alibaba.fastjson.JSON.parseObject(JSON.java:588)
	at com.ultra.cmdb.common.util.es.ES7Util.doQuery(ES7Util.java:255)
	at com.ultra.cmdb.common.util.es.ES7Util.searchTotalAndData(ES7Util.java:494)
	at com.ultra.cmdb.dao.cmdb.EsDaoEs7Impl.getPageNodeByQueryJson(EsDaoEs7Impl.java:235)
	at com.ultra.cmdb.service.es.impl.ESServiceImpl.getPageNodeByQueryJson(ESServiceImpl.java:1516)
	at com.ultra.cmdb.service.es.impl.ESServiceImpl.queryResByUserIdV2(ESServiceImpl.java:831)
	at com.ultra.cmdb.service.es.impl.ESServiceImpl.getResListByParam(ESServiceImpl.java:1179)
	at com.ultra.cmdb.service.resource.ResFullTextQueryServiceImpl.getResCascade(ResFullTextQueryServiceImpl.java:378)
	at com.ultra.cmdb.service.resource.ResFullTextQueryServiceImpl$$FastClassBySpringCGLIB$$35469f9.invoke(<generated>)
	at org.springframework.cglib.proxy.MethodProxy.invoke(MethodProxy.java:218)
	at org.springframework.aop.framework.CglibAopProxy$CglibMethodInvocation.invokeJoinpoint(CglibAopProxy.java:793)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:163)
	at org.springframework.aop.framework.CglibAopProxy$CglibMethodInvocation.proceed(CglibAopProxy.java:763)
	at org.springframework.aop.interceptor.ExposeInvocationInterceptor.invoke(ExposeInvocationInterceptor.java:97)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:186)
	at org.springframework.aop.framework.CglibAopProxy$CglibMethodInvocation.proceed(CglibAopProxy.java:763)
	at org.springframework.aop.framework.CglibAopProxy$DynamicAdvisedInterceptor.intercept(CglibAopProxy.java:708)
	at com.ultra.cmdb.service.resource.ResFullTextQueryServiceImpl$$EnhancerBySpringCGLIB$$2a2361be.getResCascade(<generated>)
	at com.ultra.cmdb.web.controller.open.v01.OpenV01ResFullTextQueryController.getResCascade(OpenV01ResFullTextQueryController.java:106)
	at sun.reflect.GeneratedMethodAccessor920.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.springframework.web.method.support.InvocableHandlerMethod.doInvoke(InvocableHandlerMethod.java:205)
	at org.springframework.web.method.support.InvocableHandlerMethod.invokeForRequest(InvocableHandlerMethod.java:150)
	at org.springframework.web.servlet.mvc.method.annotation.ServletInvocableHandlerMethod.invokeAndHandle(ServletInvocableHandlerMethod.java:105)
	at org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.invokeHandlerMethod(RequestMappingHandlerAdapter.java:878)
	at org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.handleInternal(RequestMappingHandlerAdapter.java:792)
	at org.springframework.web.servlet.mvc.method.AbstractHandlerMethodAdapter.handle(AbstractHandlerMethodAdapter.java:87)
	at org.springframework.web.servlet.DispatcherServlet.doDispatch(DispatcherServlet.java:1040)
	at org.springframework.web.servlet.DispatcherServlet.doService(DispatcherServlet.java:943)
	at org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:1006)
	at org.springframework.web.servlet.FrameworkServlet.doPost(FrameworkServlet.java:909)
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:681)
	at org.springframework.web.servlet.FrameworkServlet.service(FrameworkServlet.java:883)
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:764)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:227)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162)
	at org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:53)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162)
	at com.ultrapower.msa.sdk.oauth.MsaAuthenticationFilter.doFilter(MsaAuthenticationFilter.java:77)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162)
	at com.ultra.cmdb.xss.XssFilter.doFilter(XssFilter.java:48)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162)
	at org.springframework.web.filter.RequestContextFilter.doFilterInternal(RequestContextFilter.java:100)
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:117)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162)
	at org.springframework.web.filter.FormContentFilter.doFilterInternal(FormContentFilter.java:93)
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:117)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162)
	at org.springframework.web.filter.CharacterEncodingFilter.doFilterInternal(CharacterEncodingFilter.java:201)
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:117)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162)
	at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:197)
	at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:97)
	at org.apache.catalina.authenticator.AuthenticatorBase.invoke(AuthenticatorBase.java:541)
	at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:135)
	at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:92)
	at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:78)
	at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:360)
	at org.apache.coyote.http11.Http11Processor.service(Http11Processor.java:399)
	at org.apache.coyote.AbstractProcessorLight.process(AbstractProcessorLight.java:65)
	at org.apache.coyote.AbstractProtocol$ConnectionHandler.process(AbstractProtocol.java:890)
	at org.apache.tomcat.util.net.NioEndpoint$SocketProcessor.doRun(NioEndpoint.java:1789)
	at org.apache.tomcat.util.net.SocketProcessorBase.run(SocketProcessorBase.java:49)
	at org.apache.tomcat.util.threads.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1191)
	at org.apache.tomcat.util.threads.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:659)
	at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:61)
	at java.lang.Thread.run(Thread.java:748)
Caused by: java.lang.OutOfMemoryError: GC overhead limit exceeded
2022-12-07 14:31:17 [ERROR](c.n.p.p.s.AgentConfigExecutor      ) UNAVAILABLE: Channel shutdown invoked
io.grpc.StatusRuntimeException: UNAVAILABLE: Channel shutdown invoked
	at io.grpc.stub.ClientCalls.toStatusRuntimeException(ClientCalls.java:222)
	at io.grpc.stub.ClientCalls.getUnchecked(ClientCalls.java:203)
	at io.grpc.stub.ClientCalls.blockingUnaryCall(ClientCalls.java:132)
	at com.navercorp.pinpoint.grpc.trace.AgentGrpc$AgentBlockingStub.requestConfig(AgentGrpc.java:272)
	at com.navercorp.pinpoint.profiler.sender.AgentConfigExecutor.execute(AgentConfigExecutor.java:104)
	at com.navercorp.pinpoint.profiler.sender.AgentConfigExecutor$RequestConfigThread.run(AgentConfigExecutor.java:92)
	at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
	at java.util.concurrent.FutureTask.runAndReset(FutureTask.java:308)
	at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.access$301(ScheduledThreadPoolExecutor.java:180)
	at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.run(ScheduledThreadPoolExecutor.java:294)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624)
	at java.lang.Thread.run(Thread.java:748)
2022-12-07 14:31:17.697 [33mINFO [0;39m -- [ttp-nio-45560-exec-5] [32mtra.cmdb.dao.cmdb.EsDaoEs7Impl[0;39m [34mtPageNodeByQueryJson: 237[0;39m: get page node by query json es query json index:wzx_016_cmdb_trans_index, cost:357912, queryStr:{"track_total_hits":true,"query":{"bool":{"must":[{"terms":{"resTypeId.keyword":["USER","MOD_IPV4","MOD_ADDRESS_SEGMENT_DICTIONARY","MOD_HWC_MO6_NETPORT","MOD_HWC_MO6_ELCARD","MOD_VMWARE_VM","MOD_ROUTER","MOD_5GC_CLOUDONE","MOD_HWC_MO6_ELVOL","MOD_HWC_MO6_OPTPORT","MOD_HOST_PC","MOD_HWC_MO6_MEM","MOD_FC_VIRTUAL_DISK","MOD_NET_INTERFACE","MOD_HWC_MO6_LUN","MOD_LISTENPORT","MOD_KFK_LAG","MOD_DEV_MODEL","MOD_TENCENTCLOUD_CVM","MOD_HWC_MO6_ELSVR","MOD_HWC_MO6_FAN","MOD_HWC_MO6_DISK","MOD_TENCENTCLOUD_SECURITYGROUP","MOD_COTS_SOFTWARE","MOD_FC_VSP","MOD_FC_VIRTUAL_HOST","MOD_MIS_CLOUDHOST","MOD_H3CiMC_SWITCHIF","IPResPoolNum","MOD_CABINET","MOD_RES_SWITCH","MOD_FLINK_TASKMNG","MOD_BUSI_SYS","MOD_HWC_MO6_CPU","MOD_UNIX_LINUX","MOD_VIMSCLOUD_ZHONGXINGNUOJIYA","MOD_TEMPE_SERSOR","MOD_APP_SERV","MOD_APP_CLUS","MOD_HWC_MO6_DEVBOARD","MOD_FLINK_JOB_VERT","MOD_HWC_MO6_POWER","MOD_HWC_MO6_LINK","MOD_NET_SLOT","MOD_SWITCH","MOD_HOST_PORT","MOD_HWC_MO6_FCZONE","MOD_BUS_ADDRESS","MOD_RACK_SERV","MOD_CLOUDTWO_ZHONGXINGNUOJIYA","MOD_DES_DATA","MOD_HWC_MO6_VMSPECIFIC","MOD_HWC_MO6_NETCARD","MOD_MEC_VM","MOD_TENCENTCLOUD_CLB","MOD_HWC_MO6_VM","MOD_HOST_MIN","MOD_FILE_SYS","MOD_HWC_MO6_FCPORT","MOD_HWC_MO6_PHYHOST","MOD_MYSQL_DB","MOD_ORG_DATA","MOD_ORACLE_TABLE_SPACE","MOD_BUSI_ALERT","MOD_K8S_POD","MOD_CARD","MOD_TENCENTCLOUD","MOD_HWC_MO6_SVR","MOD_HWC_MO6_BOARD","MOD_H3CiMC_SAFEIF","MOD_HWC_MO6_VMIMAGE","MOD_HWC_MO6_VMNETCARD","MOD_CPU_NM","MOD_DISK_ARRAY","MOD_VLAN_INFO","MOD_BLADE_BOX","MOD_TENCENTCLOUD_MYSQL","MOD_FLINK_JOB_VERT_SUB","MOD_PROCESS","MOD_DIM_VENDORS","MOD_IPV6","MOD_HWC_MO6_PORT","MOD_LOGICAL_HOST","MOD_CATEGORY","MOD_NET_OPTICAL","MOD_IP_POOL","MOD_REDIS_NODE","MOD_LINK","MOD_ACC_PRN_DEVICE","MOD_FC_PORTGROUP","MOD_TENCENTCLOUD_CKAFKA_TOPIC","MOD_VMWARE_VDISK","MOD_TENCENTCLOUD_CLB_LIS","MOD_K8S_SERVICE","MOD_IPV4_ADDRESS","MOD_TENCENTCLOUD_REDIS","MOD_SAFETY_DEVICES","MOD_FLINK_JOB","MOD_VMWARE_VIRNETCARD"]}}  ]  } },"from":0,"size":100000 ,"sort": {}}2022-12-07 14:31:17 [ERROR](c.n.p.p.s.AgentConfigExecutor      ) UNAVAILABLE: Channel shutdown invoked
io.grpc.StatusRuntimeException: UNAVAILABLE: Channel shutdown invoked
	at io.grpc.stub.ClientCalls.toStatusRuntimeException(ClientCalls.java:222)
	at io.grpc.stub.ClientCalls.getUnchecked(ClientCalls.java:203)
	at io.grpc.stub.ClientCalls.blockingUnaryCall(ClientCalls.java:132)
	at com.navercorp.pinpoint.grpc.trace.AgentGrpc$AgentBlockingStub.requestConfig(AgentGrpc.java:272)
	at com.navercorp.pinpoint.profiler.sender.AgentConfigExecutor.execute(AgentConfigExecutor.java:104)
	at com.navercorp.pinpoint.profiler.sender.AgentConfigExecutor$RequestConfigThread.run(AgentConfigExecutor.java:92)
	at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
	at java.util.concurrent.FutureTask.runAndReset(FutureTask.java:308)
	at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.access$301(ScheduledThreadPoolExecutor.java:180)
	at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.run(ScheduledThreadPoolExecutor.java:294)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624)
	at java.lang.Thread.run(Thread.java:748)
2022-12-07 14:31:17.698 [33mINFO [0;39m -- [ttp-nio-45560-exec-5] [32mce.ResFullTextQueryServiceImpl[0;39m [34m       getResCascade: 380[0;39m: esSvs.getResListByParam cost : 357914 ms
2022-12-07 14:31:17.699 [33mINFO [0;39m -- [ttp-nio-45560-exec-5] [32mnV01ResFullTextQueryController[0;39m [34m       getResCascade: 114[0;39m: 根据条件获取资源===query/allRes结果为: end getResCascade total rows:0, cost:357916

```

