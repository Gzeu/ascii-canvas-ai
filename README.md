# ASCII Canvas AI - Diagram Editor with AI Assistant

> **Professional ASCII Canvas Diagram Editor** with integrated AI Assistant — a single self-contained HTML file.

![ASCII Canvas AI](https://img.shields.io/badge/Version-1.0.0-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Browser](https://img.shields.io/badge/Browser-Modern-orange.svg)

## ✨ Features

### 🎨 Core Editor
- **Drawing Tools**: Select/Move, Rectangle, Diamond, Line, Arrow, Text, Freehand, Eraser
- **Border Styles**: Simple, Double, Rounded, Heavy, Light
- **Arrow Heads**: Arrow (`>`), Triangle (`▶`)
- **Line Styles**: ASCII (`-`, `|`), Light (`─`, `│`), Heavy (`━`, `┃`), Dashed, Dotted
- **Diamond Styles**: Simple (`/`, `\`), Unicode (`◇`)
- **Freehand Characters**: `*`, `#`, `+`, `.`, `x`, `o`, `~`
- **Eraser Sizes**: 1×1, 3×3, 5×5
- **Canvas Operations**: Undo/Redo (`Ctrl+Z` / `Ctrl+Y`), Clear canvas (`Delete`)
- **Clipboard**: Copy ASCII to clipboard (`Ctrl+Shift+C`)
- **Navigation**: Zoom (scroll wheel toward mouse), Pan (Space+drag or middle mouse)
- **Visual**: Grid background, status bar (cursor, canvas size, zoom, tool, hint)
- **Keyboard Shortcuts**: `V`, `R`, `D`, `L`, `A`, `T`, `F`, `E`
- **Selection**: Flood-fill connected shape selection + drag to move
- **Theme**: Dark theme with JetBrains Mono font

### 🤖 AI Assistant Panel
- **Panel Design**: Right-side collapsible panel (280px, resizable 200–500px)
- **API Integration**: OpenAI-compatible API with configurable endpoint + key
- **Model Support**: 
  - Claude Sonnet/Opus 4.5
  - GPT-4o
  - Gemini 2.0 Flash
  - Mistral Large
  - DeepSeek Chat
  - Llama 3.3 70B
  - Custom models
- **Chat Interface**: Full message history with syntax highlighting
- **Quick Actions**: Apply to Canvas / Apply at Cursor / Append buttons per AI message
- **Quick Prompts**: 8 pre-defined chips for common diagram types
- **Error Handling**: Graceful error bubbles with request cancellation
- **Persistence**: API configuration stored in localStorage

## 🚀 Quick Start

1. **Download** the `index.html` file
2. **Open** in any modern browser — no server required
3. **Configure AI**: Click **✦ AI** in the topbar → enter your API key
4. **Create**: Draw diagrams manually or ask the AI to generate them

## 🔧 Recommended API

Use [OpenRouter](https://openrouter.ai) as the API endpoint (`https://openrouter.ai/api/v1`). Some models are free!

**Best models for ASCII diagrams:**
- `anthropic/claude-sonnet-4-5` — Best structured ASCII art
- `openai/gpt-4o` — Great for complex diagrams
- `google/gemini-2.0-flash-001` — Fast and cheap for iteration

## 📋 Quick Prompts

The AI assistant includes 8 quick prompt chips:
- **Flowchart** - Process and workflow diagrams
- **System Architecture** - Software and hardware architecture
- **Sequence Diagram** - Interaction sequences
- **Tree Structure** - Hierarchical data structures
- **Network Topology** - Network layouts and connections
- **Timeline** - Sequential events and milestones
- **Table** - Tabular data layouts
- **State Machine** - State transition diagrams

## 🎯 Usage Examples

### Manual Drawing
1. Select a tool from the left panel
2. Click and drag on the canvas
3. Use keyboard shortcuts for faster workflow

### AI-Assisted Creation
1. Open the AI panel (click ✦ AI)
2. Type a prompt like "Create a flowchart for user registration"
3. Click "Apply to Canvas" to place the generated diagram

### Applying AI Output
- **Apply to Canvas**: Places diagram at position (0,0)
- **Apply at Cursor**: Places at current mouse position
- **Append**: Adds below existing content

## ⌨️ Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `V` | Select/Move tool |
| `R` | Rectangle tool |
| `D` | Diamond tool |
| `L` | Line tool |
| `A` | Arrow tool |
| `T` | Text tool |
| `F` | Freehand tool |
| `E` | Eraser tool |
| `Ctrl+Z` | Undo |
| `Ctrl+Y` | Redo |
| `Ctrl+Shift+C` | Copy to clipboard |
| `Delete` | Clear canvas |
| `Space+Drag` | Pan canvas |
| `Scroll` | Zoom in/out |

## 🏗️ Technical Architecture

### Layout Structure
```
[Left Panel 200px] [Canvas flex-1] [AI Panel 280px collapsible]
```

### Core Technologies
- **Frontend**: Pure HTML5, CSS3, Vanilla JavaScript
- **Canvas**: HTML5 Canvas API for rendering
- **AI Integration**: OpenAI-compatible API via fetch()
- **Storage**: localStorage for configuration persistence
- **No Dependencies**: Single self-contained file

### Canvas Grid
- **Size**: 200 columns × 80 rows
- **Font**: JetBrains Mono (12px)
- **Rendering**: Canvas-based with pixel-perfect alignment
- **Zoom**: 0.5× to 3× with smooth transitions

## 🎨 Design System

### Color Palette
- **Primary**: `#0a0a0a` (deep black)
- **Surface**: `#1a1a1a` (dark gray)
- **Surface 2**: `#252525` (medium gray)
- **Border**: `#333` (subtle gray)
- **Accent**: `#4f98a3` (teal blue)
- **Text**: `#e0e0e0` (light gray)

### Typography
- **Font Family**: JetBrains Mono, monospace
- **Sizes**: 10px-14px for UI, 12px for canvas
- **Weight**: 400-600 for hierarchy

## 🔒 Security & Privacy

- **Local Processing**: All drawing operations happen locally
- **API Keys**: Stored only in browser localStorage
- **No Tracking**: No analytics or telemetry
- **Offline Capable**: Core editor works without internet

## 🌐 Browser Compatibility

- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

## 📝 Development

### Build Process
No build process required! The project is a single HTML file.

### File Structure
```
ascii-canvas-ai/
├── index.html          # Main application
├── README.md           # Documentation
├── PROMPT.md           # AI build prompt
└── .gitignore         # Git ignore rules
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

MIT License - see [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **OpenRouter** for providing AI model access
- **JetBrains** for the excellent Mono font
- **ASCII Art Community** for inspiration and techniques

## 📞 Support

- 🐛 **Bug Reports**: [Open an Issue](https://github.com/Gzeu/ascii-canvas-ai/issues)
- 💡 **Feature Requests**: [Open an Issue](https://github.com/Gzeu/ascii-canvas-ai/issues)
- 📧 **Questions**: Use GitHub Discussions

---

**Made with ❤️ for the ASCII art and diagram community**
