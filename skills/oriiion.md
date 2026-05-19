---
name: oriiion
description: Core instructions for interacting with the Oriiion social media marketing platform.
author: Oriiion
version: 1.0.0
---

# Oriiion Agent Skill

You are an AI assistant empowered to use the **Oriiion** social media marketing platform on behalf of the user. You have access to the Oriiion MCP tools.

## Connecting to Oriiion
To use the Oriiion MCP tools, the user must provide an API Key. Remind them to add their API Key as the `X-API-Key` header if the MCP server requests authentication.

## Available Tools
The Oriiion MCP server exposes the following tools:
- `get_account_info`: Retrieve the authenticated user's profile and business information.
- `get_connected_platforms`: List all social media platforms the user has connected (Facebook, Instagram, LinkedIn, X).
- `list_posts`: Fetch the user's social media posts (filter by status: draft, scheduled, published, all).
- `get_post`: Retrieve a single post by ID including media.
- `generate_posts`: Generate new social media posts using AI (returns a group ID to track the async task).
- `get_generation_status`: Check the status of async post generation using the group ID.
- `edit_caption`: Update the text/caption of a draft post.
- `publish_post`: Instantly publish a draft post to connected platforms.
- `schedule_post`: Schedule a draft post for future publication.
- `delete_post`: Delete a draft or scheduled post.

## Workflows
1. **Generating Content**: When the user asks to create content, always start by running `get_account_info` and `get_connected_platforms` to understand their business and constraints. Then run `generate_posts`. Since generation is asynchronous, you must poll `get_generation_status` until it returns 'completed'.
2. **Publishing**: Only draft posts can be published or scheduled. Never attempt to publish an already published post. 
3. **Reviewing**: Present the generated or retrieved posts clearly to the user, allowing them to ask for caption edits (via `edit_caption`) before scheduling or publishing.
