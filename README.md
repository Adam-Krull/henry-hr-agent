# henry-hr-agent

## Purpose
The purpose of this project is to implement a few key concepts of AI agents. The concepts explored in this project are:
- Multi-agent workflows - the project in first_pass.ipynb has 3 agents. The first agent routes the traffic to the appropriate specialist based on question content. The two specialized agents answer questions specific to their domains: health benefits and company policy.
- A persistent state - a state object is created and used to construct the agent graph. The state is updated by the agents as they contribute to the workflow.
- Context retrieval (RAG) - context required to answer the question is retrieved from one of two vector stores. Information retrieved from these vector stores is further specified by the employee's healthcare plan.
- Tool calling - the tool_calling.ipynb notebook defines tools by extending the BaseTool class. The tools are called as needed by the model object to which they are bound.

The project also utilizes structured output from LLMs to ensure the workflow doesn't crash out.

## Technologies used
- [psycopg](https://www.psycopg.org/psycopg3/docs/index.html) - initiates the connection with the PostgreSQL database running locally on my computer using Docker. Allows me to create and store tables and vector stores. Accesses these resources during agent execution.
- [LangChain](https://www.langchain.com/) - provides message templates, model objects, and the vector store object. Facilitates the creation of agents and interaction with my databases and vector stores.
- [LangGraph](https://www.langchain.com/langgraph) - enables the agentic workflow. Provides the graph object to link the agents together. Also provides the add_messages function that makes it easy to capture all messages sent and received throughout the workflow.
- [pydantic](https://docs.pydantic.dev/latest/) - provides models that allows for the strict typing and structure of LLM inputs and outputs. In the future, could be used to facilitate the flow of information to/from databases.

## Results
The first pass was a success. It was able to take in employee information, update the state, and route the traffic to the appropriate specialist. The project greatly improved my understanding of agentic workflows and how to string them together using LangGraph.

The tool calling project was also successful. A custom tool was defined as an extension of the BaseTool class and bound to a model object. The tool was called appropriately and the model was able to provide an adequate answer using the context provided by the tool.