<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=22&pause=1200&color=2F81F7&center=true&vCenter=true&width=640&lines=Making+documents+talk+to+AI+agents;MCP+servers+for+GroupDocs+.NET+libraries;On-premise%3A+documents+stay+on+your+machine;PDF%2C+Word%2C+Excel+%E2%86%92+agent-ready+tools" alt="Making documents talk to AI agents" />

[![MCP servers](https://img.shields.io/badge/GroupDocs_MCP_servers-15-2F81F7?style=flat-square&logo=modelcontextprotocol&logoColor=white)](https://github.com/groupdocs/GroupDocs.Mcp.Installer)
[![NuGet](https://img.shields.io/badge/NuGet-GroupDocs.*.Mcp-004880?style=flat-square&logo=nuget&logoColor=white)](https://www.nuget.org/packages?q=GroupDocs.Mcp)
[![Docker Hub](https://img.shields.io/badge/Docker_Hub-groupdocs-2496ED?style=flat-square&logo=docker&logoColor=white)](https://hub.docker.com/u/groupdocs)
[![PyPI](https://img.shields.io/badge/PyPI-groupdocs--*--net-3775A9?style=flat-square&logo=pypi&logoColor=white)](https://pypi.org/search/?q=groupdocs)
[![Docs MCP](https://img.shields.io/badge/docs.groupdocs.com-%2Fmcp-111?style=flat-square)](https://docs.groupdocs.com/mcp)

</div>

Hi, I'm **Vladimir** — Group Manager at [GroupDocs](https://www.groupdocs.com). I build the bridge between document-processing libraries and AI agents: MCP servers, agent-friendly docs, and Python packages that wrap .NET. One rule for all of it: **documents stay on your machine**. Every server runs on-premise, talks to the agent over stdio, and never sends a file to GroupDocs.

### `// ~/WhoAmI.cs`

```csharp
var me = new Developer
{
    Name  = "Vladimir Litvinchik",
    Role  = "Group Manager @ GroupDocs",
    Stack = ["C#", ".NET", "Python", "Docker", "GitHub Actions"],
    Focus = ["Model Context Protocol", "On-premise document processing", "Developer tooling"],
    Motto = "If an agent can't use it, it isn't documented yet."
};
```

### `// ~/OnPremise.cs` — why your documents never leave your machine

- **Local by design.** A server runs next to your files — `dnx` on the .NET 10 SDK, or a Docker container — and talks to the agent over stdio. Documents, extracted text and metadata stay on the machine that runs the server. Nothing is uploaded to GroupDocs or anyone else ([network access and data privacy](https://docs.groupdocs.com/parser/net/network-access-and-data-privacy/)).
- **Works offline.** A license file is validated locally, so with one in place you can block all egress and the server keeps working. Metered pay-per-use licensing is the single opt-in mode that needs connectivity, which is why air-gapped boxes use a license file. Without any license the servers run in evaluation mode, with limits.
- **Your storage, your rules.** Point a server at a folder, or plug in the S3 / Azure Blob providers from [GroupDocs.Mcp.Core](https://github.com/groupdocs/GroupDocs.Mcp.Core) when the files live in your own cloud. Pin versions in shared configs (`GroupDocs.Parser.Mcp@26.11.0`, image tag `:26.11.0`) so what runs is what you reviewed.

<sub>Not sure which option fits? The docs compare them: [SDK, Cloud or MCP?](https://docs.groupdocs.com/parser/python-net/sdk-cloud-mcp/)</sub>

### `// ~/McpServers.cs` — give your agent document superpowers

**15 servers, one pattern.** Each wraps a GroupDocs .NET library, runs from NuGet with `dnx` or as a Docker image, and is listed in the MCP Registry. Search and Total are Docker-only because they exceed NuGet's 250 MB limit.

| Server | What your agent can do | Run with |
|---|---|---|
| [**Parser**](https://github.com/groupdocs-parser/GroupDocs.Parser.Mcp) | Extract text, tables, images, barcodes and metadata | `dnx` · Docker |
| [**Conversion**](https://github.com/groupdocs-conversion/GroupDocs.Conversion.Mcp) | Convert between 80+ formats — PDF, Word, Excel, PowerPoint, HTML, images | `dnx` · Docker |
| [**Viewer**](https://github.com/groupdocs-viewer/GroupDocs.Viewer.Mcp) | Render any page to PNG, inspect page count and dimensions | `dnx` · Docker |
| [**Search**](https://github.com/groupdocs-search/GroupDocs.Search.Mcp) | Index a folder, then run full-text, fuzzy, boolean and date-range queries | Docker |
| [**Markdown**](https://github.com/groupdocs-markdown/GroupDocs.Markdown.Mcp) | Turn PDF, Office and EPUB files into clean Markdown for LLM context | `dnx` · Docker |
| [**Comparison**](https://github.com/groupdocs-comparison/GroupDocs.Comparison.Mcp) | Compare two documents and report the changes | `dnx` · Docker |
| [**Metadata**](https://github.com/groupdocs-metadata/GroupDocs.Metadata.Mcp) | Read, write, search and remove metadata in documents, images and media | `dnx` · Docker |
| [**Annotation**](https://github.com/groupdocs-annotation/GroupDocs.Annotation.Mcp) | Add, list, update and remove annotations and replies; import and export them | `dnx` · Docker |
| [**Redaction**](https://github.com/groupdocs-redaction/GroupDocs.Redaction.Mcp) | Redact text by regex, cover image areas, strip annotations and metadata | `dnx` · Docker |
| [**Signature**](https://github.com/groupdocs-signature/GroupDocs.Signature.Mcp) | Sign with text, QR code, barcode or certificate; verify and search signatures | `dnx` · Docker |
| [**Merger**](https://github.com/groupdocs-merger/GroupDocs.Merger.Mcp) | Merge documents and split out pages | `dnx` · Docker |
| [**Watermark**](https://github.com/groupdocs-watermark/GroupDocs.Watermark.Mcp) | Add, find and remove text and image watermarks | `dnx` · Docker |
| [**Editor**](https://github.com/groupdocs-editor/GroupDocs.Editor.Mcp) | Edit Office and PDF files through an HTML round-trip, fill form fields | `dnx` · Docker |
| [**Assembly**](https://github.com/groupdocs-assembly/GroupDocs.Assembly.Mcp) | Fill Word, Excel, PowerPoint and e-mail templates with JSON, XML or CSV data; one document per record for mail merge | `dnx` · Docker |
| [**Total**](https://github.com/groupdocs-total/GroupDocs.Total.Mcp) | 38 tools from 10 products behind one server (no Search, Editor or Assembly) | Docker |

**One-run setup for all of them →** [GroupDocs.Mcp.Installer](https://github.com/groupdocs/GroupDocs.Mcp.Installer) registers the servers in Claude Desktop, Claude Code, VS Code, Visual Studio 2022, Cursor, Windsurf, Cline and Codex CLI, or emits a `docker-compose.yml`. Shared plumbing → [GroupDocs.Mcp.Core](https://github.com/groupdocs/GroupDocs.Mcp.Core).

<details>
<summary><b>Try one in Claude Code, Claude Desktop, Cursor or VS Code in 30 seconds</b></summary>

Needs the [.NET 10 SDK](https://dotnet.microsoft.com/download). The first launch downloads the engine (~230 MB) once.

```bash
# Claude Code
claude mcp add groupdocs-parser -- dnx GroupDocs.Parser.Mcp --yes
```

Claude Desktop and Cursor (VS Code's `mcp.json` uses `"servers"` instead of `"mcpServers"`). The storage path is optional and defaults to the current directory:

```json
{
  "mcpServers": {
    "groupdocs-parser": {
      "type": "stdio",
      "command": "dnx",
      "args": ["GroupDocs.Parser.Mcp", "--yes"],
      "env": { "GROUPDOCS_MCP_STORAGE_PATH": "/path/to/documents" }
    }
  }
}
```

Prefer Docker, or need Search or Total? Mount your folder and go:

```json
{
  "mcpServers": {
    "groupdocs-search": {
      "command": "docker",
      "args": ["run", "--rm", "-i", "-v", "/path/to/documents:/data", "ghcr.io/groupdocs-search/search-net-mcp:latest"]
    }
  }
}
```

<sub>Each repo's README lists the exact tools, environment variables and license options.</sub>
</details>

### `// ~/AlsoBuilding.cs`

- 📚 **Agent-friendly docs** — pages on [docs.groupdocs.com](https://docs.groupdocs.com) have `.md` twins and an [`llms.txt`](https://docs.groupdocs.com/llms.txt) index, and the docs are themselves an MCP server your agent can search:
  ```json
  { "mcpServers": { "groupdocs-docs": { "url": "https://docs.groupdocs.com/mcp" } } }
  ```
- 🐍 **Python via .NET** — the GroupDocs libraries as [PyPI packages](https://pypi.org/search/?q=groupdocs), each with an `AGENTS.md` that coding agents auto-discover and a CLI: `pip install groupdocs-parser-net`, then `groupdocs-parser text report.pdf`.

### `// ~/WhatsNew.cs`

<!-- whats-new:start -->
- **2026-11-09** · [GroupDocs.Assembly.Mcp 26.11.0](https://www.nuget.org/packages/GroupDocs.Assembly.Mcp) — first release. Fill Word, Excel, PowerPoint and e-mail templates with JSON, XML or CSV data, or generate one document per record.
- **2026-11-09** · [GroupDocs.Total for Python via .NET 26.11.0](https://pypi.org/project/groupdocs-total-net/) is on PyPI: `pip install groupdocs-total-net` installs the 14 product packages in one step.
- **2026-11-08** · [GroupDocs.Annotation.Mcp 26.11.0](https://www.nuget.org/packages/GroupDocs.Annotation.Mcp) moves to engine 26.10.0: opening, previewing or saving a document no longer downloads the remote images and files it references.
- **2026-11-06** · [GroupDocs.Assembly for Python via .NET 26.11.0](https://pypi.org/project/groupdocs-assembly-net/) is on PyPI.
- **2026-11-05** · [GroupDocs.Parser.Mcp 26.11.0](https://www.nuget.org/packages/GroupDocs.Parser.Mcp) is on NuGet as per-runtime packages, so `dnx GroupDocs.Parser.Mcp --yes` now works. Docker is no longer the only way to run it.
<!-- whats-new:end -->

### `// ~/Contact.cs`

Building something with documents + AI and stuck?

- Open an issue on the server's repo.
- Ask on the [GroupDocs forum](https://forum.groupdocs.com/) — I track it.
- Email [developers@groupdocs.com](mailto:developers@groupdocs.com).

<div align="center"><sub>⭐ a repo if it saved you time — it really does help.</sub></div>
