# VSCXML Marketplace for Claude Code, ChatGPT, and Codex

Public preview marketplace for the VSCXML state-machine plugin. Version 0.4.0
contains both Claude Code marketplace metadata and the OpenAI
`.agents/plugins/marketplace.json` catalog.

## Codex installation

Register the exact 0.4.0 marketplace:

```powershell
codex plugin marketplace add miho/vscxml-marketplace --ref 0.4.0
```

For the normal user-facing flow, start `codex`, enter `/plugins`, switch to the
`vscxml-marketplace` tab, open VSCXML, and install it. The supported CLI
equivalent is:

```powershell
codex plugin add vscxml@vscxml-marketplace
codex plugin list
```

Start a new Codex task or CLI session after installation. Ask it to:

> Use VSCXML to check all backend connections and list every generator target.

The installed plugin supplies 60 MCP tools, four namespaced skills, and nine
generator targets. Explicit Codex skill names are:

| Skill | Description |
|---|---|
| `$vscxml:design` | Create and visualize SCXML state machines |
| `$vscxml:simulate` | Test behavior with event injection and tracing |
| `$vscxml:generate` | Generate native code for all nine targets |
| `$vscxml:trace` | Record, compare, and replay execution traces |

## ChatGPT preview path and limitation

After registering the marketplace, refresh the ChatGPT desktop app and open
**Plugins → Personal → VSCXML**. Install the plugin, then start a new chat or
Codex task. OpenAI documents this common plugin directory and the new-chat
requirement in its [plugin guide](https://learn.chatgpt.com/docs/plugins).

This preview uses a local `stdio` MCP server to reach desktop applications. It
is fully validated in a local Codex host. A public OpenAI plugin-directory
submission cannot currently distribute a local-only `stdio` server; ChatGPT
web and remote hosts need a reviewed HTTPS MCP endpoint or Secure MCP Tunnel.
The repository marketplace is therefore a preview-user distribution, not a
claim that VSCXML is already listed in OpenAI's public directory.

## Preview application prerequisites

Install and start the matching VSCXML 0.1.0 preview applications first:

- Generator: port 48620
- Simulator: port 48621
- Editor: port 48623

The current Windows preview installers are unsigned. Download them only from a
trusted VSCXML preview distribution, verify the version, and review any Windows
SmartScreen prompt before continuing. Plugin installation does not install or
update these applications.

The plugin pins its npm MCP dependency to `@vscxml/mcp@0.1.42` and does not use
an unversioned `npx` dependency.

## Update and uninstall

A marketplace added with `--ref 0.4.0` is intentionally pinned. When a new
preview is published, replace `0.4.1` with its exact tag:

```powershell
codex plugin remove vscxml@vscxml-marketplace
codex plugin marketplace remove vscxml-marketplace
codex plugin marketplace add miho/vscxml-marketplace --ref 0.4.1
codex plugin add vscxml@vscxml-marketplace
```

An intentionally unpinned marketplace can use `codex plugin marketplace
upgrade vscxml-marketplace` before reinstalling instead. Start a new task after
an update. To remove both the plugin and this marketplace:

```powershell
codex plugin remove vscxml@vscxml-marketplace
codex plugin marketplace remove vscxml-marketplace
```

## Claude Code

```text
/plugin add-marketplace https://github.com/miho/vscxml-marketplace
/plugin install vscxml
```

Claude Code explicit commands remain `/vscxml:design`, `/vscxml:simulate`,
`/vscxml:generate`, and `/vscxml:trace`.

## Available plugin

| Plugin | Description |
|---|---|
| **vscxml 0.4.0** | W3C SCXML Editor, Simulator, and Generator integration |

See the [plugin repository](https://github.com/miho/vscxml-plugin) and
[vscxml.com](https://vscxml.com) for tool and workflow details.
