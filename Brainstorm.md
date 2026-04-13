# Brainstorm

## Overall Vision
A clean, modern two-part web app:
1. A **Story Reader** — lets anyone play through The Cave of Time interactively
2. An **Authoring Tool** — lets writers build their own CYOA stories with a live graph

---

## Story Reader Ideas

### Layout
- Split screen: story text on the left, mini graph on the right showing where you are
- Or: full-width story text with a collapsible graph panel
- Make it feel like a book — serif font, parchment/dark theme options
- Animate page transitions (fade in/out) when a choice is made

### Features
- Progress indicator — "Page 12 of 114 pages"
- Show how many choices are available at each step
- "Ending reached!" screen with a summary of the path you took
- Restart button that takes you back to page 2
- A visited page history so you can see the path you took
- Optional: show how many total possible endings exist

### Nice-to-haves
- Mobile-friendly layout

---

## Authoring Tool Ideas

### Layout
- Left panel: segment editor (title, text body, list of choices)
- Right panel: live graph visualization that updates as you type/connect
- Top toolbar: New Segment, Export, Import, Save buttons
- Bottom status bar: total segments, unfinished count, endings count

### Graph Visualization
- Nodes = story segments, labeled by title or segment number
- Edges = choices, labeled with the choice text
- Color coding:
  - Blue = start node
  - Green = finished terminal node (an ending)
  - Red/Orange = unfinished node (has no outgoing choices yet)
  - Gray = normal node
  - Yellow = node that multiple paths converge on (a "hub")
- Clicking a node opens that segment in the left panel editor
- Draggable nodes so the author can arrange the graph how they like

### Creating a Story
- Author starts by writing the opening segment
- Adds 1-3 choice buttons at the bottom of each segment
- Each choice either links to an existing segment or creates a new blank one
- New blank segments show up as red/orange "unfinished" nodes on the graph

### Editing Flow
- Click any node on the graph → opens that segment for editing
- Click any edge → shows the choice label, option to rename or delete it
- Drag an edge from one node to another to create a new connection

### Export / Import
- Export as JSON (full story data)
- Export as playable HTML (self-contained file someone can open in a browser)
- Import a JSON file to continue editing a saved story
- Stretch goal: import a .mmd Mermaid file to visualize an existing graph

---

## Data Format Ideas

### pages.json (for the Reader)
```json
{
  "2": {
    "text": "You've hiked through Snake Canyon once before...",
    "choices": [
      { "label": "Start back home", "to": 4 },
      { "label": "Wait until morning", "to": 5 }
    ]
  }
}
```

### story.json (for the Authoring Tool)
```json
{
  "startSegment": "seg-001",
  "segments": {
    "seg-001": {
      "title": "The Canyon",
      "text": "You stand at the edge of Snake Canyon...",
      "choices": [
        { "label": "Go left", "to": "seg-002" },
        { "label": "Turn back", "to": "seg-003" }
      ]
    }
  }
}
```

---

## Tech Stack

- **React + Vite** — fast setup, modern dev experience
- **React Flow** — graph visualization, supports drag, click, custom nodes
- **React Router** — navigation between Reader and Authoring Tool
- **Tailwind CSS** — quick, clean styling without writing lots of CSS
- **localStorage** — persist authoring work between sessions, no backend needed
- **GitHub Pages or Vercel** — free static deployment

---

## Stretch Goals
- AI-assisted writing: a button that suggests the next segment based on the story so far
- Read mode inside the authoring tool: preview how the story plays as a reader
- Statistics page: average path length, most visited node, number of endings
- Undo/redo in the authoring tool
