# mcpscan

**Security scanner for MCP servers and AI agent configurations.** It finds tool poisoning, rug pulls, unpinned packages, over-broad filesystem access and leaked secrets before your agent does.

> 🚧 Under active development. See the [first-version spec](docs/SPEC.md).

```
$ mcpscan scan
CRITICAL  MCP101  tool "read_notes" description contains hidden instructions targeting ~/.ssh
HIGH      MCP001  OPENAI_API_KEY stored in plaintext in claude_desktop_config.json
MEDIUM    MCP002  server "fs-tools" runs `npx -y fs-tools` with no version pin
```

- ⚡ Single static binary for Windows, macOS and Linux
- 🔍 Discovers Claude Desktop, Claude Code, Cursor, VS Code and Windsurf configs
- 🧾 SARIF output and a GitHub Action for code scanning
- 🔒 Lockfile-based rug-pull detection

## License
[Apache-2.0](LICENSE) © DarkDataLabs
