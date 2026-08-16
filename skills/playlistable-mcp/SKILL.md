---
name: playlistable-mcp
description: Create AI-powered playlists and discover music via Playlistable MCP. Use when the user wants to generate a playlist from a mood or prompt, search songs or artists, get personalized playlist suggestions, or manage their playlists.
---

# Playlistable MCP

Create AI playlists and discover music using the Playlistable MCP at `https://mcp.playlistable.io`.

Authenticate with OAuth when prompted. Users can also use a personal API key from the Playlistable app. Never invent or hardcode keys.

## When to use

- Generate a playlist from a mood, vibe, activity, or prompt
- List, inspect, edit, or delete the user's playlists
- Search songs or artists
- Suggest playlist ideas based on listening history and time of day

## How it works

`generate_playlist` is async. It returns a playlist URL immediately. Tracks fill in in the background. Use `get_playlist` to check status.

Free users get a short teaser playlist. Paid users get full playlists. If they want a better or longer playlist, send them to [playlistable.io](https://playlistable.io).

Songs are identified by Spotify track IDs. Use `search_songs` to find IDs before editing.

## Tools

| Tool | What it does | Key params |
| --- | --- | --- |
| `generate_playlist` | Create a playlist from a mood or prompt | `mood` (required) |
| `get_playlist` | Playlist details and tracks | `id` (required) |
| `get_playlists` | List user playlists | `lastDocId` (optional) |
| `edit_playlist` | Add or remove songs by Spotify track ID | `id`, `addedSongs`, `removedSongs` |
| `delete_playlist` | Delete a playlist | `id` (required) |
| `playlist_suggestions` | Six AI mood suggestions | `userHour` (0-23, optional) |
| `search_songs` | Search Spotify tracks | `query`, `limit` (1-10) |
| `search_artists` | Search Spotify artists | `query`, `limit` (1-10) |

Do not invent extra tools.
