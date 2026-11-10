# KryloCanvas (Web-WhiteBoard)

> **An advanced, zero-install, single-file HTML5 collaborative whiteboard, technical drafting, and interactive visual workspace.**

[](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5)
[](https://tailwindcss.com/)
[](http://fabricjs.com/)
[](https://github.com)
[](https://github.com)

---

## Table of Contents

1. [Overview & Philosophy](#overview--philosophy)
2. [Highlights at a Glance](#highlights-at-a-glance)
3. [Deep-Dive Feature Architecture](#deep-dive-feature-architecture)
   - [3.1 Universal Canvas & Adaptive Rendering Engine](#31-universal-canvas--adaptive-rendering-engine)
   - [3.2 Theming & Responsive Workspace Design](#32-theming--responsive-workspace-design)
   - [3.3 Page Styling & Engineering Graph Paper](#33-page-styling--engineering-graph-paper)
   - [3.4 Mathematical Drafting & Measuring Instruments](#34-mathematical-drafting--measuring-instruments)
   - [3.5 Drawing Tools & Universal Stroke Engine](#35-drawing-tools--universal-stroke-engine)
   - [3.6 Specialized Eraser Suite](#36-specialized-eraser-suite)
   - [3.7 2D Geometric Shapes & Stroke Customization](#37-2d-geometric-shapes--stroke-customization)
   - [3.8 Typography, Fonts & Mobile Floating Pane](#38-typography-fonts--mobile-floating-pane)
   - [3.9 Flowcharts, Process Trees & Mind Mapping](#39-flowcharts-process-trees--mind-mapping)
   - [3.10 Interactive Tables Engine](#310-interactive-tables-engine)
   - [3.11 Memos & Sticky Notes](#311-memos--sticky-notes)
   - [3.12 Multi-Page Management & Drag-and-Drop Page Switcher](#312-multi-page-management--drag-and-drop-page-switcher)
   - [3.13 Multi-Format Import & Lossless PDF Export](#313-multi-format-import--lossless-pdf-export)
   - [3.14 Performance, Memory Optimization & Audio Synthesis](#314-performance-memory-optimization--audio-synthesis)
4. [Technology Stack](#technology-stack)
5. [Getting Started & Usage](#getting-started--usage)
6. [Keyboard Shortcuts & Interaction Guide](#keyboard-shortcuts--interaction-guide)
7. [Author & Intellectual Property](#author--intellectual-property)

---

## Overview & Philosophy

**KryloCanvas (Web-WhiteBoard)** is an all-in-one, modern web-based whiteboard and technical sketching application packaged inside a standalone, lightweight HTML file. It bridges the gap between casual digital whiteboards and high-precision computer-aided technical drafting suites. 

Engineered for educators, students, engineers, architects, presenters, and project planners, KryloCanvas delivers an uncompromising suite of tools: mathematically solid geometry instruments with edge snapping, millimeter-accurate isometric and Cartesian graph papers, full-featured interactive tables, automated process flowchart and mind map hierarchies, responsive multi-page document pagination, multi-format Office/PDF import capabilities, and lossless vector PDF export.

KryloCanvas requires **no server-side backend, no build steps, and no installation**. It runs directly inside modern web browsers across desktops, laptops, tablets, iPads, and mobile devices while actively conserving client-side memory through intelligent raster virtualization and adaptive device pixel ratios.

---

## Highlights at a Glance

* **Mathematical Precision Drafting**: True-to-scale extensible rulers, 180° geometry protractor with dual degree scales, 45° and 30°-60°-90° drafting set squares, and a precision compass with real-time radial readouts down to 0.01 cm (0.1 mm).
* **Solid Boundary Collision & Edge Snapping**: Measuring instruments can function in **Trace Mode** (drawing snaps directly along physical measurement bevels) or **Markings Mode** (instruments act as physical barriers where stylus ink stops at outer edges and resumes on exit).
* **Multi-Scale Graph Paper Engine**: 5 distinct grid types (1 mm, 2 mm, 1/10 Inch, Isometric 30°, Diamond 45°) with 8 engineering colorways and custom RGB spectra, supporting both **A4 Print Scale** (6 px = 1 mm; prints true-to-life on A4 paper) and **Actual Screen Scale** (3.78 px = 1 mm at 96 DPI).
* **Intelligent Multi-Page Workflow**: Infinite multi-page canvas with drag-and-drop page reordering, individual page rotation, a toolbar page counter, and automated date/time/page header stamping that dynamically adapts its contrast to the underlying content.
* **Full Process Diagramming & Mind Mapping**: 7 structural topologies with collapsible branches, auto-tidying algorithms, arbitrary block shapes, custom colors with glowing ambient halos, and elastic connector arrows featuring draggable Bézier curve handles.
* **Interactive Tables Engine**: Fast 10×10 Word-style hover matrix insertion or custom numeric grid creation (up to 100×100), with multi-cell selection, border/fill styling, and adjustable inter-cell spacing.
* **Typography & Responsive Text System**: 7 web typography families (including modern sans, rounded, serif, dot matrix, comic, monospace, and script), supported on mobile devices by a floating, non-intrusive 2-column draggable pane.
* **Comprehensive Office & PDF I/O**: Direct import for PDF, PNG/JPEG, Word (`.docx`), Excel (`.xlsx`, `.xls`, `.csv`), and PowerPoint (`.pptx`) with lazy background rendering, plus 1:1 vector PDF export with embedded whiteboard state persistence (`KCWB1`).

---

## Deep-Dive Feature Architecture

### 3.1 Universal Canvas & Adaptive Rendering Engine

At the core of KryloCanvas is an enhanced **Fabric.js (v5.3.1)** HTML5 canvas pipeline optimized for multi-surface rendering.

* **Two-Step Dynamic Device Pixel Ratio (DPR)**: To prevent browser crashes and memory exhaustion on high-density mobile and Retina displays (which can allocate up to 9× more pixels than visible), KryloCanvas initializes with a capped base pixel ratio (`1.0` on phones/low-memory hardware, `1.5` on tablets, and `2.0` on desktops). When high-precision tasks are detected (such as zooming into the workspace, drawing with compass/rulers, or rendering millimeter graph grids), the engine temporarily elevates the DPR to maximum sharpness and scales it back down during idle periods.
* **Universal Color & Thickness Pipeline**: Changes made to the global toolbar color picker or the universal thickness slider (1 to 40 px) dynamically propagate across all drawing tools (Pen, Fountain Pen, Pencil, Highlighter) and newly inserted shapes without desynchronizing active selections.
* **History State Management**: Every page maintains an isolated, 20-step undo/redo snapshot stack. A customized serialization engine preserves custom node attributes, connector bindings, table data structures, and mathematical alignments across undo/redo actions.

---

### 3.2 Theming & Responsive Workspace Design

KryloCanvas includes an adaptable user interface designed for maximum contrast and ergonomics in varied lighting environments.

* **Day / Night Pill Switch**: A custom SVG toggle switch featuring an animated day/night capsule (sun, clouds, moon with lunar craters, starlight glow, and silhouette hills). The button maintains high-visibility white/black outline borders across light and dark modes.
* **Curated Page Themes**:
  * **White Theme**: Crisp white surface with light grey alignment grids.
  * **Black Theme**: Dark slate surface with charcoal grids for reduced eye strain.
  * **Grey Theme**: Neutral mid-tone grey for balanced color rendering.
* **Custom Theme Colour Spectrum**: An integrated modal containing a 2D hue-saturation wheel, a brightness/value shade box, a hue spectrum slider, a white-to-black grayscale slider, individual R/G/B and H/S/V numeric inputs, HEX code inputs, and real-time WCAG contrast ratio calculations (`W X:1` or `B X:1`).
* **Adaptive Toolbar Compaction**: The top application header monitors viewport width and automatically compacts elements in stages (`kc-s1`, `kc-s2`, `kc-s3`, and `kc-wide`) to prevent UI wrapping, toolbar overflow, or button clipping on smaller viewports.
* **Workspace Closed Screen**: Closing the session reveals a stylized closing screen with a centered brand emblem, session confirmation, and a "Reopen Workspace" button with animated transitions and sound effects.

---

### 3.3 Page Styling & Engineering Graph Paper

Every whiteboard page can be styled independently to suit diverse note-taking and drafting tasks.

| Page Style | Description | Ideal Use Case |
| :--- | :--- | :--- |
| **Blank** | Clean canvas free of background lines or artifacts | Conceptual sketching, art, and freehand illustrations |
| **Standard Grid** | 40×40 px orthogonal grid with subtle grid borders | General diagramming, wireframing, and block layouts |
| **Single Lines** | 36 px vertical ruled lines with 1 px margin lines | Lined note-taking, prose, and structured writing |
| **Dotted Grid** | Dot matrix pattern with 36 px radial spacing | Bullet journaling, UI prototyping, and dot-matrix drafting |
| **Graph Paper** | High-precision engineering and mathematical graph grids | Geometric drafting, calculus, physics, and isometric rendering |

#### Advanced Graph Paper Engine
* **5 Grid Types**:
  1. *Millimeter (1 mm)*: 10×10 small squares per 1 cm block with major, medium, and minor hierarchy lines.
  2. *2 Millimeter (2 mm)*: 5×5 grid blocks per 1 cm for less dense technical calculations.
  3. *Inch (1/10 in)*: Imperial grid with 10 subdivisions per inch, medium lines at 1/2 inch, and heavy lines at 1 inch.
  4. *Isometric (30°)*: Equilateral triangle mesh generated with 30° axes and vertical guidelines for 3D engineering projections.
  5. *Diamond (45°)*: 45° rotated diagonal square grid with 5 mm diamond divisions.
* **8 Pre-Configured Colorways**: Green (Classic Engineering), Blue (Blueprint), Red/Maroon (Scientific), Orange (Warm Precision), Black & White (Monochrome High-Contrast), Pink, Yellow, and Violet/Purple.
* **Two Paper Scale Modes**:
  * **A4 Print Size (6 px = 1 mm)**: Generates an exact A4 page (210×297 mm, 1260×1782 px). When exported to PDF and printed at 100% scale, printed measurements match real-world physical metric rulers. On these pages, rulers, protractors, and set squares automatically adapt to this 6 px/mm scale.
  * **Actual Screen Size (3.78 px = 1 mm)**: Standard 96 DPI screen scale (1200×1600 px), ensuring comfortable viewing and interaction on standard desktop monitors.
* **Uniform Framing Margins**: Users can toggle an outer margin around graph paper. The margin boundary snaps directly to full grid lines, preventing cut-off partial grid cells at paper edges.

---

### 3.4 Mathematical Drafting & Measuring Instruments

KryloCanvas features virtual geometric drafting instruments that simulate real physical tools.

```
       [Trace Mode]  --------------------> Snaps pen strokes directly to instrument scale
       [Markings Mode] ------------------> Instrument acts as solid body; prevents bleed-through
```

#### 1. Extensible Ruler
* Translucent acrylic glass rendering with bevel refraction gradients.
* Dual measurement scales: Top edge calibrated in Centimeters & Millimeters; bottom edge calibrated in Inches (1/16th inch increments).
* Resizing handles allow horizontal expansion while maintaining scale accuracy.
* Trace Mode automatically renders clean, straight lines along ruler edges with an extended magnetic reach (~75 px).

#### 2. 180° Geometry Protractor
* Realistic stationery protractor design featuring a pure semicircular arc, flat baseline, and clear viewing window.
* Dual degree graduations running in opposite directions (0° to 180° left-to-right on the outer ring; 180° to 0° right-to-left on the inner ring).
* Graduated tick marks at 1°, 5°, and 10° intervals with radial angle lines converging toward the center origin.
* High-visibility red origin crosshair, targeting bullseye, and an upward-pointing "MARKING POINT" indicator.
* Snapping allows users to trace either the circular upper arc or the straight bottom reference edge.

#### 3. 45° & 30°-60°-90° Drafting Set Squares
* Precision-scaled triangles with internal viewing cutouts.
* Millimeter and centimeter scale graduations along vertical and horizontal legs.
* Clean hypotenuse edges allowing straight diagonal drafting lines.

#### 4. Precision Geometry Compass
* Mechanical steel and brass compass illustration featuring an adjustable pivot needle and pencil tip.
* **Lockable Needle Pivot**: Tap and hold the red crosshair pivot needle to lock ("Fix") it to the canvas. Once fixed, the compass needle remains stationary while the pencil arm can be freely rotated or extended.
* **Directional Extension Handle (`↔ Extend`)**: Drag the pencil arm along its axis to increase or decrease radius without rotating the compass.
* **Fine-Grained Radius Tuning**: Radius adjustable down to 0.00 cm with 0.01 cm (0.1 mm) increments via HUD buttons, sliders, or direct numerical entry.
* **Live Alongside Floating HUD**: Displays a floating pill badge with current radius dimensions (`R = X.XX cm (XX mm)`).
* **Drawing Actions**:
  * *Circle*: Automatically renders a 360° circle centered at the needle pivot point.
  * *Arc*: Renders an exact 90° arc starting from the current pencil tip position.
  * *Custom Arc*: Dedicated panel with angle sliders and precise arc-length calculators in mm, cm, inches, or meters.
  * *Mark Center*: Places an ink dot directly at the needle pivot point.
  * *Flip*: Flips the compass arm horizontally without altering the pivot coordinates.

---

### 3.5 Drawing Tools & Universal Stroke Engine

* **Pen**: Standard solid drawing brush for everyday writing and sketching.
* **Fountain Pen**: Dynamic calligraphic pen with smoothed line joins and an enlarged stroke footprint.
* **Pencil**: Fine-point drafting pencil with 0.5× stroke scale for detailed annotations.
* **Highlighter**: Translucent stroke with 4× width multiplier, preserving underlying text and ink visibility.
* **Select Tool**: Unlocks full manipulation of drawn strokes, inserted shapes, text boxes, and images. Includes Fabric.js control points for rotating, scaling, skewing, and deleting objects.
* **Preview Mode**: Pan and pinch-zoom across all pages simultaneously using native multi-touch gestures or `Ctrl + Mouse Wheel`.

---

### 3.6 Specialized Eraser Suite

KryloCanvas provides four distinct erasing tools tailored for different workflows:

1. **Normal Eraser**: A circular touch eraser with a live visual boundary cursor. It uses geometric segment bisection to cut freehand vector strokes, removing erased segments while leaving remaining line portions intact.
2. **Pixel Lasso Eraser**: A continuous eraser stroke that deletes underlying vector segments along its path.
3. **Section Eraser**: A bounding-box selection eraser. Drag a selection rectangle over any section of the canvas to delete all enclosed strokes and shapes.
4. **Region Eraser (Pixel Brush)**: A freehand stroke eraser. Scribble over any collection of strokes, and any intersecting objects will be cleared upon stroke completion.

---

### 3.7 2D Geometric Shapes & Stroke Customization

Users can insert 43 pre-configured vector shapes from an organized pop-up grid:

* **Polygons & Triangles**: Equilateral Triangle, Isosceles Triangle, Scalene Triangle, Right Angle Triangle, Square, Rectangle, Rounded Square, Rounded Rectangle, Squircle, Parallelogram, Rhombus, Trapezium, Kite, Pentagon, Hexagon, Heptagon, Octagon, Diamond.
* **Curves & Arcs**: Circle, Semicircle, Oval, Wedge, Straight Line, Curved Line, S-Shaped Curve.
* **Arrows & Symbols**: Right Arrow, Left Arrow, Up Arrow, Down Arrow, Horizontal Double Arrow, Vertical Double Arrow, Curved Arrow Right, Curved Arrow Left, Return Arrow, Heart, Moon, Cloud, Star, Cross.
* **Flow & Structural Shapes**: Cylinder, Document, Data (Input/Output), Callout.

#### Shape Styling Floating HUD
Selecting any shape opens a floating customization HUD:
* **Outline / Fill Tabs**: Switch between outline stroke styling and background fill colors.
* **Line Styles**: Choose from **Solid**, **Dashed**, **Dotted**, **Dash-dot**, and **Long dash** stroke patterns.
* **Weight & Opacity Sliders**: Adjust stroke widths from 1 to 20 px and object opacity from 0% to 100%.
* **Proportional Resizing**: Adjust shape dimensions via a dedicated size slider (20 px to 1000 px) or using bounding box corner handles.

---

### 3.8 Typography, Fonts & Mobile Floating Pane

KryloCanvas features an in-canvas typography engine that integrates seamlessly with Fabric.js text boxes.

#### 7 Web Font Families
1. **Krylo Sans** (`Inter`): Clean, modern sans-serif for general text.
2. **Krylo Sans Plus** (`Fredoka`): Rounded display font for headlines and creative notes.
3. **Krylo Sans Premia** (`Playfair Display`): High-contrast serif for formal headings.
4. **Krylo Sans Dotted** (`Silkscreen`): Dot-matrix typeface inspired by technical LCDs.
5. **Krylo Comic** (`Comic Neue`): Casual handwriting style for storyboarding.
6. **Krylo Mono** (`Courier New`): Monospaced typeface for tabular data and code.
7. **Krylo Script** (`Caveat`): Expressive handwritten cursive font.

#### Mobile Draggable Text Pane (`#kc-tpane`)
On mobile screens and tablets (viewports < 768 px), opening the text formatting panel can obscure active typing areas. KryloCanvas automatically replaces the modal dialog with an unobtrusive, 2-column floating pill toolbar:
* **Drag-to-Move**: Position the toolbar anywhere on the screen using its 4-way arrow handle.
* **Inline Styling**: Direct toggle buttons for Bold, Italic, Underline, and Alignment.
* **Size Stepper & Input**: Tap `+4` / `-4` buttons or type an exact pixel size directly.
* **More Options & Enlarge**: Expand into the full formatting panel or open the custom color wheel.
* **Docking Edge Tab (`Aa`)**: Closing the pane minimizes it into a compact edge tab that can be tapped to restore controls at any time.

#### Clipboard Text Editor Modal
A dedicated text-editing modal allows users to edit multi-line text, format blocks, copy selections to the clipboard, cut highlighted phrases, and paste external text without virtual keyboards triggering unexpected browser viewport zoom changes.

---

### 3.9 Flowcharts, Process Trees & Mind Mapping

KryloCanvas features an automated process diagramming and tree generation engine.

```
       [Root Process]
             │
      ┌──────┴──────┐
 [Branch A]    [Branch B]
      │             │
  [Leaf 1]      [Leaf 2]
```

* **7 Diagram Topologies**:
  1. *Horizontal Flow*: Sequential steps running left to right with connector arrows.
  2. *Vertical Tree*: Top-down hierarchy running from root nodes to subordinate branches.
  3. *Mind Map*: Central topic node with radial branches projecting outward.
  4. *Cycle*: Circular process loops where the final step reconnects to the first.
  5. *Decision Tree*: Diamond decision nodes branching to conditional outcome blocks.
  6. *Org Chart*: Structured multi-tier management tree with executive and department nodes.
  7. *Single Node*: Blank starting block for building custom network topologies.
* **Elastic Connector Arrows**:
  * Arrows are bound to parent and child nodes by unique IDs. Repositioning or resizing a node automatically recalculates arrow lengths and connection angles in real time.
  * **Draggable Bézier Handle (`fcCurve`)**: Selecting an arrow displays a central green handle that can be dragged to bend straight lines into smooth curves.
  * **Arrow Toolbar**: Quickly reverse arrow direction, flip curve orientation, rotate bends by 45°, straighten lines, adjust line thickness (1 to 20 px), switch dash patterns, and select arrow head styles (End, Both, Open, None).
* **Automated Tree Operations**:
  * *Child / Sibling Creation*: Instantly spawn child nodes or sibling blocks with matching visual themes.
  * *Fan Branches*: Create 2, 3, 5, or a custom number (1 to 20) of branching leaves at once.
  * *Sub-tree Folding*: Collapse or expand subordinate node trees to declutter complex diagrams.
  * *Auto-Tidy (Tree Realignment)*: Automatically repositions and balances all nodes across a tree hierarchy with uniform horizontal and vertical spacing.
* **Custom Node Shapes**: Flowchart nodes can adopt any of the 43 vector shape geometries while maintaining centered, auto-wrapped text.

---

### 3.10 Interactive Tables Engine

KryloCanvas includes an integrated, spreadsheet-style table system.

* **Word-Style 10×10 Hover Grid**: Hover and click across a visual grid selector to instantly insert tables up to 10×10 on the active page.
* **Custom Numeric Input**: Insert tables with up to 100 rows and 100 columns using numeric inputs.
* **Full Object Manipulation**: Tables can be dragged, scaled via bounding handles, or rotated to any angle.
* **Cell Selection Modes**: Tap any cell to select it, drag across cells to highlight multi-cell rectangular ranges, or use toolbar shortcuts to select entire rows, columns, or the whole table.
* **In-Place Cell Editing**: Double-click or double-tap any cell to open the text editor, with automatic line wrapping and vertical alignment (Top, Middle, Bottom).
* **Table HUD Features**:
  * *Cell Spacing*: Adjust the gap between table cells from 0 px (joined borders) up to 40 px (separated card grids).
  * *Column Width & Row Height*: Increment or decrement dimensions with `+5` / `-5` buttons or enter exact pixel values.
  * *Add / Remove Rows & Columns*: Add or delete rows and columns at any position.
  * *Border & Fill Styling*: Apply background fills and border outlines to selected cells, rows, or the entire table.

---

### 3.11 Memos & Sticky Notes

* **Visual Sticky Notes**: Insert rounded sticky notes with customizable soft ambient glow halos.
* **Circular Color Palette**: Select note colors using an 8-point radial color ring or a full custom color wheel.
* **Internal Page Patterns**: Switch memo backgrounds between **Blank**, **Grid**, **Lines**, and **Dots**.
* **Direct Typography**: Double-tap notes to edit multi-line text, adjust font sizes, apply alignments, and format text.

---

### 3.12 Multi-Page Management & Drag-and-Drop Page Switcher

* **Drag-and-Drop Page Reordering**: Every page features an interactive purple **Page Switcher** side button. Press and hold to drag the page vertically across the workspace; a glowing drop-line indicator highlights target insertion points.
* **Independent Page Rotation**: Tap the blue rotate button on any page to rotate its dimensions, background patterns, and vector drawings by 90° clockwise.
* **Dynamic Header & Watermark**: Every page automatically renders an unobtrusive date, day, and page counter (`DD/MM/YYYY - DayName | Page X / Y`) in the upper-right corner. The system continuously evaluates the luminance of the canvas behind the watermark, dynamically rendering white text over dark backgrounds and black text over light backgrounds.
* **PDF Frame Mode**: When working with imported PDF or Office documents, an invisible content frame allows users to scale, shift, or rotate underlying document pages independently of whiteboard drawings.

---

### 3.13 Multi-Format Import & Lossless PDF Export

#### Import Capabilities
* **PDF Import**: Utilizes **PDF.js** to stream and render multi-page documents. Pages load lazily to preserve memory on large documents.
* **Image Import**: Load PNG and JPEG graphics. Images are automatically scaled to prevent memory overloads from high-resolution mobile camera uploads.
* **Microsoft Word / Google Docs (`.docx`)**: Parsed via **Mammoth.js** and paginated into canvas pages.
* **Microsoft Excel (`.xlsx`, `.xls`, `.csv`)**: Processed via **SheetJS**, breaking dense spreadsheets into readable multi-page grid views.
* **Microsoft PowerPoint (`.pptx`)**: Custom XML parser renders slide graphics, shapes, tables, and typography into whiteboard pages.

#### Lossless Export Capabilities
* **Single-Page PNG Export**: Download high-resolution PNG images of the current active page with all UI overlays and handles cleanly hidden.
* **Multi-Page Vector PDF Export**: Generates printable PDF documents via **jsPDF**. Every page is rendered onto true A4 paper sizes (in matching portrait or landscape orientations) or 96 DPI screen formats.
* **Lossless State Serialization (`KCWB1`)**: Exported PDFs embed a serialized JSON snapshot of the entire whiteboard session inside the PDF metadata header (`Subject` field). Re-importing the PDF into KryloCanvas restores all objects, shapes, tables, and flowcharts in an editable state.

---

### 3.14 Performance, Memory Optimization & Audio Synthesis

* **Canvas Virtualization (Page Sleeper)**: Documents with 6 or more pages use an `IntersectionObserver` to collapse the canvas backbuffers (`width=1, height=1`) of off-screen pages. Underlying vector objects are preserved in memory while freeing up GPU textures, restoring full resolution automatically as pages scroll into view.
* **Lazy Zip Decompression**: Uses the browser's native `DecompressionStream` to read ZIP central directories on demand, avoiding loading multi-megabyte `.docx` or `.pptx` files entirely into RAM.
* **Synthesized Audio Engine**: Sound effects (such as the canvas whoosh animation) are synthesized programmatically using the **Web Audio API** via bandpass noise buffers and exponential gain ramps, eliminating external audio asset dependencies.

---

## Technology Stack

* **Markup & Structure**: HTML5 Canvas, SVG vectors.
* **Styling & Theming**: Tailwind CSS (CDN-delivered), CSS Container Queries, CSS Grid, Custom Variables.
* **Canvas Manipulation Engine**: Fabric.js (v5.3.1).
* **Document Processing & Conversion**:
  * PDF.js (v2.16.105) — Lazy PDF rendering.
  * jsPDF (v2.5.1) — Client-side PDF generation.
  * JSZip (v3.10.1) & DecompressionStream — In-memory archive extraction.
  * Mammoth.js (v1.4.2) — `.docx` to HTML translation.
  * SheetJS / xlsx (v0.18.5) — Spreadsheet parsing.
* **Web Fonts**: Google Fonts (`Inter`, `Fredoka`, `Playfair Display`, `Silkscreen`, `Comic Neue`, `Courier New`, `Caveat`).
* **Audio**: Native Web Audio API (`AudioContext`).

---

## Getting Started & Usage

KryloCanvas is delivered as a **single, self-contained `index.html` file**.

### Running the Application

1. **Direct Browser Execution**:
   * Double-click `index.html` or open it with any modern browser (Chrome, Edge, Safari, Firefox, Opera).
2. **Local Static Server**:
   ```bash
   # Using Python 3 built-in server
   python3 -m http.server 8000
   
   # Or using Node.js npx serve
   npx serve .
   ```
   Navigate to `http://localhost:8000` in your web browser.

---

## Keyboard Shortcuts & Interaction Guide

| Context | Action | Shortcut / Gesture |
| :--- | :--- | :--- |
| **Global** | Undo last canvas action | `↩️ UNDO` Button / `Ctrl + Z` |
| **Global** | Redo last canvas action | `↪️ REDO` Button / `Ctrl + Y` |
| **Preview Tool** | Zoom in / Zoom out | `Pinch In / Out` or `Ctrl + Mouse Wheel` |
| **Preview Tool** | Pan across pages | `1-Finger Drag` (Touch) or `Left-Click Drag` (Mouse) |
| **Selection** | Delete selected object(s) | Red Trash Icon / `Delete` Key |
| **Selection** | Rotate selected object(s) | Circular Arrow Handle (Top Center) |
| **Text Tool** | Create new text block | Click/tap anywhere on an active page |
| **Text Tool** | Edit existing text | Double-click or double-tap on text box |
| **Flowchart** | Edit block label | Tap green pencil handle `✎` or double-tap block |
| **Flowchart** | Curve connector arrow | Drag the green curvy-arrow handle on the arrow |
| **Compass** | Fix / Lock needle pivot | Press and hold red needle crosshair -> Select **📌 Fix** |
| **Compass** | Extend compass radius | Drag `↔ Extend` handle along the arm |
| **Compass** | Freehand arc drawing | Tap and hold pencil tip -> Select **Draw Arc Freely** |
| **Tables** | Edit cell text | Double-click / double-tap inside any cell |
| **Tables** | Multi-cell selection | Click and drag across adjacent cells |
| **Pages** | Reorder / Move page | Press, hold, and drag the purple **Page Switcher** button |
| **Pages** | Rotate page 90° | Tap the blue circular arrow button on the right edge |

---

## Author & Intellectual Property

**KryloCanvas (Web-WhiteBoard)** was created and architected by **Abhimat Chatterjee**.

The complete software architecture, structural algorithms, math snapping implementations, design paradigms, and intellectual property embodied within this project belong to the author.

* **Creator & Architect**: Abhimat Chatterjee
* **Copyright**: &copy; 2026 Abhimat Chatterjee. All rights reserved.
