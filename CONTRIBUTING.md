# Contributing

## Local setup

1. Clone this repository.
2. Copy it into Cursor's local plugins folder as `leapwork-play`, leaving out `.git`. Use a real copy: Cursor did not pick up the plugin through a Windows junction.

   ```powershell
   # Windows
   robocopy C:\path\to\play-cursor-plugin "$env:USERPROFILE\.cursor\plugins\local\leapwork-play" /E /XD .git
   ```

   ```bash
   # macOS and Linux
   mkdir -p ~/.cursor/plugins/local
   rsync -a --exclude .git ./ ~/.cursor/plugins/local/leapwork-play/
   ```

3. Quit Cursor completely and open it again. **Developer: Reload Window** is not enough, because plugins are read when Cursor starts.
4. Open the **Customize** page and check that **Leapwork Play** shows under **Plugins** with its logo.
5. In Agent chat, ask "create a test case in Leapwork" and sign in when asked.

Run the copy from step 2 again after every change, then restart Cursor.

## Troubleshooting

- **Leapwork Play shows under MCPs but not under Plugins**: that entry comes from an `mcp.json` (for example a workspace's `.cursor/mcp.json`), not from this plugin. Check step 2's folder and restart Cursor.
- **The agent calls another Leapwork server**: turn off other Leapwork Play MCP servers (dev, QA or localhost) in Cursor's MCP settings while testing. They expose the same tool names as the plugin's `play` server.

## Notes

- `README.md` is the plugin's page for users, so keep it written for them.
- Keep paths in `.cursor-plugin/plugin.json` relative, with no `..`.
- Publish by submitting this repository at [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish).
