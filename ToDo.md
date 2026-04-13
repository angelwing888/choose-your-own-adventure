# ToDo

## Setup
- [ ] Set up React project with Vite (`npm create vite@latest`)
- [ ] Install dependencies: React Router, Cytoscape.js (or React Flow) for graph viz
- [ ] Set up GitHub Pages or Vercel deployment pipeline
- [ ] Create `web/data/` directory for JSON data files

## Data Preparation
- [ ] Write script to convert `output/cot-pages-ocr-v2/*.txt` → `web/data/pages.json`
- [ ] Write script to convert `output/cot-story-graph.mmd` → `web/data/graph.json`
- [ ] Verify pages.json has correct page text and page numbers
- [ ] Verify graph.json has correct edges matching the .mmd file

## Landing Page
- [ ] Create a home page with links to Reader and Authoring Tool
- [ ] Add basic styling and project description

## Story Reader
- [ ] Create Reader page/component
- [ ] Load and parse `pages.json` and `graph.json`
- [ ] Display current page text
- [ ] Render clickable choice buttons based on graph edges
- [ ] Handle navigation between pages on choice click
- [ ] Handle terminal pages (endings) — show restart option
- [ ] Add a "back" button or history breadcrumb
- [ ] Style the reader to feel like a book/story experience

## Authoring Tool — Core
- [ ] Create Authoring Tool page/component
- [ ] Add ability to create a new story segment (title + text body)
- [ ] Add ability to edit an existing segment
- [ ] Add ability to delete a segment
- [ ] Add ability to create a choice connection between two segments
- [ ] Add ability to label a choice (e.g. "Go left", "Wait until morning")
- [ ] Save story state to localStorage so work isn't lost on refresh

## Authoring Tool — Graph Visualization
- [ ] Integrate Cytoscape.js or React Flow for graph display
- [ ] Render each story segment as a node
- [ ] Render each choice connection as a directed edge
- [ ] Color terminal nodes differently (no outgoing edges)
- [ ] Color unfinished nodes differently (no outgoing edges but not marked as endings)
- [ ] Highlight the main story trunk from the start node
- [ ] Click a node in the graph to jump to that segment in the editor

## Authoring Tool — Advanced Features
- [ ] Show a list of unfinished/dead-end segments
- [ ] Detect and warn about unreachable segments
- [ ] Detect and highlight segments that converge (multiple paths leading to same node)
- [ ] Export story as JSON file
- [ ] Import story from JSON file

## Deployment
- [ ] Deploy site to GitHub Pages or Vercel
- [ ] Confirm Reader works on deployed site
- [ ] Confirm Authoring Tool works on deployed site
- [ ] Update README.md with the live URL
- [ ] Submit README.md to Canvas before deadline
