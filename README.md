# Meniscus — liquid glass design system for AI agents (MCP)

[![Meniscus: liquid glass your AI gets right](https://meniscus.site/og/home.jpg)](https://meniscus.site)

Meniscus is a hosted MCP server that teaches design and coding agents real liquid glass: edges that bend the world
behind them, not blurred cards. It gives Claude Code, Cursor, VS Code and any MCP client a tested design language with
numbers, 34 component and 10 effect specs, build recipes for Figma, web, SwiftUI, Flutter and React Native, and
100+ verified reference renders. Numbers follow the current generation of the look (iOS 27 / macOS 27).

**Website:** [meniscus.site](https://meniscus.site) · **Docs:** [meniscus.site/docs](https://meniscus.site/docs) ·
**Guide:** [What is liquid glass?](https://meniscus.site/liquid-glass) · **Specs:** [components](https://meniscus.site/components),
[effects](https://meniscus.site/effects) · **Pricing:** [meniscus.site/pricing](https://meniscus.site/pricing)

## Server URL

```
https://meniscus.site/mcp
```

Remote server, Streamable HTTP. Sign-in is OAuth in the browser: there is no API key to paste. Listed in the official
MCP Registry as `site.meniscus/meniscus` ([server.json](server.json)).

## Connect

**Claude Code**

```bash
claude mcp add --transport http meniscus https://meniscus.site/mcp
```

Then run `/mcp` in Claude Code and choose meniscus to sign in.

**Claude desktop and claude.ai:** Settings → Connectors → Add custom connector, paste the server URL, then Connect.

**Cursor:** add to `~/.cursor/mcp.json` (or the project's `.cursor/mcp.json`):

```json
{
  "mcpServers": {
    "meniscus": { "url": "https://meniscus.site/mcp" }
  }
}
```

**VS Code:** add to `.vscode/mcp.json`:

```json
{
  "servers": {
    "meniscus": { "type": "http", "url": "https://meniscus.site/mcp" }
  }
}
```

Any other client that supports remote servers with OAuth works the same way: give it the URL; it discovers the sign-in
by itself.

## Ask for a screen

Name the platform and the parts; your agent picks the tools.

```
Design a dark macOS notes app with a glass sidebar and toolbar in Figma.
Build it in SwiftUI next. Use the meniscus tools and check your screenshot against the brief's checklist.
```

## Tools

| Tool | What it returns |
|---|---|
| `create_design_brief` | One call for a concrete screen: direction, tokens, specs of the components it names, build notes and limits for your stack, a checklist and two reference images. |
| `get_guidelines` | The design language; with a medium (`design-tool`, `web`, `swiftui`, `flutter`, `react-native`) also that medium's recipe. |
| `get_component_spec` | One of 34 components: material, geometry, optics numbers, anatomy, states, rules, references. |
| `get_effect_spec` | One of 10 effects or accent materials: refraction, frost, specular, dispersion, iridescence, caustics, morph, tint, liquid metal, border beam. |
| `search_references` | Search the reference renders by text and filters (kind, component, effect, platform, theme). |
| `get_references` | Load reference images by id, cropped to the glass or full frame. |
| `get_platform_support` | What is implemented and verified on each platform. |

All tools are read-only.

## Plans

**Free:** the design language, every spec, web and design-tool recipes, 1 image per spec, 30 tool calls a day, no card
needed. **Pro, Team and Lifetime:** every medium (SwiftUI, Flutter, React Native), every image, screen templates, the
React Native starter and 2,000 calls a day (fair use). Limits reset at 00:00 UTC. Details:
[meniscus.site/pricing](https://meniscus.site/pricing).

## For agents and crawlers

- [llms.txt](https://meniscus.site/llms.txt) and [llms-full.txt](https://meniscus.site/llms-full.txt)
- Every page has a Markdown copy, e.g. [docs.md](https://meniscus.site/docs.md)
- [Changelog](https://meniscus.site/changelog) ([Atom feed](https://meniscus.site/changelog.xml))

## About this repository

This repository holds the public listing and setup documentation. The server itself is a hosted service at
meniscus.site; its source is not published here. Questions, bugs and refunds: [support@meniscus.site](mailto:support@meniscus.site),
or open an issue.

---

Meniscus is an independent product and is not affiliated with, endorsed by or sponsored by Apple Inc. Apple, iPadOS,
macOS, SwiftUI, Xcode, SF Symbols, visionOS and Metal are trademarks of Apple Inc., registered in the U.S. and other
countries and regions. IOS is a trademark or registered trademark of Cisco in the U.S. and other countries and is used
under licence. The words liquid glass are used only to describe a visual style.
