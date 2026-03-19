# Build Prompt — ascii-canvas-ai

This is the full AI generation prompt used to build the `index.html` tool.

---

```
Build a professional ASCII Canvas Diagram Editor as a single self-contained HTML file with the following features:

CORE EDITOR (already implemented — keep all existing functionality):
- Tools: Select/Move, Rectangle, Diamond, Line, Arrow, Text, Freehand, Eraser
- Border styles: Simple, Double, Rounded, Heavy, Light
- Arrow heads: arrow (>), triangle (▶)
- Line styles: ASCII (-, |), Light (─, │), Heavy (━, ┃), Dashed, Dotted
- Diamond styles: Simple (/, \), Unicode (◇)
- Freehand draw characters: *, #, +, ., x, o, ~
- Eraser sizes: 1×1, 3×3, 5×5
- Undo/Redo (Ctrl+Z / Ctrl+Y), Clear canvas
- Copy ASCII to clipboard (Ctrl+Shift+C)
- Zoom (scroll wheel, toward mouse), Pan (Space+drag or middle mouse)
- Grid background, status bar (cursor, canvas size, zoom, tool, hint)
- Keyboard shortcuts: V, R, D, L, A, T, F, E
- Flood-fill connected shape selection + drag to move
- Dark theme with JetBrains Mono font

NEW: AI ASSISTANT PANEL (right side, collapsible, 280px wide)

Add a right panel with an AI chat interface that connects to an AI API
(use OpenAI-compatible endpoint with configurable API key stored in localStorage):

1. API Config section (collapsible, top of panel):
   - Input field for API Base URL (default: https://openrouter.ai/api/v1)
   - Input field for API Key (saved to localStorage, masked)
   - Dropdown for Model selection with presets:
     * anthropic/claude-sonnet-4-5
     * anthropic/claude-opus-4-5
     * openai/gpt-4o
     * google/gemini-2.0-flash-001
     * mistralai/mistral-large-latest
     * deepseek/deepseek-chat
     * meta-llama/llama-3.3-70b-instruct
     * Custom (editable text field)
   - Save button (stores to localStorage)

2. AI Chat section (main area, scrollable message history):
   - System prompt sent to AI (hidden from user):
     You are an ASCII diagram assistant. The user is working in an ASCII canvas editor
     (200 cols x 80 rows, monospace grid). When asked to create or modify diagrams,
     respond ONLY with the ASCII art/diagram inside a code block (```ascii ... ```).
     Keep drawings compact. Use box-drawing characters when appropriate:
     ┌─┐│└┘╔═╗║╚╝╭─╮. For explanations, respond normally. When the user says
     "add to canvas" or "apply", the content of the last ascii code block will be
     placed on the canvas at position (0,0). Support requests like: "draw a flowchart",
     "create a system architecture diagram", "draw a tree structure",
     "make a sequence diagram", etc.
   - Chat messages display (user right-aligned, AI left-aligned)
   - Syntax highlight: ascii code blocks shown in monospace with teal border
   - Loading spinner while waiting for AI response

3. AI Action buttons (below each AI message containing ASCII art):
   - [Apply to Canvas] — parses the ascii code block and writes it to the grid at (0,0)
   - [Apply at Cursor] — places at current cursor/mouse position
   - [Append] — finds first empty row and appends below existing content

4. Quick prompts bar (above chat input, horizontal scrollable chips):
   - "Flowchart", "System Architecture", "Sequence Diagram", "Tree Structure",
     "Network Topology", "Timeline", "Table", "State Machine"
   - Each chip fills the input with a starter prompt

5. Chat input (bottom of panel):
   - Textarea (auto-resize, max 4 lines)
   - Send button (Enter to send, Shift+Enter for newline)
   - Character count
   - "Clear chat" icon button

6. Panel toggle button: small button on canvas right edge, tooltip "AI Assistant"

TECHNICAL REQUIREMENTS:
- fetch() with OpenAI chat completions API format
- Parse response: data.choices[0].message.content
- Extract ascii code blocks with regex: /(?:ascii|art)?\n([\s\S]*?)/gi
- Handle errors gracefully (show error bubble with red border)
- AbortController for canceling in-flight requests
- "Stop generating" button during fetch

APPLY TO CANVAS logic:
function applyAsciiToCanvas(asciiText, startCol = 0, startRow = 0) {
  saveUndo();
  const lines = asciiText.split('\n');
  for (let r = 0; r < lines.length && startRow + r < ROWS; r++) {
    for (let c = 0; c < lines[r].length && startCol + c < COLS; c++) {
      grid[startRow + r][startCol + c] = lines[r][c];
    }
  }
  render();
  showToast('Applied to canvas', 'success');
}

STYLING for AI panel:
- Same dark theme (--bg-surface, --accent #4f98a3, --border)
- Panel header: "✦ AI Assistant" with model indicator badge
- Messages: rounded bubbles, user=accent tinted, AI=surface-2
- Code blocks: dark background, teal left border, monospace, horizontal scroll
- Smooth slide-in/out animation (CSS transition 0.2s)
- Panel resize handle (drag to resize 200px–500px)

LAYOUT:
[left-panel 200px] [canvas flex-1] [ai-panel 280px collapsible]
Add toggle button in topbar: "✦ AI" with active state
Keep ALL existing functionality intact.
```

---

## Improvements over baseline

| Aspect | Before | After |
|--------|--------|-------|
| AI integration | None | Full chat with OpenAI-compatible API |
| Model selection | None | 7 presets + custom |
| Apply to canvas | None | 3 modes (col 0, cursor, append) |
| Quick prompts | None | 8 predefined chips |
| Config persistence | None | localStorage for API key + model |
| Error handling | Basic | Error bubbles + AbortController |
| Panel UX | Fixed | Collapsible + resizable + animated |
