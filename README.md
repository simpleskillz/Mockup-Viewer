<p align="center">
  <strong>Drop a JSX file. Get a live, interactive React preview. No server needed.</strong>
</p>
<p align="center">
  <strong> </strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/zero-dependencies-10b981?style=flat-square" alt="Zero Dependencies"/>
  <img src="https://img.shields.io/badge/single-HTML_file-10b981?style=flat-square" alt="Single File"/>
  <img src="https://img.shields.io/badge/100%25-client_side-10b981?style=flat-square" alt="Client Side"/>
  <img src="https://img.shields.io/badge/React-18-61dafb?style=flat-square&logo=react" alt="React 18"/>
  <img src="https://img.shields.io/badge/Tailwind-CSS-38bdf8?style=flat-square&logo=tailwindcss" alt="Tailwind"/>
  <img src="https://img.shields.io/badge/license-MIT-yellow?style=flat-square" alt="MIT"/>
</p>

---

## What is this?

**Mockup Viewer** is a single HTML file that lets you preview React (JSX) components with full interactivity — directly in the browser. No Node.js, no npm, no build step, no server.

Upload a `.jsx` file → Babel transpiles it in the browser → React renders it in a sandboxed iframe → you click, hover, navigate, fill forms — everything works.

Built for designers, developers, and clients who need to **see and interact with mockups** without setting up a dev environment.

---

## Features

| Feature | Description |
|---|---|
| **Drag & Drop** | Drop a `.jsx` file or click to upload |
| **Live Preview** | Full React 18 rendering with hooks, state, events |
| **Tailwind CSS** | Built-in Tailwind support via CDN |
| **Viewport Switcher** | Desktop / Tablet / Mobile preview modes |
| **Recent Files** | Last 5 uploaded files saved in localStorage |
| **Error Handling** | Clear error overlay with transpilation details |
| **Zero Backend** | Files never leave the browser — 100% private |
| **Single File** | One `index.html` — that's the entire app |

---

## Quick Start

### Option 1 — Just open it
```bash
# Download
curl -O https://raw.githubusercontent.com/simpleskillz/mockup-viewer/main/index.html

# Open in browser
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

### Option 2 — Clone the repo
```bash
git clone https://github.com/simpleskillz/mockup-viewer.git
cd mockup-viewer
open index.html
```

### Option 3 — Host it anywhere
Upload `index.html` to any static hosting:
- GitHub Pages
- Netlify (drag & drop)
- Vercel
- Any Apache/Nginx server
- S3 bucket
- Even a USB stick

No build step. No config. It just works.

---

## How It Works

```
┌─────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│  Upload JSX  │ ──▶ │  Babel Parse  │ ──▶ │ React Render │ ──▶ │ Live Preview │
│  (drag/drop) │     │  (in-browser) │     │  (iframe)    │     │  (interact!) │
└─────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
```

1. You drop a `.jsx` file
2. [Babel Standalone](https://babeljs.io/docs/babel-standalone) transpiles JSX → JS in the browser
3. Import/export statements are stripped automatically
4. The component is rendered via `ReactDOM.createRoot` inside a sandboxed iframe
5. Tailwind CSS is loaded in the iframe from CDN
6. You interact with the component as if it were a real app

---

## Supported JSX Features

- ✅ React hooks (`useState`, `useEffect`, `useRef`, etc.)
- ✅ Multiple components in one file
- ✅ Tailwind CSS utility classes
- ✅ Google Fonts via `<style>` tags
- ✅ Inline styles
- ✅ SVG elements
- ✅ Event handlers (onClick, onChange, etc.)
- ✅ Conditional rendering
- ✅ Array mapping / lists
- ✅ Default export detection
- ❌ Multi-file imports (everything must be in one file)
- ❌ npm packages (unless loaded via CDN in the component)

---

## Example

Create a file called `counter.jsx`:

```jsx
import React, { useState } from 'react';

const Counter = () => {
  const [count, setCount] = useState(0);

  return (
    <div className="min-h-screen bg-gray-900 flex items-center justify-center">
      <div className="text-center">
        <div className="text-8xl font-bold text-white mb-8">{count}</div>
        <div className="flex gap-4">
          <button
            onClick={() => setCount(c => c - 1)}
            className="px-8 py-4 bg-red-500 text-white text-xl font-bold rounded-xl hover:bg-red-400 transition"
          >
            −
          </button>
          <button
            onClick={() => setCount(c => c + 1)}
            className="px-8 py-4 bg-emerald-500 text-white text-xl font-bold rounded-xl hover:bg-emerald-400 transition"
          >
            +
          </button>
        </div>
      </div>
    </div>
  );
};

export default Counter;
```

Drop it into Mockup Viewer → interactive counter with Tailwind styling, working immediately.

---

## Use Cases

- **UI/UX Designers** — Preview mockups without a dev environment
- **Developers** — Quick component prototyping without `create-react-app`
- **Clients** — Send a JSX file + this viewer, client sees interactive mockup
- **Recruitment** — Preview job listing page templates (this is what it was built for)
- **Workshops** — Students drop their JSX exercises and see results instantly
- **Offline** — Works without internet once loaded (CDN scripts are cached)

---

## Tech Stack

| What | How |
|---|---|
| JSX Transpilation | [Babel Standalone](https://babeljs.io/docs/babel-standalone) |
| Rendering | [React 18](https://reactjs.org/) + ReactDOM |
| Styling | [Tailwind CSS](https://tailwindcss.com/) via CDN |
| Sandboxing | iframe with `sandbox="allow-scripts allow-same-origin"` |
| State | localStorage for recent files |
| Total size | ~15 KB (+ CDN scripts loaded on demand) |

---

## Self-Hosting

Since it's a single HTML file, hosting is trivial:

**GitHub Pages:**
1. Push `index.html` to a repo
2. Settings → Pages → Deploy from main branch
3. Done — live at `https://yourusername.github.io/mockup-viewer/`

**Netlify:**
1. Drag the `index.html` file to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Done

**Any server:**
```bash
# Python
python3 -m http.server 8080

# Node
npx serve .

# PHP
php -S localhost:8080
```

---

## Privacy

Your files **never leave the browser**. There is no server, no upload endpoint, no analytics, no tracking. The JSX file is read via the FileReader API and processed entirely client-side. Recent files are stored in `localStorage` on your machine only.

---

## Contributing

PRs welcome. Some ideas:

- [ ] Built-in example mockups to try
- [ ] Dark/light theme toggle
- [ ] Export rendered preview as screenshot
- [ ] Support for `.tsx` with TypeScript
- [ ] Multiple file support (import from other uploaded files)
- [ ] Shareable links (encode small components in URL hash)

---

## License

MIT — do whatever you want with it.

---

<p align="center">
  <sub>Made with ☕ for people who just want to see their JSX without running <code>npm install</code> for 10 minutes.</sub>
</p>
