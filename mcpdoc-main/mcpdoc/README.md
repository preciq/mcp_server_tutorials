# MCPDoc + MCP Inspector (SSE) Quickstart

This guide documents the working steps to connect the MCP Inspector to the
MCPDoc server over SSE.

## Prerequisites

- `uvx` installed and available on your PATH
- `npx` available (Node.js installed)

## Steps

1. Start the MCPDoc server in SSE mode:
   ```bash
   uvx --from mcpdoc mcpdoc \
     --urls "LangGraph:https://langchain-ai.github.io/langgraph/llms.txt" "LangChain:https://python.langchain.com/llms.txt" \
     --transport sse \
     --port 8082 \
     --host localhost
   ```

2. In a separate terminal, start the MCP Inspector:
   ```bash
   npx @modelcontextprotocol/inspector
   ```

3. Open the Inspector UI using the tokenized URL printed in the terminal.

4. In the Inspector UI, select **SSE** transport.

5. Set the server URL to:
   ```
   http://localhost:8082/sse
   ```

6. Click **Connect**.

7. Verify the tools list appears (e.g., `list_doc_sources`, `fetch_docs`).

## Troubleshooting

- If you see `spawn mcp-server-everything ENOENT`, you are in **STDIO** mode.
  Switch to **SSE** in the Inspector.
- If connection fails, confirm the server is listening on port 8082:
  ```bash
  ss -lntp | rg ':8082'
  ```
