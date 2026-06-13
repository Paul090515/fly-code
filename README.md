# FLY code

FLY code is a multi-model terminal coding agent. It can inspect a project, read
and edit files with confirmation, run approved shell commands, and help with Git
workflows from a focused command-line interface.

This project is an original implementation. It is inspired by modern terminal
coding assistants, but it does not copy proprietary branding, UI assets, or
private behavior.

## Install

From npm, after publishing:

```bash
npm install -g fly-code
fly
```

For local development:

```bash
npm install
npm run build
npm link
fly --help
```

## Quick Start

Set a provider and model:

```bash
fly config set provider openai
fly config set model gpt-4.1-mini
```

Use environment variables for secrets:

```bash
set OPENAI_API_KEY=your-key
set ANTHROPIC_API_KEY=your-key
```

Run one-shot mode:

```bash
fly "summarize this project"
```

Run interactive mode:

```bash
fly
```

Create project instructions in `FLY.md`:

```markdown
# FLY instructions

- Prefer small, tested changes.
- Run npm test before finishing TypeScript changes.
```

## Providers

Supported provider names:

- `openai`: OpenAI Chat Completions API.
- `anthropic`: Anthropic Messages API.
- `local`: Any OpenAI-compatible local or self-hosted endpoint.
- `fake`: Deterministic provider for smoke tests and demos.

Useful config keys:

```bash
fly config set provider openai
fly config set model gpt-4.1-mini
fly config set baseUrl http://localhost:11434/v1
fly config list
```

## Safety Model

- Read-only tools run automatically.
- File writes require confirmation unless `--trusted` is set.
- Shell commands require confirmation.
- Destructive shell commands always require explicit confirmation.
- API keys and common secret values are redacted before prompts are sent to a
  provider.

## Development

```bash
npm install
npm run typecheck
npm test
```

## GitHub Deployment

Create a GitHub repository named `fly-code`, then push this folder:

```bash
git init
git add .
git commit -m "Initial FLY code CLI MVP"
git branch -M main
git remote add origin https://github.com/YOUR_NAME/fly-code.git
git push -u origin main
```

Publishing to npm:

```bash
npm login
npm publish
```
