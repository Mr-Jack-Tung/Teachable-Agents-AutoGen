# Teachable Agents (AutoGen) with Ollama mistral
- Author: Ricky Loynd - Senior Research Engineer at Microsoft (October 26, 2023)
- Practice: Mr. Jack (June 02, 2024)
- URL: https://microsoft.github.io/autogen/blog/2023/10/26/TeachableAgent

Conversational assistants based on LLMs can remember the current chat with the user, and can also demonstrate in-context learning of user teachings during the conversation. But the assistant's memories and learnings are lost once the chat is over, or when a single chat grows too long for the LLM to handle effectively. Then in subsequent chats the user is forced to repeat any necessary instructions over and over.<br>

Teachability addresses these limitations by persisting user teachings across chat boundaries in long-term memory implemented as a vector database. Instead of copying all of memory into the context window, which would eat up valuable space, individual memories (called memos) are retrieved into context as needed. This allows the user to teach frequently used facts and skills to the teachable agent just once, and have it recall them in later chats.<br>

Any instantiated agent that inherits from ConversableAgent can be made teachable by instantiating a Teachability object and calling its add_to_agent(agent) method. In order to make effective decisions about memo storage and retrieval, the Teachability object calls an instance of TextAnalyzerAgent (another AutoGen agent) to identify and reformulate text as needed for remembering facts, preferences, and skills. Note that this adds extra LLM calls involving a relatively small number of tokens, which can add a few seconds to the time a user waits for each response.<br>

![alt text](https://github.com/Mr-Jack-Tung/Teachable-Agents-AutoGen/blob/main/Screenshot%20_%20Teachable-Agents-AutoGen%20_%202024-06-02.jpg)
