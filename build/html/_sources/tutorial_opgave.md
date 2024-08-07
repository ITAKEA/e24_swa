# Tutorial opgave
De næste 2 uger skal i arbejde med en del tutorials. De er alle som udgangspunkt forbundet til denne hoved tutorial 
 [Build an LLM RAG Chatbot With LangChain](https://realpython.com/build-llm-rag-chatbot-with-langchain/#demo-an-llm-rag-chatbot-with-langchain-and-neo4j). I selve undervisningspeiroderne kommer jeg til at gennemgå de forskellige værktøjer i bruger i disse tutorials. Dette er eksempelvis    

**Inkluderede "sub"-Tutorial**
* [Embeddings and Vector Databases With ChromaDB](https://realpython.com/chromadb-vector-database/)
* [Prompt Engineering: A Practical Example](https://realpython.com/practical-prompt-engineering/)
* [LLM RAG Evaluation with MLflow Example Notebook](https://mlflow.org/docs/latest/llms/rag/notebooks/mlflow-e2e-evaluation.html)
* [Docker Compose will BLOW your MIND!! (a tutorial)](https://www.youtube.com/watch?v=DM65_JyGxCo)
* [LangChain Quickstart Guide](https://python.langchain.com/v0.1/docs/get_started/quickstart/)
* [Video: LangChain v0.1.0 Launch](https://www.youtube.com/playlist?list=PLfaIDFEXuae0gBSJ9T0w7cu7iJZbH3T31)

* Neo4J og graph databaser
* CouchDB og vector databaser
* Sqlite og relationelle databaser
* Lanchain
* RAG
* Text embeddings

## Læringsmål

Følgende skal i både kunne forklare og vise hvordan i gør brug af:
 
* Hvad er LangChain og hvordan bruges det?
* Hvad er Neo4j og hvordan bruges det?
* Hvad er fodelene ved en 'Graph Database'
* Hvad er en Vectordatabase?
* Hvad er tekst embeddings?
* Læse og forstå documentation (langchain, neo4j, )
* Forklar hvad en 'chain' er i langchan context.
* Forstå hvad RAG står for og kunne forklare hvordan det bruges.
* Forstå sammenhængen mellem LLM og VectorDB´s
* Forstå:chat models, prompts, chains, and retrieval, agents.
* Forstå asyncron netværkskommunikation
* Forstå hvad docker og docker-compose


## Opgave beskrivelse

Denne uge skal i bruge på følgende opgave.  Den er udformet som en Tutorial, og selve koden (det i skal lave) kan i finde på Github. I kan teoretisk set være færdige med denne opgave i løbet af en lille time, hvis i bruger den færdigekode, kopy/paster lidt hist og her osv.     

Det er dog ikke meningen med opgaven.     

**Meningen er at i skal forstå alle elementer i opgaven på en måde så i vil kunne fortælle hvad der præcist sker i hvert step.**     

Hvordan i kommer dertil er op til jer, og i må få alt den hjælp i behøver fra mig eller LLM´er etc.     

Tip: I skal bruge 20 timer på denne opgave, hvis i bruger mindre har i brugt for lidt tid på den!


* [Build an LLM RAG Chatbot With LangChain](https://realpython.com/build-llm-rag-chatbot-with-langchain/#demo-an-llm-rag-chatbot-with-langchain-and-neo4j)

Under "Step 5: Deploy the LangChain Agent" skal i **ikke** følge artiklen, men istedet følge det som jeg har skrevet herunder. I artiklen bruger forfatteren "FastApi" og "Streamlit UI". Jeg har herunder omskrevet artikel til at bruge Flask og Jupyter Notebook. Det passer bedre til det vi har arbejdet med i dette semester.

## Step 5: Deploy the LangChain Agent

At long last, you have a functioning LangChain agent that serves as your hospital system chatbot. The last thing you need to do is get your chatbot in front of stakeholders. For this, you’ll deploy your chatbot as a Flask API endpoint and create a Jupyter Notebook to interact with the endpoint.

Before you get started, create two new folders called `chatbot_frontend/` and `tests/` in your project’s root directory. You’ll also need to add some additional files and folders to `chatbot_api/`:

```
./
│
├── chatbot_api/
│   │
│   ├── src/
│   │   │
│   │   ├── agents/
│   │   │   └── hospital_rag_agent.py
│   │   │
│   │   ├── chains/
│   │   │   ├── hospital_cypher_chain.py
│   │   │   └── hospital_review_chain.py
│   │   │
│   │   ├── models/
│   │   │   └── hospital_rag_query.py
│   │   │
│   │   ├── tools/
│   │   │   └── wait_times.py
│   │   │
│   │   ├── utils/
│   │   │   └── async_utils.py
│   │   │
│   │   ├── entrypoint.sh
│   │   └── main.py
│   │
│   ├── Dockerfile
│   └── pyproject.toml
│
├── chatbot_frontend/
│   │
│   ├── src/
│   │   ├── entrypoint.sh
│   │   └── notebook.ipynb
│   │
│   ├── Dockerfile
│   └── pyproject.toml
│
├── hospital_neo4j_etl/
│   │
│   ├── src/
│   │   ├── entrypoint.sh
│   │   └── hospital_bulk_csv_write.py
│   │
│   ├── Dockerfile
│   └── pyproject.toml
│
├── tests/
│   ├── async_agent_requests.py
│   └── sync_agent_requests.py
│
├── .env
└── docker-compose.yml
```

You need the new files in `chatbot_api` to build your Flask app, and `tests/` has two scripts to demonstrate the power of making asynchronous requests to your agent. Lastly, `chatbot_frontend/` has the code for the Jupyter Notebook that’ll interface with your chatbot. You’ll start by creating a Flask application to serve your agent.

### Serve the Agent With Flask

You’ll serve your agent through a POST request, so the first step is to define what data you expect to get in the request body and what data the request returns. Flask uses marshmallow library for object serialization and deserialization:

#### chatbot_api/src/models/hospital_rag_query.py

```python
from marshmallow import Schema, fields

class HospitalQueryInput(Schema):
    text = fields.Str(required=True)

class HospitalQueryOutput(Schema):
    input = fields.Str()
    output = fields.Str()
    intermediate_steps = fields.List(fields.Str())
```

In this script, you define marshmallow schemas `HospitalQueryInput` and `HospitalQueryOutput`. `HospitalQueryInput` is used to verify that the POST request body includes a `text` field, representing the query your chatbot responds to. `HospitalQueryOutput` verifies the response body sent back to your user includes `input`, `output`, and `intermediate_step` fields.

Next, the driving logic for your chatbot API is in `chatbot_api/src/main.py`:

#### chatbot_api/src/main.py

```python
from flask import Flask, request, jsonify
from agents.hospital_rag_agent import hospital_rag_agent_executor
from models.hospital_rag_query import HospitalQueryInput, HospitalQueryOutput
from utils.async_utils import async_retry
import asyncio

app = Flask(__name__)

@app.route("/", methods=["GET"])
def get_status():
    return jsonify({"status": "running"})

@async_retry(max_retries=10, delay=1)
async def invoke_agent_with_retry(query: str):
    """Retry the agent if a tool fails to run.

    This can help when there are intermittent connection issues
    to external APIs.
    """
    return await hospital_rag_agent_executor.ainvoke({"input": query})

@app.route("/hospital-rag-agent", methods=["POST"])
async def query_hospital_agent():
    request_data = request.get_json()
    input_data = HospitalQueryInput().load(request_data)
    query_response = await invoke_agent_with_retry(input_data['text'])

    output_data = {
        "input": input_data['text'],
        "output": query_response["output"],
        "intermediate_steps": [str(s) for s in query_response["intermediate_steps"]]
    }

    return jsonify(HospitalQueryOutput().dump(output_data))
```

You import Flask, your agent executor, the marshmallow schemas you created for the POST request, and `@async_retry`. Then you instantiate a Flask object and define `invoke_agent_with_retry()`, a function that runs your agent asynchronously. The `@async_retry` decorator above `invoke_agent_with_retry()` ensures the function will be retried ten times with a delay of one second before failing.

Lastly, you define `query_hospital_agent()`, which serves POST requests to your agent at `/hospital-rag-agent`. This function extracts the `text` field from the request body, passes it to the agent, and returns the agent’s response to the user.

You’ll serve this API with Docker and you’ll want to define the following entrypoint file to run inside the container:

#### chatbot_api/src/entrypoint.sh

```bash
#!/bin/bash

# Run any setup steps or pre-processing tasks here
echo "Starting hospital RAG Flask service..."

# Start the main application
python main.py
```

The main driver file for Flask app looks like this:

#### chatbot_api/src/main.py

```python
# chatbot_api/src/main.py

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=8000)
```

The driving Dockerfile for your Flask app looks like this:

#### chatbot_api/Dockerfile

```Dockerfile
# chatbot_api/Dockerfile

FROM python:3.11-slim

WORKDIR /app
COPY ./src/ /app

COPY ./pyproject.toml /code/pyproject.toml
RUN pip install /code/.

EXPOSE 8000
CMD ["sh", "entrypoint.sh"]
```

This Dockerfile tells your container to use the `python:3.11-slim` distribution, copy the contents from `chatbot_api/src/` into the `/app` directory within the container, install the dependencies from `pyproject.toml`, and run `entrypoint.sh`.

The last thing you’ll need to do is update the `docker-compose.yml` file to include your Flask container:

#### docker-compose.yml

```yaml
version: '3'

services:
  hospital_neo4j_etl:
    build:
      context: ./hospital_neo4j_etl
    env_file:
      - .env

  chatbot_api:
    build:
      context: ./chatbot_api
    env_file:
      - .env
    depends_on:
      - hospital_neo4j_etl
    ports:
      - "8000:8000"
```

To run the API, along with the ETL you built earlier, open a terminal and run:

```bash
$ docker-compose up --build
```

If everything runs successfully, you’ll see a screen similar to the following at `http://localhost:8000`:

---

## Create a Interaction Interface with Jupyter Notebook

Instead of using Streamlit, you'll use a Jupyter Notebook to create a simple front-end to interface with the chatbot API. Here's the code for your Jupyter Notebook (`chatbot_frontend/src/notebook.ipynb`):

### chatbot_frontend/src/notebook.ipynb

```python
#!/usr/bin/env python
# coding: utf-8

# In[1]:


import requests

# Set the URL for your chatbot API
CHATBOT_URL = "http://localhost:8000/hospital-rag-agent"

def ask_question(question):
    data = {"text": question}
    response = requests.post(CHATBOT_URL, json=data)
    
    if response.status_code == 200:
        result = response.json()
        return result['output'], result['intermediate_steps']
    else:
        return "An error occurred while processing your message.", []

# Function to display chat interaction
def chat():
    import IPython.display as display
    from ipywidgets import widgets
    
    input_box = widgets.Text(placeholder='Ask your question here...')
    output_area = widgets.Output()
    
    def on_submit(sender):
        with output_area:
            print(f"User: {input_box.value}")
            output, steps = ask_question(input_box.value)
            print(f"Bot: {output}")
            print(f"Intermediate Steps: {'; '.join(steps)}")
            print("-"*50)
        input_box.value = ''
    
    input_box.on_submit(on_submit)
    display.display(input_box, output_area)

# Start the chat
chat()
```

Create an entrypoint file to run Jupyter Notebook:

### chatbot_frontend/src/entrypoint.sh

```bash
#!/bin/bash

# Run any setup steps or pre-processing tasks here
echo "Starting hospital chatbot frontend..."

# Run the Jupyter Notebook
jupyter notebook --ip=0.0.0.0 --port=8888 --no-browser --allow-root
```

And finally, the Docker file to create an image for the frontend:

### chatbot_frontend/Dockerfile

```Dockerfile
FROM python:3.11-slim

WORKDIR /app

COPY ./src/ /app

COPY ./pyproject.toml /code/pyproject.toml
RUN pip install /code/.
RUN pip install jupyter

CMD ["sh", "entrypoint.sh"]
```

Update the `docker-compose.yml` file to include your `chatbot_frontend` service:

#### docker-compose.yml

```yaml
version: '3'

services:
  hospital_neo4j_etl:
    build:
      context: ./hospital_neo4j_etl
    env_file:
      - .env

  chatbot_api:
    build:
      context: ./chatbot_api
    env_file:
      - .env
    depends_on:
      - hospital_neo4j_etl
    ports:
      - "8000:8000"

  chatbot_frontend:
    build:
      context: ./chatbot_frontend
    env_file:
      - .env
    depends_on:
      - chatbot_api
    ports:
      - "8888:8888"
```

Finally, open a terminal and run:

```bash
$ docker-compose up --build
```

Once everything builds and runs, you can access the Jupyter Notebook interface at `http://localhost:8888/` to begin chatting with your chatbot:

You've now built a fully functioning hospital system chatbot end-to-end with Flask and Jupyter Notebook. Take some time to ask it questions, see the kinds of questions it’s good at answering, find out where it fails, and think about how you might improve it with better prompting or data. You can start by making sure the example questions are correctly answered.



## Conclusion
Congratulations on completing this in-depth tutorial!

You’ve successfully designed, built, and served a RAG LangChain chatbot that answers questions about a fake hospital system. There are certainly many ways you can improve the chatbot you built in this tutorial, but you now have a sound understanding of how to integrate LangChain with your own data, giving you the creative freedom to build all kinds of custom chatbots.

In this tutorial, you’ve learned how to:

* Use LangChain to build personalized chatbots.
* Create a chatbot for a fake hospital system by aligning with business requirements and leveraging available data.
* Consider the implementation of graph databases in your chatbot design.
* Set up a Neo4j AuraDB instance for your project.
* Develop a RAG chatbot capable of fetching both structured and unstructured data from Neo4j.
* Deploy your chatbot using Flask API and Jupyter Notebook.

You can find the complete source code and data for this project, in the supporting materials, which you can download using the link below:

---


* til denne tutorial er der en del relaterede artikler, som det vil være godt (i det mindste) at skimme igennem.
    * [Prompt Engineering: A Practical Example](https://realpython.com/practical-prompt-engineering/)
    * [Embeddings and Vector Databases With ChromaDB](https://realpython.com/chromadb-vector-database/)
