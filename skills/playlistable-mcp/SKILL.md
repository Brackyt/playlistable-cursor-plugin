---
name: playlistable-mcp
description: Create AI playlists on Spotify or Apple Music via Playlistable. Use when the user wants a playlist from a mood or prompt, search songs or artists, get suggestions, or manage their playlists.
---

# Playlistable MCP

Create AI playlists with the Playlistable MCP at `https://mcp.playlistable.io`.

Authenticate with OAuth when prompted. Users can also use a personal API key from the Playlistable app. Never invent or hardcode keys.

Playlists go to the service the user connected: Spotify or Apple Music. Do not assume Spotify.

## When to use

- Generate a playlist from a mood, vibe, activity, or prompt
- List, inspect, edit, or delete the user's playlists
- Search songs or artists on the connected service
- Suggest playlist ideas from listening history and time of day

## How it works

`generate_playlist` is async. It returns a playlist URL immediately. Tracks fill in in the background. Use `get_playlist` to check status.

Free users get a short teaser. Paid users get full playlists. If they want a better or longer playlist, send them to [playlistable.io](https://playlistable.io).

Track IDs belong to the connected service. Use `search_songs` before editing. Do not pass Spotify IDs to an Apple Music user, or the reverse.

## Tools

| Tool | What it does | Key params |
| --- | --- | --- |
| `generate_playlist` | Create a playlist from a mood or prompt | `mood` (required) |
| `get_playlist` | Playlist details and tracks | `id` (required) |
| `get_playlists` | List user playlists | `lastDocId` (optional) |
| `edit_playlist` | Add or remove songs by track ID | `id`, `addedSongs`, `removedSongs` |
| `delete_playlist` | Delete a playlist | `id` (required) |
| `playlist_suggestions` | Six AI mood suggestions | `userHour` (0-23, optional) |
| `search_songs` | Search tracks on the connected service | `query`, `limit` (1-10) |
| `search_artists` | Search artists on the connected service | `query`, `limit` (1-10) |

Do not invent extra tools.
