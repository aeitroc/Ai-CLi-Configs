# AI Assistant Configuration

This directory contains configuration files for enhancing the capabilities of AI assistants like Claude and Codex. The primary configuration is for the Model Context Protocol (MCP), which allows the AI to interact with various external tools and services.



### How it Works

When an AI assistant needs to use a tool, it references one of the servers defined in this file. The configuration specifies the command to execute, any arguments to pass, and necessary environment variables. This setup allows for a flexible and powerful way to extend the AI's capabilities.

### Configured MCP Servers

Below is a table detailing the servers configured in `.mcp-servers.json`.

| Server Name | Description | Command/Package |
| :--- | :--- | :--- |
| `git` | Git operations (commits, branches, diffs) | `npx -y mcp-git` |
| `git-advanced` | Advanced Git operations and analysis | `npx -y @cyanheads/git-mcp-server` |
| `sqlite` | SQLite database management | `npx -y mcp-sqlite` |
| `postgres` | PostgreSQL database operations | `npx -y enhanced-postgres-mcp-server` |
| `fetch` | HTTP requests and web scraping | `npx -y mcp-fetch` |
| `memory` | Memory storage for context persistence | `npx -y @modelcontextprotocol/server-memory` |
| `everything` | Comprehensive MCP server with multiple tools | `npx -y @modelcontextprotocol/server-everything` |
| `claude-context` | Claude context management with Zilliz vector database | `npx -y @zilliz/claude-context-mcp` |
| `ref-tools` | Reference and documentation tools | `npx -y ref-tools-mcp` |
| `qdrant` | Qdrant vector database operations | `/Users/user/.local/bin/mcp-server-qdrant` |
| `playwright` | Web automation and testing with Playwright | `npx -y playwright-mcp` |
| `codex` | Advanced reasoning and code generation with Codex | `codex mcp` |
| `memory-agent-stdio` | Memory agent MCP server with stdio transport | `bash -lc "cd ... && uv run ..."` |

### Custom Configurations

Several servers have custom configurations worth noting:

*   **`qdrant`**: Connects to a local Qdrant instance at `http://localhost:6333`.
*   **`codex`**: Configured for high reasoning effort by setting the `CODEX_MODEL_REASONING_EFFORT` environment variable.
*   **`memory-agent-stdio`**: Runs a local Python-based MCP server from `/Users/besi/.codex/mem-agent-mcp` using `uv`.

## Usage

These configurations are likely loaded by an AI client or development environment that supports the Model Context Protocol. Ensure that the client is configured to read the `.mcp-servers.json` file from this directory.

### Prerequisites

For the servers to function correctly, you may need to have certain tools and packages installed:

*   **Node.js and `npx`**: Required for most servers, which are npm packages.
*   **Local Binaries**: The `qdrant` and `codex` servers rely on executables being available in the system's `PATH` or at a specified location.
*   **Python Environment**: The `memory-agent-stdio` server requires a Python environment with `uv` and the necessary dependencies installed in its project directory.
*   **Running Services**: Some servers, like `qdrant` and `postgres`, may require the corresponding database service to be running.
