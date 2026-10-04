# Curb for Claude Code and Grok Build

[Curb](https://hicurb.com) moves your website onto fast, AI-ready hosting and
keeps it there. This plugin connects your agent to your Curb account so it can
do the whole job from the terminal:

- move a website to Curb (migrate it as-is, or rebuild it)
- follow the build and share the preview
- send you to checkout and connect your domain, without touching email
- edit copy, restore an earlier version, and read contact-form enquiries

Nothing is published until you say yes.

## Install

```text
/plugin marketplace add Adamparishspok/curb-plugin
/plugin install curb@curb
/mcp
```

In `/mcp`, choose **curb** and sign in to Curb. There is no key to copy; a
Curb account is made on the way if you do not have one.

Grok Build reads Claude Code marketplaces, so the same two commands work there.

### Just the MCP server

```bash
claude mcp add --transport http curb https://app.hicurb.com/api/mcp
```

The server also works from ChatGPT, Claude and Grok as a custom connector.
See [hicurb.com/agents](https://hicurb.com/agents).

## What is in here

- `.mcp.json`: the Curb MCP server (`https://app.hicurb.com/api/mcp`, OAuth)
- `skills/curb/SKILL.md`: how the agent should use it

## Support

hello@hicurb.com · [Privacy](https://hicurb.com/privacy) · [Terms](https://hicurb.com/terms)
