- collapsed:: true
	- ```java
	      public static void main(String[] args) {
	          // 从环境变量读取 API Key，若需要直接写死也可以改成字符串常量
	          String apiKey = TestApiKey.API_KEY;
	  
	          // 构建请求体 JSON
	          Map<String, Object> body = new HashMap<>();
	          body.put("model", "qwen-plus");
	  
	          Map<String, Object> input = new HashMap<>();
	          List<Map<String, String>> messages = new ArrayList<>();
	          Map<String, String> systemMsg = new HashMap<>();
	          systemMsg.put("role", "system");
	          systemMsg.put("content", "You are a helpful assistant.");
	          Map<String, String> userMsg = new HashMap<>();
	          userMsg.put("role", "user");
	          userMsg.put("content", "请告诉我http有哪些状态码？");
	          messages.add(systemMsg);
	          messages.add(userMsg);
	          input.put("messages", messages);
	          body.put("input", input);
	  
	          Map<String, Object> parameters = new HashMap<>();
	          parameters.put("result_format", "message");
	          body.put("parameters", parameters);
	  
	          String json = JSONUtil.toJsonStr(body);
	  
	          String url = "https://dashscope.aliyuncs.com/api/v1/services/aigc/text-generation/generation";
	  
	          HttpResponse resp = HttpRequest.post(url)
	                  .header("Authorization", "Bearer " + apiKey)
	                  .contentType("application/json")
	                  .body(json)
	                  .execute();
	  
	          int status = resp.getStatus();
	          String respBody = resp.body();
	  
	          System.out.println("Status: " + status);
	          System.out.println("Response: " + respBody);
	      }
	  ```