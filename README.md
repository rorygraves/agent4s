# LLM4S

Goal: To provide a simple, robust and scalable framework for building LLM applications in Scala.

N.b. This is most definitely a work in progress project and is likely to change significantly over time.

Whilst most LLM work is done in Python we believe that Scala can offer a fundamentally better foundation for 
building reliable, maintainable AI-powered applications.

The goal of this project is large but unobtainable - take the lessons learned from the Python LLM ecosystem and build
even better tooling platform.

This we want to implement (and the equivalent python frameworks):

* Single API access multiple LLM providers (LiteLLM)
* A great tool chain for building LLM apps (LangChain/LangGraph)
* An agentic framework (PydanticAI, CrewAI etc)




# Random Todos


 - [ ] Add a tiktoken port 
 - [ ] Generalize calling API to be able to call anthropic as well.
 - [ ] Implement full agentic loop code
 - [ ] Implement a simple tool calling mechanism


## React loop

## Tool calling handling
Tool calling is a critical integration - make it as simple as possible
### Tool sig generation

e.g. ScalaMeta based tool definition generator

Take a method e.g. 

```scala

/** My tool does some funky things with a & b...
 * @param a: The first thing
 * @param b: The second thing
 */
 def my_tool(a: Int, b: String): ToolResponse = {
 ...
 }
```
Use ScalaMeta to extract the method params / types, doc comment etc and generate an openai tool definition from it.
see: https://github.com/scalameta/scalameta/pull/692
https://github.com/scalameta/scalameta/issues/556

### Tool call mapping
  From the tool call request - map the parameters and invoke the method.

This could be code generation - or reflective?
 Or code generation from the scalameta parse to mean that a lLM request to call a tool 
 can be mapped to the given tool calling arguments.
  
### Docker container based execution

A lot of tools need to be run in a protected environment (e.g. a docker container to prevent
accidental leakage/accidents when for example the LLM tries to do an 'rm -rf /' or similar (even by accident))

