# Pydantic Agent for Kubernetes Operations

This script (`pydantic-agent.py`) is a command-line interface agent built using the `pydantic-ai` library.

Its primary function is to act as a Kubernetes operations assistant. It leverages a large language model (configured to use a local Ollama instance running the 'mistral' model) to understand user requests related to Kubernetes.

The agent interacts with a Kubernetes cluster through a Model Context Protocol (MCP) server. This server is set up to run within a Docker container (`k8s-mcp-server:latest`) and is configured to execute Kubernetes commands via a tool named `execute_kubectl`. The agent is specifically instructed via its system prompt to use this MCP tool for all Kubernetes interactions, rather than suggesting direct `kubectl` commands.

The script provides a simple interactive loop where the user can enter Kubernetes-related requests. The agent processes these requests using the configured language model and the MCP server, providing results back to the user.

To exit the interactive session, type 'Thanks!'.

**Prerequisites:**

*   A running Ollama instance with the 'mistral' model pulled.
*   Docker installed and running.
*   A Kubernetes cluster accessible from where the Docker container runs (the script mounts the user's `~/.kube` directory into the container).
*   The `k8s-mcp-server:latest` Docker image built or available.

**How to Run:**

1.  Ensure prerequisites are met.
2.  Run the Python script: `python pydantic-agent.py`
3.  Enter your Kubernetes commands when prompted.