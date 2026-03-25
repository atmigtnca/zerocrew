Set up hwpx-mcp-server globally. Execute the following steps in order:

## Step 1: Check uvx
- Run `which uvx` to check if uvx is installed
- If not found: install with `pip install uv`, then re-check
- Record the uvx path (e.g., /home/ubuntu/.local/bin/uvx)

## Step 2: Verify hwpx-mcp-server
- Run `uvx hwpx-mcp-server --help` to verify the package is available
- If it fails, notify the user

## Step 3: Configure project .mcp.json
- Check the `.mcp.json` file at the project root
- If it is missing or lacks hwpx configuration, create/update it with:
```json
{
  "mcpServers": {
    "hwpx": {
      "command": "[uvx path]",
      "args": ["hwpx-mcp-server", "--transport", "stdio"]
    }
  }
}
```
- If already configured, inform the user that it is already set up

## Step 4: Confirmation
- Report the setup result to the user
- Inform: "After restarting Claude Code, an MCP server approval popup will appear. Please click 'Allow'."

$ARGUMENTS
