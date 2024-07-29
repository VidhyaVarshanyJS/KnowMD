# KnowMD 
![knowmd logo](https://github.com/user-attachments/assets/b7d4c15a-af17-42ea-86e4-99bedabb3eaf)

## Abstract
Recent advancements in biomedical language models have significantly improved the processing and understanding of medical texts. However, existing models struggle with efficiently retrieving and synthesizing information from large, unstructured datasets. This project integrates Microsoft’s GraphRAG with local large language models (LLMs) to enhance retrieval-augmented generation (RAG) capabilities. By leveraging GraphRAG’s structured knowledge graphs and local LLMs’ inference capabilities, we aim to revolutionize biomedical natural language processing.

## Introduction
Physicians face the challenge of staying current with rapidly expanding medical literature. The KnowMD project aims to assist medical professionals in making accurate and comprehensive diagnoses by developing a GraphRAG-based system. This tool will provide contextual information and insights to supplement physicians' expertise, utilizing open-source LLM models for high-performance, evidence-based responses.

## Key Highlights
- **Agentic-RAG:** Integrating GraphRAG's knowledge search method with an AutoGen agent via function calling.
- **Offline LLM Support:** Configuring GraphRAG (local & global search) to support local models from Ollama for inference and embedding.
- **Non-OpenAI Function Calling:** Extending AutoGen to support function calling with non-OpenAI LLMs from Ollama via Lite-LLM proxy server.
- **Interactive UI:** Deploying Chainlit UI to handle continuous conversations, multi-threading, and user input settings.

## Objectives
1. **Construct a Comprehensive Medical Knowledge Graph:**
   - Integrate Microsoft’s GraphRAG with local LLMs to enhance RAG capabilities.
2. **Develop a GraphRAG-Based Retrieval and Generation System:**
   - Efficiently query the knowledge graph and generate detailed, evidence-based responses for diagnosis and treatment support.
3. **Evaluate System Performance:**
   - Assess the system's ability to enhance medical decision-making against traditional search and summarization approaches.
4. **Deploy in a Clinical Setting:**
   - Collect feedback from physicians to continually improve the tool and ensure it meets medical community needs.

## Methodology
1. **Data Collection:**
   - Gather biomedical texts and convert them into suitable formats.
2. **GraphRAG Initialization:**
   - Set up GraphRAG to create necessary files and folders for knowledge graph construction.
3. **Model Configuration:**
   - Configure AutoGen and Ollama local LLMs for function calling and inference.
4. **UI Development:**
   - Develop a user interface using Chainlit for user interactions.
5. **Integration and Testing:**
   - Integrate all components and test the system using various biomedical queries.
6. **Performance Evaluation:**
   - Measure performance using metrics such as accuracy, response time, and user satisfaction.

## Required Tools and Techniques
- **Microsoft GraphRAG:** For constructing structured knowledge graphs from raw text.
- **AutoGen AI Agents:** For conversational and task-oriented functionalities.
- **Ollama Local LLMs:** For inference and embedding, ensuring cost-effective and secure data processing.
- **Chainlit UI:** For handling continuous conversations and user input settings.
- **Linux Environment:** For development and testing using WSL and Visual Studio Code.

## Testing Plan / Performance Metrics
- **Accuracy:** Measure the correctness of retrieved and generated information.
- **Response Time:** Evaluate the system's speed in handling queries.
- **User Satisfaction:** Assess user feedback on usability and effectiveness.
- **Robustness:** Test the system's ability to handle a variety of biomedical queries.
- **Cost Efficiency:** Analyze operational costs compared to traditional online LLMs.

## Installation and Setup

### Linux

1. **Install LLMs:**

    Visit [Ollama's website](https://ollama.com/) for installation files.

    ```bash
    ollama pull mistral
    ollama pull nomic-embed-text
    ollama pull llama3
    ollama serve
    ```

2. **Create conda environment and install packages:**

    ```bash
    conda create -n RAG_agents python=3.12
    conda activate RAG_agents
    git clone https://github.com/karthik-codex/autogen_graphRAG.git
    cd autogen_graphRAG
    pip install -r requirements.txt
    ```

3. **Initiate GraphRAG root folder:**

    ```bash
    mkdir -p ./input
    python -m graphrag.index --init  --root .
    mv ./utils/settings.yaml ./
    ```

4. **Replace 'embedding.py' and 'openai_embeddings_llm.py' in the GraphRAG package folder using files from Utils folder:**

    ```bash
    sudo find / -name openai_embeddings_llm.py
    sudo find / -name embedding.py
    ```

5. **Create embeddings and knowledge graph:**

    ```bash
    python -m graphrag.index --root .
    ```

6. **Start Lite-LLM proxy server:**

    ```bash
    litellm --model ollama_chat/llama3
    ```

7. **Run app:**

    ```bash
    chainlit run appUI.py
    ```

### Windows

1. **Install LLMs:**

    Visit [Ollama's website](https://ollama.com/) for installation files.

    ```pwsh
    ollama pull mistral
    ollama pull nomic-embed-text
    ollama pull llama3
    ollama serve
    ```

2. **Create conda environment and install packages:**

    ```pwsh
    git clone https://github.com/karthik-codex/autogen_graphRAG.git
    cd autogen_graphRAG
    python -m venv venv
    ./venv/Scripts/activate
    pip install -r requirements.txt
    ```

3. **Initiate GraphRAG root folder:**

    ```pwsh
    mkdir input
    python -m graphrag.index --init  --root .
    cp ./utils/settings.yaml ./
    ```

4. **Replace 'embedding.py' and 'openai_embeddings_llm.py' in the GraphRAG package folder using files from Utils folder:**

    ```pwsh
    cp ./utils/openai_embeddings_llm.py .\venv\Lib\site-packages\graphrag\llm\openai\openai_embeddings_llm.py
    cp ./utils/embedding.py .\venv\Lib\site-packages\graphrag\query\llm\oai\embedding.py 
    ```

5. **Create embeddings and knowledge graph:**

    ```pwsh
    python -m graphrag.index --root .
    ```

6. **Start Lite-LLM proxy server:**

    ```pwsh
    litellm --model ollama_chat/llama3
    ```

7. **Run app:**

    ```pwsh
    chainlit run appUI.py
    ```

## Final Outcome
The integration of GraphRAG with local LLMs is expected to significantly enhance the retrieval and synthesis capabilities of biomedical NLP systems. This solution aims to provide accurate, contextually grounded responses, secure data processing, and cost-effective operations, serving as a valuable tool for medical professionals in research and clinical applications.


## Useful Links 🔗
- **Full Guide:** [GraphRAG](https://github.com/microsoft/graphrag) 📚
