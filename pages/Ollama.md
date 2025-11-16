- SpringAI引入依赖
	- ```xml
	  <dependency>
	      <groupId>org.springframework.ai</groupId>
	      <artifactId>spring-ai-ollama-spring-boot-starter</artifactId>
	      <version>1.0.0-M6</version>
	  </dependency>
	  ```
- 修改配置
	- ```yml
	  spring:
	    ai:
	      ollama:
	        base-url: http://localhost:11434
	        chat:
	          model: gemma3:1b
	  ```
- 修改注入的`chatModel名`
	- ```java
	  // 取消注释即可在 SpringBoot 项目启动时执行
	  //@Component
	  public class OllamaAiInvoke implements CommandLineRunner {
	  
	      @Resource
	      private ChatModel ollamaChatModel;
	  
	      @Override
	      public void run(String... args) throws Exception {
	          AssistantMessage output = ollamaChatModel.call(new Prompt("你好，我是鱼皮"))
	                  .getResult()
	                  .getOutput();
	          System.out.println(output.getText());
	      }
	  }
	  ```