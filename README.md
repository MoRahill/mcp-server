 mcp-server

A simple [Model Context Protocol (MCP)](https://modelcontextprotocol.io) server built with Python and `FastMCP`. It acts as an **AI Sticky Notes** app: an AI assistant (like Claude) can save notes, read them back, and summarize them, all stored in a plain text file.


 Requirements

- Python (see `.python-version`)
- [uv](https://docs.astral.sh/uv/) package manager

Installation

1. Clone the repository:

   bash
   git clone https://github.com/<your-username>/mcp-server.git
   cd mcp-server
   

2. Install dependencies:

   bash
   uv sync
   

   If you are setting up from scratch instead, run:

   bash
     uv add "mcp[cli]"
   

Running the Server

Test with the MCP Inspector

The quickest way to try the tools, resource, and prompt in your browser:

bash
uv run mcp dev main.py


Run directly

bash
uv run main.py


Connecting to Claude Desktop

Install the server into Claude Desktop with one command:

bash
uv run mcp install main.py




Restart Claude Desktop afterward. You should see the server's tools available in the chat.

 Usage Examples

Once connected, try asking your AI assistant:

- "Add a note: buy groceries tomorrow"
- "Show me all my notes"
- "What's my latest note?"
- "Summarize my notes"

 How It Works

- Notes are stored one per line in `notes.txt`, located next to `main.py`.
- The file is created automatically the first time a tool, resource, or prompt runs.
- `add_note` appends the message followed by a newline.
- `read_notes` returns the file contents, or `"No notes yet."` if it is empty.
- `notes://latest` returns the last line of the file.
- `note_summary_prompt` embeds all notes in a prompt: `Summarize the current notes: ...`

 Notes and Limitations

- Notes are stored in plain text with no encryption, so avoid saving sensitive information.
- There is no way to edit or delete individual notes through the server; edit `notes.txt` directly if needed.
- Multi-line messages will be split across several lines, so `notes://latest` returns only the last line.

