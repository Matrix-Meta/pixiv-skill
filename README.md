# Pixiv Skill for OpenClaw

A powerful Pixiv integration for OpenClaw, allowing you to search illustrations, view rankings, browse user profiles, and download content (including images, manga, and ugoira/animations) directly from your agent interface.

## Features

- **Search**: Search for illustrations by keyword.
- **Rankings**: View daily, weekly, and monthly rankings (including R-18 if account allows).
- **User Profiles**: View public user profiles and stats.
- **My Profile**: View your own logged-in profile.
- **Feed**: View the latest works from users you follow.
- **Following**: List users you are following.
- **Download**: Download single illustrations, manga series, and ugoira (automatically converted to GIF).

## Installation

1. Copy this folder to your OpenClaw skills directory.
2. Install dependencies:
   ```bash
   npm install
   ```

## Configuration

1. Create a `config.json` file in the root of the skill directory (see `config.example.json` if available, or just use the structure below).
2. You need a **Pixiv Refresh Token**. 
   - To get one, we recommend using a tool like `pixivpy`'s login script or inspecting network traffic from a browser login (though OAuth token is preferred).

**config.json**:
```json
{
  "refresh_token": "YOUR_PIXIV_REFRESH_TOKEN"
}
```

Alternatively, you can set the token via the CLI:
```bash
node scripts/pixiv-cli.js login <REFRESH_TOKEN>
```

## Usage

This skill is designed to be used by the OpenClaw agent, but you can also use the CLI directly.

### CLI Commands

- **Search**: `node scripts/pixiv-cli.js search "keyword" [page]`
- **Ranking**: `node scripts/pixiv-cli.js ranking [mode] [page]`
  - Modes: `day`, `week`, `month`, `day_male`, `day_female`, `week_original`, `week_rookie`, `day_ai`
- **User Profile**: `node scripts/pixiv-cli.js user <user_id>`
- **My Profile**: `node scripts/pixiv-cli.js me`
- **Feed**: `node scripts/pixiv-cli.js feed [all/public/private] [page]`
- **Following**: `node scripts/pixiv-cli.js following [page]`
- **Download**: `node scripts/pixiv-cli.js download <illust_id>`
  - Downloads are saved to `downloads/<illust_id>/`.
  - Ugoira (animations) are automatically converted to .gif.

## Dependencies

- `@ibaraki-douji/pixivts`: Unofficial Pixiv API client.
- `axios`: For downloading files.
- `adm-zip`: For extracting Ugoira zip files.
- `gif-encoder-2`, `pngjs`, `jpeg-js`: For converting Ugoira frames to GIF.

## Disclaimer

This project is an unofficial tool and is not affiliated with Pixiv Inc. Please respect Pixiv's Terms of Service when using this tool.
