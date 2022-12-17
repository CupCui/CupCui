#### 问题: ES查询时报错内容过大: java.io.IOException: entity content is too long [107162543] for the configured buffer limit [104857600]

**[ElasticSearch]** **[ERROR]**

问题: ES查询时报错 entity content is too long for the configured buffer limit

原因: 单次查询内容大小太大

解决: 设置ES查询内容限制HeapBufferedResponseConsumerFactory.

Java代码参考:

```java
private static final RequestOptions COMMON_OPTIONS;

	static {
		RequestOptions.Builder builder = RequestOptions.DEFAULT.toBuilder();
		builder.setHttpAsyncResponseConsumerFactory(
      // 设置查询内容大小限制,默认100 * 1024 * 1024
				new HttpAsyncResponseConsumerFactory.HeapBufferedResponseConsumerFactory(300 * 1024 * 1024)
		);
		COMMON_OPTIONS = builder.build();
	}


	private QueryResp doQuery(String index, String json) throws IOException {
		String endPoint = "/" + index + "/_search";
		Request req = new Request("POST", endPoint);
		req.setOptions(COMMON_OPTIONS);

		if (!isUseKeyword) {
			json = json.replaceAll(".keyword", "");
		}

		LOG.debug("query json:{}",json);
		req.setEntity(new NStringEntity(json,ContentType.APPLICATION_JSON));
		Response response = ES7Util.getLowLevelClient().performRequest(req);
		String respStr = EntityUtils.toString(response.getEntity());
		LOG.debug("respStr:{}",respStr);
		QueryResp queryResp = JSON.parseObject(respStr,QueryResp.class);
		return queryResp;
	}
```



参考:

[https://stackoverflow.com/questions/51020646/org-apache-http-contenttoolongexception-entity-content-is-too-long-105539255](https://stackoverflow.com/questions/51020646/org-apache-http-contenttoolongexception-entity-content-is-too-long-105539255)

[https://www.elastic.co/guide/en/elasticsearch/client/java-api-client/current/java-rest-low-usage-requests.html](https://www.elastic.co/guide/en/elasticsearch/client/java-api-client/current/java-rest-low-usage-requests.html)

