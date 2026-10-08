# Beacon plugin

Beacon puts your agent's status on your iPhone: home-screen widget cards, notifications, questions you answer from your phone, and Live Activities on the Lock Screen and Dynamic Island.

This plugin bundles:

- **MCP server**: the hosted Beacon server at `https://mcp.usebcn.com/mcp`. You sign in once with your Beacon account (OAuth). There's no API key to paste.
- **Skill** (`skills/beacon`): tells the agent when to post, which surface to use, how to name itself, and to clean up after itself.

## Requirements

- The Beacon iPhone app, signed in with the same account you use to connect the plugin.
- Widgets, notifications and Live Activities are optional. Each tool result says what actually reached your device.

## Tools

| Tool | What it does |
|---|---|
| `post_update` | Post or update a status card on your widget board |
| `ask_user` | Ask a question you can answer from your phone |
| `check_replies` | Read answers to earlier questions (read-only) |
| `acknowledge_replies` | Mark answers as handled once acted on |
| `clear_card` | Remove one of the agent's own cards |
| `get_state` | Read the current board, activities, and reply counts |
| `notify_user` | Send a notification |
| `start_activity` / `update_activity` / `end_activity` | Run a Live Activity |
| `create_webhook` | Create a post-only webhook URL for a script or CI job |

## Privacy Policy

Beacon stores the cards, questions, replies, and notifications your agents send, so it can deliver them to your devices. It doesn't read your conversations or files. Full policy: https://usebcn.com/privacy

## Support

https://usebcn.com/support

## Install in Claude Code

```
/plugin marketplace add Ark-Innovations-LLC/beacon-plugin
/plugin install beacon@beacon
```

## License

MIT. See [LICENSE](LICENSE).
