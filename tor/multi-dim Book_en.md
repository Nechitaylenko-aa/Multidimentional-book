# TECHNICAL SPECIFICATION

## «Multidimensional Book» (Hyperdimensional Book System — HBS)

---

### 1. CONCEPT

> A Multidimensional Book is a system consisting of one main book and several sub-books (satellites), synchronized via invisible tags. The reader engages in linear reading of the main book. At specific points (tagged locations), the system automatically loads the corresponding section of a sub-book into a neighboring tab/panel. This section contains in-depth theory or context necessary for a complete understanding of the current fragment.

**Key difference from hypertext:** No active links, no forced transitions, no reading interruptions. The reader decides independently whether to consult the pre-loaded material or continue reading the main book. The system provides context without imposing it.

---

### 2. SYSTEM COMPONENTS

The system consists of two independent applications:

| Component | Purpose |
|-----------|---------|
| **HBS Writer** | For the author — creation, structuring, tagging, and export of the multidimensional book |
| **HBS Reader** | For the reader — opening, reading, navigation, and synchronization of books |

Both components must operate on all major platforms: Windows, macOS, Linux, and Web (with Web as the priority environment for the Reader).

---

## PART 1. HBS WRITER (FOR AUTHORS)

### 1.1. Book Project Management

- Creating a new project with specification of:
    - Main book title
    - Number of sub-books (from 1 to ∞, optimized for 2–12)
    - Titles and brief descriptions for each sub-book
- Importing existing texts (DOCX, Markdown, TXT) as a basis for chapters
- Auto-save and versioning of the project (local + optional cloud storage)

### 1.2. Main Book Editor

- Full-featured text editor (WYSIWYG or Markdown with preview)
- Support for structure: Book → Part → Chapter → Section → Subsection (up to 6 levels deep)
- Ability to insert:
    - Plain text
    - Illustrations, tables, formulas (LaTeX/MathML)
    - Code blocks with syntax highlighting (for technical books)

### 1.3. Sub-book Editor

- Similar functionality, but with priority on reference/theoretical material
- Each sub-book has its own independent structure
- Ability to reuse sub-books across multiple projects

### 1.4. Tagging — The Key Feature!

> **Core idea:** The author places invisible marker-tags within the main book's text, linking a text fragment to a specific location in a specific sub-book.

**Tagging Interface:**
- Author selects a text fragment (a word, sentence, or entire paragraph)
- Clicks the «Link to Sub-book» button → a selection window opens:
    - Choose a sub-book (e.g., «Sub-book 3: Theory of Relativity»)
    - Choose a section within that sub-book (chapter, part, paragraph) — visual navigation through the sub-book's structure
    - Brief description of the link (optional, for the author's reference)
- The tag is saved as metadata, **with no impact on the main text's display** (no footnotes, asterisks, or highlights in the final book)

**Tag Visualization for the Author:**
- «Show Tags» mode — color highlighting of fragments linked to sub-books
- «All Project Tags» panel — a list of all links with filtering by sub-book
- «Orphan Tag» check — verification of tags pointing to non-existent sub-book sections

### 1.5. Structure and Link Management

- **Link Map (Graph):** Visual representation of which main book fragments are linked to which sub-book sections
- **Statistics:**
    - Number of tags in each chapter
    - Which sub-books are used most frequently
    - Where the highest «density» of references occurs
- **Automated Checks:**
    - Do all tags point to existing sub-book sections?
    - Are there any circular dependencies?
    - Are there any «dangling» sub-book sections not linked to the main book?

### 1.6. Export

**HBS-KIT Format (packaged archive with metadata):**
- `manifest.json` — book description, list of sub-books, tags, and structure
- `main_book/` — all main book files
- `subbooks/` — files for each sub-book
- `metadata/` — files with tags and link data

**Additional Export Formats (optional):**
- Export to EPUB (with loss of multidimensionality — only linear text)
- Export to PDF (with footnotes indicating which sub-books have linked content)
- Export to web version (HTML + JS + CSS — runs in a browser without installation)

---

## PART 2. HBS READER (FOR READERS)

### 2.1. Reading Interface

**Default Mode:**
- Main book displayed full-screen in linear reading mode
- Display: table of contents, page/position numbers, reading progress
- Support for bookmarks, highlights, and notes (local storage)

**Mode with Loaded Sub-book:**
- System tracks reading position in the background
- When reader reaches a tagged fragment → the corresponding sub-book section automatically opens in a neighboring tab/panel (right, bottom, or new browser tab — user-configurable)
- **No animations, pop-ups, sounds, or visual interruptions** to the main reading flow
- The reader merely notices that the sub-book tab has appeared (or updated its content)

**Tag Navigation Behavior:**
- If the reader opens the neighboring sub-book tab, they see the relevant section
- After reviewing, they can close the tab or switch back to the main book
- If the reader scrolls the main book backward or forward, the sub-book synchronizes accordingly

### 2.2. Synchronization Settings

The reader can configure system behavior:

| Option | Description |
|--------|-------------|
| **Auto-load** | Whether synchronization is enabled by default |
| **Sub-book Location** | Right / Bottom / New Tab / Pop-up Window |
| **Load Depth** | Exact paragraph only / Entire chapter / Brief summary |
| **Notifications** | Whether to show an icon indicating a sub-book has been loaded |
| **History** | Whether to save history of opened sub-book sections |

### 2.3. Navigation

- **Table of Contents** — separate for each book (main and sub-books)
- **Switching Between Books** — via tabs or keyboard shortcuts
- **Search** — across the main book and all sub-books simultaneously
- **Link Map** (for advanced readers) — visualization of which main book fragment links to which sub-book

### 2.4. Technical Requirements for Reader

- Cross-platform: browser version (primary) + desktop wrappers for Windows/macOS/Linux
- Works offline (after loading HBS-KIT)
- Ability to open multiple books simultaneously
- Export of notes and highlights

---

## PART 3. UNIQUE ADVANTAGES (WHY THIS IS NEEDED)

### 3.1. For the Reader

- **Seamless Reading** — no hyperlinks, no distractions from clicking. Reading remains linear and immersive.
- **Context at Hand** — theory isn't relegated to an appendix or footnotes; it's always nearby but never imposed.
- **Freedom of Choice** — the reader decides whether to dive deeper. No one forces them.
- **Accelerated Learning** — ideal for technical literature: read a mechanism description, see the theory sub-book alongside, study exactly what's needed at that moment.
- **Reduced Cognitive Load** — no need to remember where that formula from Chapter 3 was; the system reminds you at the right moment.

### 3.2. For the Author

- **New Presentation Format** — the ability to create a book that adapts to the reader's level (beginners read only the main book; professionals load sub-books).
- **Modularity** — write a sub-book (theory, reference) once and use it across multiple projects.
- **Depth Without Clutter** — the main book stays concise and readable; all extras go into sub-books.
- **Easier Maintenance of Complex Material** — keep things current: update theory in the sub-book → it updates automatically everywhere it's used.
- **Analytics** — know which sub-book sections readers open most often and where material needs improvement.

### 3.3. For Publishers and Platforms

- **New Market Product** — sell not just a book but a «knowledge ecosystem».
- **Subscription Model** — for example, main book sold once; sub-books updated and expanded via subscription.
- **Educational Institutions** — ideal for university textbooks with core material and advanced sections for more proficient students.
- **Technical Documentation** — documentation for complex systems (API, medical equipment, engineering) benefits greatly from this format.

---

## PART 4. TECHNICAL ARCHITECTURE SOLUTIONS (FOR DEVELOPERS)

### 4.1. Data Format (HBS-KIT)

- Root folder with `manifest.json`
- All texts in Markdown (with extensibility to HTML for complex layout)
- Tag files: `tags.json` — an array of objects with the following fields:

```json5
{
  "id": "tag_001",
  "main_book": {
    "book_id": "main",
    "section": "chapter1/part2/paragraph3"
  },
  "subbook": {
    "book_id": "subbook_3",
    "section": "chapter5/part3/paragraph1"
  },
  "description": "Theory of relativity for understanding relativistic effects",
  "active": true
}
```

- Book structure defined in toc.json (table of contents for each book)

### 4.2 Synchronization Logic (Reader)

1. Reader advances through the main book → current section changes.
2. System checks: Are there any tags for the current section (or position range)?
3. If yes — the corresponding sub-book section loads in the background and is buffered for the neighboring tab.
4. The neighboring tab/panel automatically updates its content but does not shift focus away from the main book.
5. All operations run via an event-driven model, locally, without servers.

### Proposed Technology Stack

|Component|Proposed Stack|
|---------|--------------|
|Frontend (Reader)|React / Vue + TypeScript, using IndexedDB for local book storage|
|Backend (optional)|Node.js / Python for cloud storage and device synchronization|
|Writer|Electron (desktop) + React / Vue, or a separate web application|
|Storage Format|Markdown + JSON, archived as ZIP (similar to EPUB)|
|Position Synchronization|localStorage or a separate state file|


### DEVELOPMENT ROADMAP (MINIMUM FOR MVP)


Stage 1 (MVP — 3–4 months development)

    Writer: Basic book + sub-book structure, manual tagging via interface

    Reader: Opening HBS-KIT, synchronization on desktop (Electron), single sub-book position

    Export/Import: Local HBS-KIT format only

Stage 2 (6–9 months)

    Writer: Visual link map, automated checks, DOCX import

    Reader: Web version, synchronization settings, multiple sub-books simultaneously

    Cloud storage for books and reader progress

Stage 3 (12–18 months)

    Export to EPUB/PDF with preserved footnotes

    Analytics for authors

    Plugins and API for integration with educational platforms

    Mobile applications (iOS/Android)
    
    
## CONCLUSION

The Multidimensional Book is not just a reader with sub-books — it is a new way of structuring and consuming knowledge. It solves a real problem: how to make complex material accessible without oversimplifying it; how to offer depth without cognitive overload.

This format does not currently exist. Whoever implements it first will gain:

    Technological advantage in the EdTech sector

    Loyal audience among authors and readers of complex literature

    Patent potential (should they choose to pursue it)    
