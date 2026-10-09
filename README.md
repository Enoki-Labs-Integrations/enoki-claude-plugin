# Enoki

Enoki tests AI agents for security and safety weaknesses. It attacks your agent the way an adversary would, shows the exact attack and how your agent responded, and re-verifies a fix once you have made it.

This plugin connects Claude to Enoki and adds one skill, `test-agent-change`. After you change an agent's system prompt, tools, model or guardrails, ask Claude to test the change. Claude starts an Enoki assessment scoped to what the change touched, reports what it found, and re-runs the attacks behind a finding you fixed.

## What the plugin contains

- **A connection to Enoki's MCP server** at `https://mcp.enokilabs.ai/mcp`. It gives Claude Enoki's tools: register an agent, start and stop assessments, read findings, close them and re-verify fixes.
- **The skill `test-agent-change`**, which tells Claude how to use those tools to check one change.

The plugin runs nothing on your machine. Claude calls Enoki's MCP server, and Enoki runs the assessments from its own servers against the agent endpoint you register.

## Install

In Claude Code:

```
/plugin install enoki --marketplace ethicgate/enoki-claude-plugin
```

## Before you start

You need an Enoki workspace. The first time Claude calls Enoki, you sign in and approve the connection on app.enokilabs.ai; only a workspace owner or admin can approve it. You can also connect with a workspace API key instead. [Connect your agent](https://docs.enokilabs.ai/connect-your-agent) has both ways.

Register a test or staging deployment of your agent rather than production: an assessment sends adversarial messages to it.

## Try it

- "I changed the refund tool in our support agent. Test it with Enoki."
- "What did the last Enoki run find on our support agent?"
- "I fixed the prompt leak Enoki found. Check that it is fixed."

## Privacy and support

- Privacy policy: https://enokilabs.ai/privacy
- Documentation: https://docs.enokilabs.ai
- Support: hello@enokilabs.ai
