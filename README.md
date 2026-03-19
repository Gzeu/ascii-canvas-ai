# ascii-canvas-ai

> **ASCII Canvas Diagram Editor** with integrated AI Assistant — a single self-contained HTML file.

## Features

### Core Editor
- **Tools**: Select/Move, Rectangle, Diamond, Line, Arrow, Text, Freehand, Eraser
- **Border styles**: Simple, Double, Rounded, Heavy, Light
- **Arrow heads**: arrow (`>`), triangle (`▶`)
- **Line styles**: ASCII (`-`, `|`), Light (`─`, `│`), Heavy (`━`, `┃`), Dashed, Dotted
- **Diamond styles**: Simple (`/`, `\`), Unicode (`◇`)
- **Freehand characters**: `*`, `#`, `+`, `.`, `x`, `o`, `~`
- **Eraser sizes**: 1×1, 3×3, 5×5
- Undo/Redo (`Ctrl+Z` / `Ctrl+Y`), Clear canvas
- Copy ASCII to clipboard (`Ctrl+Shift+C`)
- Zoom (scroll wheel toward mouse), Pan (Space+drag or middle mouse)
- Grid background, status bar (cursor, canvas size, zoom, tool, hint)
- Keyboard shortcuts: `V`, `R`, `D`, `L`, `A`, `T`, `F`, `E`
- Flood-fill connected shape selection + drag to move
- Dark theme with JetBrains Mono font

### AI Assistant Panel
- Right-side collapsible panel (280px, resizable 200–500px)
- OpenAI-compatible API (configurable endpoint + key stored in localStorage)
- Model presets: Claude Sonnet/Opus, GPT-4o, Gemini Flash, Mistral Large, DeepSeek, Llama 3.3
- Chat interface with message history
- **Apply to Canvas** / **Apply at Cursor** / **Append** buttons per AI message
- 8 quick-prompt chips: Flowchart, System Architecture, Sequence Diagram, Tree Structure, Network Topology, Timeline, Table, State Machine
- AbortController for request cancellation
- Error bubbles with red border on API failures

## Usage

1. Download `index.html`
2. Open in any modern browser — no server needed
3. Configure AI: click **✦ AI** in the topbar → enter your OpenRouter (or OpenAI) API key
4. Draw diagrams manually or ask the AI to generate them

## Recommended API

Use [OpenRouter](https://openrouter.ai) as the API endpoint (`https://openrouter.ai/api/v1`). Some models are free.

**Best models for ASCII diagrams:**
- `anthropic/claude-sonnet-4-5` — best structured ASCII art
- `openai/gpt-4o` — great for complex diagrams
- `google/gemini-2.0-flash-001` — fast and cheap for iteration

## Build Prompt

See [`PROMPT.md`](./PROMPT.md) for the full AI generation prompt used to build this tool.

## Layout

```
[Left Panel 200px] [Canvas flex-1] [AI Panel 280px collapsible]
```

## License

MIT
