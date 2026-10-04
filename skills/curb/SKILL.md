---
name: curb
description: Move a website to Curb or work on a site already hosted there — start a migration or rebuild from a URL, check build status, get a checkout link, connect a domain, edit copy, restore a version, or read contact-form enquiries. Use when the user mentions Curb, moving or migrating their website, hosting, connecting a domain, or changing text on their Curb site.
---

# Working with Curb

Curb hosts websites on a static, AI-ready stack. The `curb` MCP server acts on the user's own Curb account. If its tools fail with an authentication error, tell the user to run `/mcp`, choose `curb`, and sign in; nothing else is needed.

## Always first

Call `account_overview`. It lists every site with its `id`, stage, preview and live addresses, and whether it is `migrated` (copied as-is) or rebuilt. Every site tool takes that `id` as `site_id`.

## Moving a website to Curb

1. Ask for their current website address if you do not have it.
2. `site_create` with the URL. Use `track: "migrate"` (the default) to copy the site as it is; use `"rebuild"` only if they want a fresh site written from what the current one says.
3. `site_status` with the returned id. Building takes minutes to hours; do not poll in a tight loop. Tell them they will get an email when the preview is ready, and offer to check again later.
4. When there is a `previewUrl`, give it to them to look at.
5. `plans_list`, then `checkout_link` with the plan they choose. They pay on Curb's page; never ask for card details.
6. After they have paid, `domain_lookup` on their domain, explain what you found in plain words (who hosts the DNS, whether it carries email), then `domain_connect`. Give them the one record to add, exactly as returned. Email is never touched. When they say it is added, `domain_status`.

## Editing a site

- Rebuilt site: `site_get` shows the content and which fields can change, with length limits. Propose with `site_propose` (dotted paths, string values).
- Migrated site: `site_get` will say there is no stored content. Use `site_request_change` with the change in the user's own words, including any exact text.
- Both return a change that is **waiting for approval**. Show the user exactly what will change and call `changes_approve` only after they say yes. Then `changes_list` shows when it is live.
- `site_versions` and `site_revert` put an earlier version back; confirm first, it publishes.

## Rules

- Never invent facts about the business: hours, prices, awards, licence numbers. Ask.
- One question at a time; the user may not be technical.
- Repeat DNS values only as a tool returned them.
- `leads_list` holds people's contact details; summarise, do not paste them elsewhere.
