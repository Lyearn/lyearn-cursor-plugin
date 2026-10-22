# Lyearn for Cursor

Connect Cursor to a Lyearn workspace. Agents can search company knowledge, find people, look up learning and skills, and read workforce analytics, using only the access that member already has.

The plugin adds one remote MCP server, `lyearn`, at `https://api.use1.lyearn.com/productivity/mcp`. There is no API key to paste.

## Requirements

- Cursor 3.13.0 or later. That is the first version that installs this plugin format, including a remote MCP server that signs the member in with OAuth. Older versions will not offer the plugin.
- A Lyearn account in the workspace you want to use.

## Install

**From the marketplace.** Open Customize, search for Lyearn, and install it. Reload Cursor if the server does not appear.

**From this folder, before it is published.** Copy this directory to `~/.cursor/plugins/local/lyearn`, so `.cursor-plugin/plugin.json` sits directly inside that folder. Copy the files. A symlink to a checkout elsewhere is skipped. Then restart Cursor, or run **Developer: Reload Window**.

Open Customize and confirm the Lyearn MCP server is listed. A marketplace plugin with the same name takes precedence over the local copy. On an Enterprise team, an admin must turn on **Allow Local Plugin Imports**. That setting is off by default, and when it is off Cursor ignores `~/.cursor/plugins/local`.

## Sign in

Cursor discovers the server's OAuth endpoints and opens Lyearn's sign-in page. It does not ask for a client id or secret.

1. Install the plugin and connect the Lyearn server.
2. Sign in as yourself and, if you belong to more than one workspace, pick one.
3. Approve the access you want to grant. Pay data is off until you opt in. Org changes are created as drafts for someone to review in Lyearn. They are not published from Cursor.
4. The agent then acts with your permissions. A tool you cannot use in Lyearn is not offered.

Disconnect from **Profile → Connected AI apps**. An admin can also remove connections from **Settings → Manage → AI app connections**.

## Configuration

`mcp.json` is the only configuration:

```json
{
  "mcpServers": {
    "lyearn": {
      "url": "https://api.use1.lyearn.com/productivity/mcp"
    }
  }
}
```

Leave the URL as it is for the public Lyearn edge. To point a local copy at another edge, change `url` and keep the path `/productivity/mcp`. The manifest in `.cursor-plugin/plugin.json` references this file. There are no plugin variables to fill in.

## Example prompts

- Find Priya Sharma and tell me her title and manager.
- What does our company knowledge say about the sales process?
- Which learning content covers onboarding for new managers?
- How is my team's productivity trending this month?
- Draft an org change that moves Support under Customer Operations. Leave it as a draft.

Ask for a person, a record, or a report the way you would in Lyearn. If a result is paged, ask Cursor to continue from where it left off.

## Troubleshooting

**The server is not listed.** Reload the window. For a local install, confirm the copy is at `~/.cursor/plugins/local/lyearn` and is a real directory. Check that no marketplace plugin named `lyearn` is installed, and that Enterprise local plugin imports are allowed.

## License

[MIT](LICENSE).
