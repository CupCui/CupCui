---
layout: post
title: 问题 ES 查询时报错 I/O 异常 java.lang.IllegalStateException Request cannot be executed; I/O reactor status STOPPED
categories: ERROR ElasticSearch
description: 问题 ES 查询时报错 I/O 异常 java.lang.IllegalStateException Request cannot be executed; I/O reactor status STOPPED
keywords: ERROR, ElasticSearch, I/O reactor status STOPPED
---

#### 问题: ES 查询时报错 I/O 异常: java.lang.IllegalStateException: Request cannot be executed; I/O reactor status: STOPPED

**[ES]** **[I/O STOPPED]** **[OOM]**

问题: ES 查询时报错 IO 异常, java.lang.IllegalStateException: Request cannot be executed; I/O reactor status: STOPPED

原因: 使用ES过程中遇到一个Request cannot be executed; I/O reactor status: STOPPED 的异常，大概意思是和server端的连接异常终止了。开始以为是引用的版本不对，或者自己使用问题，后来发现就是因为OOM导致程序宕机，进而引发连接终止.

解决: 排查并解决关联的OOM问题

参考: [https://www.cnblogs.com/Naylor/p/15763941.html](https://www.cnblogs.com/Naylor/p/15763941.html)

```json
// ES查询报错 I/O reactor status: STOPPED
2022-12-07 14:35:58.813 ERROR -- [tp-nio-45560-exec-34] ra.cmdb.common.util.es.ES7Util   searchTotalAndData: 515: 查询数据失败：java.lang.RuntimeException: Request cannot be executed; I/O reactor status: STOPPED
        at org.elasticsearch.client.RestClient.extractAndWrapCause(RestClient.java:940)
        at org.elasticsearch.client.RestClient.performRequest(RestClient.java:300)
        at org.elasticsearch.client.RestClient.performRequest(RestClient.java:288)
        at com.ultra.cmdb.common.util.es.ES7Util.doQuery(ES7Util.java:252)
        at com.ultra.cmdb.common.util.es.ES7Util.searchTotalAndData(ES7Util.java:494)
        at com.ultra.cmdb.dao.cmdb.EsDaoEs7Impl.getPageNodeByQueryJson(EsDaoEs7Impl.java:235)
        at com.ultra.cmdb.service.es.impl.ESServiceImpl.getPageNodeByQueryJson(ESServiceImpl.java:1516)
        at com.ultra.cmdb.service.es.impl.ESServiceImpl.queryResByUserIdV2(ESServiceImpl.java:831)
        at com.ultra.cmdb.service.es.impl.ESServiceImpl.getResListByParam(ESServiceImpl.java:1179)
        at com.ultra.cmdb.service.resource.ResFullTextQueryServiceImpl.getFullTextQueryResultPageForOpenCtl(ResFullTextQueryServiceImpl.java:173)
        at com.ultra.cmdb.service.resource.ResFullTextQueryServiceImpl$$FastClassBySpringCGLIB$$35469f9.invoke(<generated>)
        at org.springframework.cglib.proxy.MethodProxy.invoke(MethodProxy.java:218)
        at org.springframework.aop.framework.CglibAopProxy$CglibMethodInvocation.invokeJoinpoint(CglibAopProxy.java:793)
        at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:163)
        at org.springframework.aop.framework.CglibAopProxy$CglibMethodInvocation.proceed(CglibAopProxy.java:763)
        at org.springframework.aop.interceptor.ExposeInvocationInterceptor.invoke(ExposeInvocationInterceptor.java:97)
        at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:186)
        at org.springframework.aop.framework.CglibAopProxy$CglibMethodInvocation.proceed(CglibAopProxy.java:763)
        at org.springframework.aop.framework.CglibAopProxy$DynamicAdvisedInterceptor.intercept(CglibAopProxy.java:708)
        at com.ultra.cmdb.service.resource.ResFullTextQueryServiceImpl$$EnhancerBySpringCGLIB$$2a2361be.getFullTextQueryResultPageForOpenCtl(<generated>)
        at com.ultra.cmdb.web.controller.open.v01.OpenV01ResFullTextQueryController.fullTextQueryByResType(OpenV01ResFullTextQueryController.java:51)
        at sun.reflect.GeneratedMethodAccessor745.invoke(Unknown Source)
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
Caused by: java.lang.IllegalStateException: Request cannot be executed; I/O reactor status: STOPPED
        at org.apache.http.util.Asserts.check(Asserts.java:46)
        at org.apache.http.impl.nio.client.CloseableHttpAsyncClientBase.ensureRunning(CloseableHttpAsyncClientBase.java:90)
        at org.apache.http.impl.nio.client.InternalHttpAsyncClient.execute(InternalHttpAsyncClient.java:123)
        at org.elasticsearch.client.RestClient.performRequest(RestClient.java:296)
        ... 74 common frames omitted

```

