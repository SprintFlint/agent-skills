# SprintFlint Agent Skills

Two ways to give an AI assistant access to your SprintFlint workspace.

## Option 1: MCP server (recommended)

SprintFlint hosts a public MCP server at `mcp.sprintflint.com` — eight day-one tools (`list-projects`, `list-sprints`, `list-issues`, `my-issues`, plus issue/comment write tools).

**Setup:** copy the JSON config block from [sprintflint.com/mcp](https://sprintflint.com/mcp) into Claude Desktop, Cursor, or Zed. For Claude Code, use `claude mcp add` with the snippet on the same page.

**Auth:** bearer token — same token as the REST API. Generate one from [SprintFlint](https://sprintflint.com) → "My Profile" → "API Token".

## Option 2: REST API skill (this repo)

For agents that don't speak MCP. The skill in [SKILL.md](SKILL.md) wraps the REST API directly.

### 1. Get your API token

[SprintFlint](https://sprintflint.com) → "My Profile" → "API Token" → "Generate Token".

### 2. Set your token as an env var

```bash
export SPRINTFLINT_API_TOKEN="your-token-here"
```

Or add to your project's `.env` file:

```
SPRINTFLINT_API_TOKEN=your-token-here
```

### 3. Point your agent at the skill

Reference [SKILL.md](SKILL.md) from your agent's skill loader (Cursor, Claude Code, or any agent runtime that supports markdown skill files). It documents the endpoints the agent should call.

## Usage

With either option configured, ask your assistant things like:

```
List my SprintFlint projects
```

```
Create an issue in project 1, sprint 3: "Fix login button styling"
```

```
Update issue SF-42 status to done
```

```
Add a comment to SF-42: "Completed the refactor"
```

## API base URL

`https://sprintflint.com/api/v1`

## Security

- Never commit your API token to version control.
- Use environment variables or a secret manager.
- The token has the same permissions as your account.

## License

MIT
