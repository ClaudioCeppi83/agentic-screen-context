# agentic-screen-context 🖥️⚡

> Zero-latency screen visual context parser and local code enricher for AI agents.

Capture your active window or screen, extract visible errors and code signatures via OCR or Vision, correlate them with your local repository codebase, and inject a rich Markdown context payload directly into your clipboard.

![agentic-screen demo](docs/demo.gif)

---

## ⚡ Quick Start

Execute instantly via `npx` inside your project root:

```bash
npx agentic-screen-context
```

Or install globally:

```bash
npm install -g agentic-screen-context
agentic-screen
```

### Options

```bash
agentic-screen [options]

Options:
  -c, --copy          Copy output to clipboard (default: true)
  -o, --out <path>    Save output markdown to specified file path
  --api-key <key>     Gemini API key for multimodal extraction
  -d, --dry-run       Run extraction pipeline without writing to clipboard
  -h, --help          Display help and flags
```

---

## 🚀 How It Works (Pipeline Pattern)

1. **Native Screen Capture:** Cross-platform native capture without heavy dependencies (macOS `screencapture`, Linux `grim`/`maim`, Windows PowerShell `GetForegroundWindow`).
2. **Visual Context Parser:** Offline OCR powered by `tesseract.js` WASM, with optional ultra-fast multimodal parsing via `gemini-1.5-flash` when `GEMINI_API_KEY` is provided.
3. **Local Code Enricher:** Fast fuzzy search (`fuzzysort`) matches detected signatures or errors to local project files, pulling in relevant imports and surrounding lines (+/- 15 lines).
4. **Markdown Payload Formatter:** Structures context into a prompt-ready markdown block copied straight into your clipboard.

---

## 🛠️ Supported Operating Systems

| OS | Capture Utility | Fallback |
| :--- | :--- | :--- |
| **Linux (Wayland)** | `grim` | Clipboard buffer fallback |
| **Linux (X11)** | `maim` / `xdotool` | Whole screen capture / Clipboard fallback |
| **macOS** | `/usr/sbin/screencapture` | Active display capture |
| **Windows** | PowerShell (`System.Drawing`) | Clipboard buffer fallback |

---

## 🧪 Development & Testing

```bash
# Run unit & integration tests
npm test

# Build TypeScript
npm run build
```

---

## 📄 License

MIT © [Claudio Ceppi](https://github.com/ClaudioCeppi83)
