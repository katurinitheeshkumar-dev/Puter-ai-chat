# Claude AI Chat — Advanced UI with Puter.js

A modern, production-ready AI chat interface powered by **Anthropic Claude** models via [Puter.js](https://puter.com).

No API keys. No backend. No server setup. Users pay for their own usage.

![Claude AI Chat](https://img.shields.io/badge/Claude-Opus%20%7C%20Sonnet%20%7C%20Haiku-d97757?style=flat-square)
![Puter.js](https://img.shields.io/badge/Puter.js-v2-blue?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)

## Features

- **Streaming responses** — tokens appear in real time
- **Multiple Claude models** — Opus 5.5, Sonnet 5.5, Haiku 5.5, Fable 5.1, and more
- **Conversation history** — saved in localStorage, switch between chats
- **Markdown rendering** — code blocks, tables, lists, headings
- **Copy responses** with one click
- **Stop generation** mid-stream
- **Mobile responsive** with slide-out sidebar
- **Clean dark UI** inspired by modern AI chat apps
- **Suggestion chips** on the welcome screen

## Quick Start

1. Clone or download this repo
2. Open `index.html` with a local server (required by Puter.js)

```bash
# Using Python
python -m http.server 8000

# Using Node (npx)
npx serve .

# Using VS Code Live Server extension
```

3. Open `http://localhost:8000` in your browser
4. Start chatting — Puter will handle authentication (guest or account)

> **Important:** Do not open the file with `file://`. Always serve it over HTTP.

## How It Works

```html
<script src="https://js.puter.com/v2/"></script>
```

Puter.js provides free access to Claude and 500+ other models. Your users authenticate with Puter (or continue as guest) and their usage is billed to their own Puter account — you pay nothing.

```js
const response = await puter.ai.chat(messages, {
  model: 'claude-sonnet-5-5',
  stream: true
});

for await (const part of response) {
  if (part?.text) {
    // append token to UI
  }
}
```

## Available Models

| Model | ID | Best for |
|-------|-----|----------|
| Claude Opus 5.5 | `claude-opus-5-5` | Most capable, complex reasoning |
| Claude Sonnet 5.5 | `claude-sonnet-5-5` | Best balance (default) |
| Claude Haiku 5.5 | `claude-haiku-5-5` | Fast & cheap |
| Claude Fable 5.1 | `claude-fable-5-1` | Deep reasoning |
| Claude Opus 5 | `claude-opus-5` | Previous flagship |
| Claude Sonnet 5 | `claude-sonnet-5` | Previous balanced |

You can change the default model in the top-left dropdown.

## Project Structure

```
puter-claude-chat/
├── index.html      # Complete single-file app
└── README.md
```

Everything is in one HTML file — easy to host anywhere (GitHub Pages, Netlify, Vercel, Cloudflare Pages, etc.).

## Deploy

### GitHub Pages
1. Push this repo to GitHub
2. Settings → Pages → Source: Deploy from branch `main` / root
3. Done. Your chat is live.

### Netlify / Vercel
Just drag-and-drop the folder or connect the repo. Zero config needed.

## Customization

- **System prompt** — edit the system message inside `sendMessage()`
- **Default model** — change the `selected` option in the `<select>`
- **Colors** — CSS variables at the top of `<style>`
- **Suggestions** — edit the `.suggestion` buttons in the welcome screen

## License

MIT — free to use, modify, and distribute.
