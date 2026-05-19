# Oriiion Agent Plugin

This repository contains the official Agent Plugin for **Oriiion**, the AI-powered social media marketing platform. 

It provides AI agents (like Claude Code and other MCP-compatible clients) with the "brain" (instructional skills) and "hands" (MCP server tools) needed to interact with your Oriiion workspaces.

## Installation

You can install this skill directly into compatible agents. 

**For Cursor (and similar IDE agents):**
Type this directly into your agent chat:
```text
/plugin install oriiion-AI/oriiion-skills
```

**For Claude Code:**
Run this in your terminal:
```bash
npx skills add https://github.com/oriiion-AI/oriiion-skills --skill oriiion
```

## Requirements

To use this plugin, you must have an active Oriiion account and an **API Key**. 

When the agent attempts to use an Oriiion tool (like generating a post or fetching workspaces), it will ask you for your API key. You must provide it as the `X-API-Key` header, or simply provide it to the agent directly in the chat so it can authenticate on your behalf.

## Features
- **Workspace Management**: Fetch your active workspaces.
- **Social Media Generation**: Generate text and images for LinkedIn, Facebook, Instagram, Twitter, and more.
- **Async Polling**: Built-in skill instructions guide the agent on how to correctly wait for long-running generations.
- **Publishing**: Schedule or immediately publish generated content to your connected social channels.
