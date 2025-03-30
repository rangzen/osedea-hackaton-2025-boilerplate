# Osedea Hackathon 2025 Boilerplate

A simple but comprehensive boilerplate for building AI-powered applications using LangGraph, n8n, and modern development tools.

## Table of Contents
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Setup](#setup)
- [Usage](#usage)
  - [JupyterLab](#jupyterlab)
  - [LangGraph Studio](#langgraph-studio)
  - [n8n](#n8n)
  - [ngrok](#ngrok)
- [Troubleshooting](#troubleshooting)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [Sources](#sources)

## Features

- **Development Environment**:
  - Python 3.11 devcontainer with pre-configured tools
  - JupyterLab for interactive development
  - LangGraph for building AI workflows
  - Docker Compose for service orchestration

- **Services**:
  - n8n for workflow automation
  - PostgreSQL for data persistence
  - HTTPS support via ngrok
  - Integration with OpenAI and Tavily APIs

## Prerequisites

Before you begin, ensure you have the following installed:

- [Docker](https://docs.docker.com/get-docker/)
- [ngrok](https://ngrok.com/download)
- [VSCode](https://code.visualstudio.com/) with the [Remote Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## Setup

1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd osedea-hackaton-2025-boilerplate
   ```

2. **Configure Environment Variables**:
   ```bash
   cp .env.example .env
   ```
   Edit `.env` with your configuration values.

3. **Required API Keys and Accounts**:
   - [OpenAI API Key](https://platform.openai.com/api-keys) for LLM functionality
   - [Tavily API Key](https://app.tavily.com/home) for web search capabilities
   - [n8n Account](https://n8n.io/) for workflow automation
   - [ngrok Account](https://ngrok.com) for HTTPS access

4. **Configure ngrok**:
   - Create a new domain at [ngrok dashboard](https://dashboard.ngrok.com/domains)
   - Update `DOMAIN_NAME` and `SUBDOMAIN` in your `.env` file

## Usage

### JupyterLab

1. Start the devcontainer in VSCode (should be asked while opening the folder with the devcontainer extension)
2. Open a terminal (in VSCode) and run:
   ```bash
   jupyter notebook
   ```
3. Check the URL of the JupyterLab instance in the terminal output (should be something like `http://localhost:8888/?token=<token>`)

### LangGraph Studio

1. Navigate to the studio directory:
   ```bash
   cd studio
   ```

2. Configure studio environment:
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

3. Start the LangGraph development server:
   ```bash
   langgraph dev
   ```

4. Access the following endpoints:
   - [Studio Interface](https://smith.langchain.com/studio/?baseUrl=http://127.0.0.1:2024)
   - [API Documentation](http://127.0.0.1:2024/docs)
   - [API Base URL](http://127.0.0.1:2024)

5. Test the system:
   - Open the Studio interface
   - Locate the `test_tavili_wikipedia` graph
   - Enter a question in the Input section. Example: "What is the ancient name of Baghdad?"
   - Click on the `Submit` button

### n8n

1. Start the services:
   ```bash
   docker compose up -d
   ```

2. Access n8n:
   - Open [http://localhost:5678](http://localhost:5678)
   - Create an admin account (you can keep the same credentials for the local instance to receive the activation key)
   - Configure and test workflows

### ngrok

HTTPS is mandatory for calling other services: Google, Discord, etc. and to receive webhooks. ngrok will provide a secure URL to access the local instance.

1. Start ngrok with your domain:
   ```bash
   ngrok http --url=your-domain.ngrok-free.app 5678
   ```

2. Use the HTTPS URL to access n8n securely.

## Troubleshooting

### Common Issues

1. **Devcontainer Issues**:
   - Ensure Docker is running
   - Try rebuilding the container: `F1 > Dev Containers: Rebuild Container`
   - Check VSCode logs for detailed error messages

2. **API Connection Issues**:
   - Verify API keys in `.env` files
   - Check network connectivity
   - Ensure services are running

3. **n8n Problems**:
   - Check Docker logs: `docker compose logs n8n`
   - Verify PostgreSQL connection
   - Ensure proper ngrok configuration

### Getting Help

- Check the [LangChain documentation](https://python.langchain.com/docs/get_started/introduction)
- Review [n8n documentation](https://docs.n8n.io/)
- Open an issue in the repository
- Use the Slack channel #hackathon-2025 or ping any member of the team: Carl, Robin or Cedric.

## Project Structure

```
.
├── .devcontainer/          # Dev container configuration
├── studio/                 # LangGraph Studio application
├── docker-compose.yaml     # Docker services configuration
├── requirements.txt        # Python dependencies
└── .env.example            # Environment variables template
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## Sources

- [LangChain Academy](https://academy.langchain.com/)
- [LangChain Academy Repository](https://github.com/langchain-ai/langchain-academy)
- [n8n Docker Compose Guide](https://docs.n8n.io/hosting/installation/server-setups/docker-compose/)
