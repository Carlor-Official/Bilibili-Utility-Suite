Current release: **1.6.23**, compatible with MoeCard NT 3.2.2. Runtime status now handles invisible nicknames and reports the plugin's current environment or container metrics. Each platform package supports framework IPC import and standalone forward/reverse WebSocket connections.

Download one of three packages for Windows x86_64, Linux x86_64, or Linux ARM64. IPC import requires framework 3.1.3+. The archive has `mengka-plugin.json` at its root and can also be extracted for standalone use. See [1.6.23 release notes](release-notes-1.6.23.md). Back up existing data before upgrading.

<div align="center">
  <img src="bilibili-suite-cover.png" width="100%" alt="B站综合插件" />

  <p>
    <a href="https://github.com/CarlorOfficial/Bilibili-Utility-Suite/releases/latest"><img src="https://img.shields.io/badge/download-GitHub%20Releases-6C5CE7?style=flat-square" alt="GitHub Releases" /></a>
    <img src="https://img.shields.io/badge/platform-Windows%20%7C%20Linux-2684FF?style=flat-square" alt="Windows and Linux" />
    <img src="https://img.shields.io/badge/architecture-x86__64%20%7C%20ARM64-00A884?style=flat-square" alt="x86_64 and ARM64" />
  </p>

  <p><strong>B站综合插件</strong></p>
  <p>Bilibili Utility Suite</p>
  <p>A cross-platform Bilibili feature suite for MoeCard NT</p>
  <p><a href="README.md">简体中文</a> · <a href="https://github.com/CarlorOfficial/Bilibili-Utility-Suite/releases/latest">Download</a> · <a href="https://github.com/CarlorOfficial/Bilibili-Utility-Suite/issues">Issues</a></p>
</div>

---

## Overview

B站综合插件 (Bilibili Utility Suite) connects to MoeCard NT through native IPC and provides Bilibili queries, subscriptions, link parsing, notifications, and locally rendered image cards for group and private chats. Standalone deployments can still use forward or reverse WebSocket.

Windows and Linux share the same browser-based administration UI. The plugin sends plain text and image messages only and does not depend on Markdown support.

> This repository is the official release and documentation channel. It does not publish the plugin's core source code, and a valid authorization is required to use plugin features.

## Highlights

- Dynamic, live, guard, gift, live-event, bangumi, decoration, and collection notifications
- User, live room, latest dynamic, latest video, decoration, and fan medal queries
- Bilibili user, live room, dynamic, video, and workshop link parsing
- Plain-text and locally rendered image-card modes
- Independent Bilibili QR login, authorization, credentials, subscriptions, and data for every QQ account
- Bark notifications for iOS
- Per-bot and per-group WebUI configuration, 18 customizable message templates, runtime logs, and signed online updates

Send `哔哩菜单` in chat to open the command menu.

## Supported Platforms

| Platform | Package | Requirements |
| --- | --- | --- |
| Windows x64 | `BilibiliSuite-1.6.23-windows-x86_64.zip` | IPC import: MoeCard NT 3.1.3+; standalone: extract and run |
| Linux x86_64 / amd64 | `BilibiliSuite-1.6.23-linux-x86_64.tar.gz` | IPC import: MoeCard NT 3.1.3+ Docker runtime; standalone: glibc 2.39+ |
| Linux ARM64 | `BilibiliSuite-1.6.23-linux-arm64.tar.gz` | IPC import: MoeCard NT 3.1.3+ Docker runtime; standalone: glibc 2.39+ |

Each archive contains the same executable for IPC and both WS modes on its platform. Windows and Linux binaries are not interchangeable. Standalone Linux requires Ubuntu 24.04, Debian 13, or another system with glibc 2.39 or later; IPC uses the container runtime supplied by the framework.

## Quick Start

1. Download the package for the server OS and architecture from [GitHub Releases](https://github.com/CarlorOfficial/Bilibili-Utility-Suite/releases/latest).
2. In MoeCard NT, open **Plugins → Plugin Import**, upload the package, review its requested capabilities, and confirm the import.
3. Open the plugin administration page from MoeCard NT. Native IPC is connected automatically and does not require a WebSocket port or token.
4. Add plugin-owner QQ numbers, verify each bot's authorization status, and configure features per bot and group.
5. Use the account page or send `扫码登录账号` in chat to complete an independent Bilibili QR login before using queries and subscriptions.

For standalone deployment, extract the same archive, run `BilibiliSuite.exe` on Windows or use `install.sh` on Linux, complete the WebUI initialization, and select forward or reverse WebSocket in the plugin settings. There is no separate WS download.

## Custom Message Templates

The WebUI provides 18 templates for live notifications and summaries, live events, dynamics and videos, bangumi updates, profile and live-room queries, decorations, and collections. Each bot has an independent global template set, while individual groups may override it. Variables are validated against a per-template allowlist, image variables remain real image messages, and no Markdown is generated.

## Isolation and Reliability

- Every bot QQ has independent authorization, heartbeat, storage, credentials, and subscriptions.
- An unauthorized QQ is disabled independently and never shuts down the whole process.
- One bot's authorization or data cannot be reused by another bot.
- Temporary authorization-service instability does not stop the plugin after a single failed heartbeat.
- WebUI logs redact tokens, cookies, and common sensitive values.

## Signed Updates

Standalone deployments can check the latest GitHub Release in the WebUI. Native IPC installations are upgraded from MoeCard NT's plugin management page. Platform-specific packages and their `.sig` files are published together.

## Security Notice

Release packages contain signed binaries, runtime libraries, and documentation only. They do not include core plugin source code, signing keys, user configuration, or business data. Keep `config.json`, `web-admin.json`, `admin.token`, and plugin data directories private.

## Support

- Downloads and changelog: [Releases](https://github.com/CarlorOfficial/Bilibili-Utility-Suite/releases)
- Bug reports and suggestions: [Issues](https://github.com/CarlorOfficial/Bilibili-Utility-Suite/issues)

No open-source license is currently granted for the plugin's core implementation. Download official packages only from this repository's Releases page.
