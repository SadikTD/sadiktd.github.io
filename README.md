# Sadik's Tool Hub

A personal, password-protected homepage that auto-syncs all GitHub Pages tools and external tools into one clean, searchable interface.

**Live:** [sadiktd.github.io](https://sadiktd.github.io)

---

## Features

- **Password-protected** — login screen with a 12-hour session
- **Auto-discovery** — fetches all public GitHub repos on every load, no manual updates needed
- **Smart caching** — GitHub API results cached for 30 minutes to avoid rate limits
- **Live / Repo badges** — green `● Live` badge for repos with GitHub Pages enabled, grey `Repo` badge for others
- **Pinned tools** — pin any tool to appear at the top
- **Real-time search** — filter tools by name or description instantly
- **Sort options** — Default, A–Z, or Latest Updated
- **Copy link** — copy any tool's URL in one click
- **Light / Dark mode** — toggle with preference saved across sessions
- **Fully responsive** — works on desktop and mobile
- **Keyboard shortcuts** — `/` or `Ctrl+K` to focus search, `Esc` to clear

---

## How It Works

On every page load the hub calls the GitHub API to fetch all public repos. New repos appear automatically — no editing required. Results are cached in `localStorage` for 30 minutes so the API is not called on every visit.

```
Page load
  └── Valid cache? → Serve instantly from localStorage
  └── No cache / stale → Fetch from GitHub API → Save to cache → Render
```

---

## Configuration

All settings live in the `CONFIG` block near the top of `index.html`.

### Pin tools
```js
pinned: ['repo-name'],
```

### Hide repos
```js
hidden: ['sadiktd', 'sadiktd.github.io', 'repo-to-hide'],
```

### Override name, description, or icon for a GitHub repo
```js
overrides: {
  'repo-name': {
    name: 'Display Name',
    description: 'Custom description shown on the card.',
    icon: '📊'
  }
}
```

### Add an external tool (not on GitHub Pages)
```js
external_tools: [
  {
    id:          'tool-id',
    name:        'Tool Name',
    description: 'What it does.',
    url:         'https://example.com',
    icon:        '🔧',
    pinned:      false
  }
]
```

---

## Tech Stack

- Vanilla HTML / CSS / JavaScript — zero dependencies, zero build step
- GitHub REST API v3 for repo discovery
- Web Crypto API (`SubtleCrypto`) for password hashing
- `localStorage` for session, cache, and theme preference

---

## License

Private repository. Not licensed for public use or redistribution.
