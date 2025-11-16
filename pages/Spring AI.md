- Demo
	- ```java
	  @Component
	  public class SpringAiAiInvoke implements CommandLineRunner {
	  
	      @Resource
	      private ChatModel dashscopeChatModel;
	  
	      @Override
	      public void run(String... args) throws Exception {
	          AssistantMessage output = dashscopeChatModel.call(new Prompt("你好！我是程序员"))
	                  .getResult()
	                  .getOutput();
	          System.out.println(output.getText());
	      }
	  }
	  ```
- [[chatClient]]
- [[Advisors]]
- [[chatMemory]]
- [[promptTemplate模版]]
-