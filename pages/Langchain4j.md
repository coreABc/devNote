- Demo
	- ```java
	      public static void main(String[] args) {
	          QwenChatModel chatModel = QwenChatModel.builder()
	                  .apiKey(TestApiKey.API_KEY)
	                  .modelName("qwen-plus")
	                  .build();
	  
	          String res = chatModel.chat("你好，请告诉我为什么1+1=2");
	          System.out.println(res);
	  
	      }
	  ```