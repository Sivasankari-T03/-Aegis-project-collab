# AEGIS — Conversational AI with 3D Motion

**AEGIS** (neural · spatial · reactive) is an interactive conversational AI engine that answers questions about Artificial Intelligence algorithms and **visualizes them in real-time 3D**.

Ask about search algorithms, CSPs, game theory, machine learning, or try the built-in demos — a glowing agent flies a path that maps how the algorithm executes, while a step-by-step breakdown stays in sync with the flight.

![AEGIS Demo](https://img.shields.io/badge/Three.js-r128-blue) ![Gemini API](https://img.shields.io/badge/Gemini-API-teal) ![Tailwind CSS](https://img.shields.io/badge/Tailwind-CSS-38bdf8)

---

## ✨ Features

- **Conversational AI** powered by Google Gemini (with robust model fallback + offline fallback plan)
- **3D Algorithm Visualization** using Three.js
  - Dynamic agent with gyro rings, satellites, and rainbow comet trail
  - Topic-aware scenes: Maze (Pac-Man style), Grid (Sudoku), Spiral, Wave, Orbit, Radial
  - Numbered decision waypoints with hover tooltips explaining *why* each move was chosen
  - Phase-colored ground ribbon that highlights the current algorithm step
- **Ghost Chase Mode** — when you ask about Pac-Man / pursuit, a red ghost flies its own intercept path and shows its predicted next cell
- **Cinematic Controls**
  - Orbit / Follow camera
  - Flight speed slider (0.25× – 3×)
  - Auto-rotate toggle
- **Step-by-step execution** synced with the agent’s progress
- **Voice input** (Web Speech API)
- **Live Demo** mode — works without an API key
- Beautiful dark glass UI with Tailwind CSS

---

## 🚀 Quick Start

### Option 1 — Live Demo (no setup)

1. Open the page in a browser.
2. Click **⚡ Live Demo**.
3. Watch the agent fly a Lissajous curve.

### Option 2 — Full AI Mode

1. Get a free API key from [Google AI Studio](https://aistudio.google.com/apikey).
2. Paste it into the **Gemini API Key** field (the key never leaves your browser).
3. Type a question or click a preset:
   - 🍒 Pac-Man
   - 🧩 Sudoku
   - 🌀 Spiral
4. Hit **Ask AI Engine**.

> **Tip:** For best results when running locally, serve the file over HTTP (e.g. `npx serve` or the bundled proxy server) so the optional local proxy can avoid CORS issues.

---

## 🧠 How It Works

1. You ask a question (or use a preset / voice).
2. AEGIS sends a carefully crafted system prompt + your query to Gemini.
3. The model returns strict JSON containing:
   - Algorithm name & syllabus unit
   - Natural-language explanation
   - Motion reason (why this 3D path shape)
   - Pseudocode
   - Visual style
   - 3D path waypoints
   - Step-by-step phases
   - (Optional) Ghost chase data for Pac-Man style queries
4. The frontend builds a Catmull-Rom spline, lays out the matching 3D scene, and flies the agent while highlighting steps in real time.

If the model reply is malformed, an **offline fallback planner** still generates a coherent visualization so the experience never breaks.

---

## 📚 Syllabus Coverage

AEGIS is tuned for a standard AI course syllabus:

| Unit | Topics |
|------|--------|
| I | History of AI, Intelligent Agents, Uninformed Search (BFS, DFS, UCS…) |
| II | Informed Search (A*, Greedy), Local Search, Optimization |
| III | Game Playing (Minimax, Alpha-Beta, MCTS), CSPs & Backtracking |
| IV | Propositional & First-Order Logic, Inference |
| V | Machine Learning, Generative AI, Real-world applications |

---

## 🛠 Tech Stack

- **Frontend**: HTML5, Tailwind CSS, Vanilla JS
- **3D**: Three.js r128 + OrbitControls
- **AI**: Google Gemini API (`gemini-2.5-flash` → fallback chain)
- **Extras**: Web Speech API (voice), Canvas sprites for waypoint labels

---

## 📁 Project Structure
├── aegis.html          # Single-file application (everything is self-contained)
└── README.md

The entire experience lives in one HTML file — no build step required.

---

## 🎮 Controls

| Action              | How |
|---------------------|-----|
| Orbit camera        | Drag |
| Zoom                | Scroll |
| Reset view          | ⌂ Reset button |
| Auto-rotate         | ⟳ Orbit button |
| Chase camera        | 🎥 Follow button |
| Change flight speed | ⏩ Slider |
| Hover waypoint      | See why the agent chose that move |
| Voice input         | 🎙 microphone button |

---

## 📝 Example Queries

- “Pac-Man maze: a ghost chases Pac-Man and predicts its next move”
- “Sudoku backtracking solver scanning the 9×9 grid”
- “Explain A* search with an example path”
- “How does Minimax with Alpha-Beta pruning work?”
- “Spiral matrix traversal”
- “BFS vs DFS — which is better for maze solving?”

---

## ⚠️ Notes

- API key is stored only in the browser (it lives in the input field for the session only).
- When opened as `file://`, the optional local proxy is unavailable — use the Live Demo or serve the page over HTTP.
- The offline fallback guarantees a visualization even if the model returns unusable JSON.

---

## 📜 License

MIT License — feel free to use, modify, and share.

---

**AEGIS v2.0** · Three.js r128 · Gemini API  
*Drag to orbit · Scroll to zoom · Hover numbered waypoints for the “why” · 🎥 Follow-cam · ⏩ Speed*
