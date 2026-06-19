# Charlie — AI Coding Assistant Interface

> A production-ready React + TypeScript frontend for AI-powered chat and coding assistance. Drop in your API key and ship in hours, not weeks.

![License](https://img.shields.io/badge/license-MIT-blue.svg) ![Language](https://img.shields.io/badge/language-TypeScript-3178c6.svg) ![Framework](https://img.shields.io/badge/framework-React-61dafb.svg) ![UI](https://img.shields.io/badge/ui-shadcn%2Fui-000000.svg) ![Status](https://img.shields.io/badge/status-active-brightgreen.svg)

---

## Overview

**Charlie** is a fully scaffolded AI assistant interface built with React, TypeScript, and the complete [shadcn/ui](https://ui.shadcn.com/) component library. It ships with a real-time WebSocket layer, an embedded code editor, file upload support, and a collapsible sidebar — everything you need to build a production AI product without touching a single UI component from scratch.

Most developers spend 40–80 hours building exactly this kind of interface before they can even test their AI integration. Charlie eliminates that entirely. Connect your preferred AI provider (OpenAI, Anthropic Claude, Mistral, or any OpenAI-compatible endpoint), configure your environment variables, and you have a live, polished AI coding assistant.

Whether you're building an internal developer tool, a white-label SaaS product, or an AI-powered customer support agent, Charlie gives you the complete frontend foundation — battle-tested, accessible, and ready to brand.

---

## Key Features

- **Real-Time Chat Interface** — Full conversational UI with message history, streaming support via WebSocket, and a clean message threading layout
- **Integrated Code Editor** — Embedded code editor component for syntax-highlighted code display and editing directly inside the chat flow
- **File Upload Support** — Drag-and-drop and click-to-upload file handling, enabling document-aware AI workflows
- **Sidebar Navigation** — Collapsible sidebar for conversation history, session management, or navigation — fully wired and responsive
- **WebSocket Connectivity** — Custom `useWebSocket` hook for real-time, low-latency communication with your backend or AI streaming endpoint
- **Complete shadcn/ui Component Suite** — All 40+ shadcn/ui components pre-installed: dialogs, sheets, drawers, carousels, charts, command palettes, and more — ready to use immediately
- **Error Boundary Protection** — Production-grade error isolation so one failing component never crashes the entire interface
- **Mobile-Responsive** — `use-mobile` hook and responsive layout baked in from the start
- **TypeScript Throughout** — Fully typed codebase for safer refactoring, better IDE support, and fewer runtime surprises
- **Replit-Ready** — Preconfigured `.replit` file means zero-friction deployment and live previews out of the box

---

## How It Works

Charlie is structured as a standard Vite + React client application (`client/`) designed to communicate with a backend server over HTTP and WebSocket.

```
User Browser
    │
    ▼
 React Frontend (client/)
    ├── ChatInterface.tsx      ← Main conversation UI
    ├── CodeEditor.tsx         ← Inline code editing/display
    ├── FileUpload.tsx         ← File attachment handler
    ├── Sidebar.tsx            ← Navigation & session list
    └── hooks/useWebSocket.ts  ← Real-time WS connection
    │
    ▼
 Backend Server (your endpoint)
    ├── REST API routes        ← Message handling, file processing
    ├── WebSocket handler      ← Streaming AI responses
    └── AI Provider SDK        ← OpenAI / Anthropic / etc.
```

The `useWebSocket` hook manages connection lifecycle, reconnection logic, and message dispatch. The `ChatInterface` component owns conversation state and renders the message thread. The `CodeEditor` and `FileUpload` components integrate directly into the chat flow, enabling a true coding assistant experience rather than a simple chatbot.

---

## Installation & Setup

### Prerequisites

- Node.js 18+
- npm or yarn
- An AI provider API key (OpenAI, Anthropic, etc.)

### 1. Clone the Repository

```bash
git clone https://github.com/Dessiidoo/Charlieold.git
cd Charlieold
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment Variables

Copy the example environment file and fill in your values:

```bash
cp .env.example .env
```

Edit `.env`:

```env
# AI Provider Configuration
OPENAI_API_KEY=sk-your-openai-key-here
# OR
ANTHROPIC_API_KEY=your-anthropic-key-here

# Backend Server
VITE_API_BASE_URL=http://localhost:3000
VITE_WS_URL=ws://localhost:3000/ws

# Optional
VITE_APP_NAME=Charlie
VITE_APP_VERSION=1.0.0
```

### 4. Start the Development Server

```bash
npm run dev
```

The client will start at `http://localhost:5173` (or the Replit preview URL if running on Replit).

### 5. Deploy on Replit

This project includes a pre-configured `.replit` file. Simply fork the Repl, add your environment secrets via the Replit Secrets panel, and click **Run**.

---

## Usage

### Basic Chat

Once running, open the interface in your browser. Type a message in the input field and press Enter or click Send. Responses stream in real time via the WebSocket connection.

### Code Editor

When the AI returns a code block, it renders inside the integrated `CodeEditor` component with syntax highlighting. You can edit the code directly in the interface.

### File Upload

Click the attachment icon or drag a file into the chat input area to attach documents, images, or code files to your message before sending.

### Sidebar

Use the sidebar to navigate between conversations, start a new session, or access settings. The sidebar collapses on mobile automatically.

### Connecting Your Own Backend

Update `VITE_API_BASE_URL` and `VITE_WS_URL` in your `.env` to point at your server. The `useWebSocket` hook in `client/src/hooks/useWebSocket.ts` handles the connection — wire your server's WebSocket endpoint to an AI streaming SDK and Charlie handles the rest of the UI.

---

## Why This Exists

Building an AI product in 2025 is not about the AI — every team has API access. The bottleneck is always the interface. A credible, responsive, real-time chat UI with code display, file handling, and session management takes weeks to build correctly, even for experienced frontend teams.

Charlie solves this. It is the interface layer that every AI product needs, built once, built properly, and ready to be adapted. The entire shadcn/ui component library is pre-installed, meaning any UI element you need during product development — data tables, command palettes, modals, drawers, charts — is already there. You are never blocked on UI scaffolding again.

This is the starting point that lets you spend your time on what actually differentiates your product: your prompts, your data, your business logic.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Language | TypeScript |
| Framework | React 18 |
| Build Tool | Vite |
| UI Components | shadcn/ui (Radix UI primitives) |
| Styling | Tailwind CSS |
| Real-Time | WebSocket (native + custom hook) |
| Code Editor | Embedded editor component |
| Deployment | Replit / any Node host |

---

## Project Structure

```
Charlieold/
├── client/
│   ├── index.html
│   └── src/
│       ├── App.tsx                    # Root application component
│       ├── index.css                  # Global styles + Tailwind directives
│       ├── components/
│       │   ├── ChatInterface.tsx       # Core chat UI
│       │   ├── CodeEditor.tsx          # Embedded code editor
│       │   ├── ErrorBoundary.tsx       # Error isolation
│       │   ├── FileUpload.tsx          # File attachment handler
│       │   ├── Sidebar.tsx             # Navigation sidebar
│       │   └── ui/                    # Complete shadcn/ui component library (40+ components)
│       └── hooks/
│           ├── use-mobile.tsx          # Responsive breakpoint hook
│           ├── use-toast.ts            # Toast notification hook
│           └── useWebSocket.ts        # WebSocket connection manager
├── .gitignore
├── .replit                            # Replit deployment config
└── README.md
```

---

## Roadmap

- [ ] `.env.example` file with documented variables
- [ ] Demo mode with sample conversation (no backend required)
- [ ] Backend starter template (Express + OpenAI streaming)
- [ ] Docker / `docker-compose` setup for self-hosted deployment
- [ ] Conversation export (JSON, Markdown)
- [ ] Theme switcher (light / dark / custom brand colors)

---

## License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

For white-label or commercial licensing inquiries (including setup support, custom branding, and backend integration), contact the repository owner directly.

---

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change. Please make sure to update tests as appropriate.

---

*Built with React, TypeScript, and shadcn/ui. Designed to accelerate AI product development.*