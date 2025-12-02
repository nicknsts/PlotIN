# PlotIN Manual

## 1. Introduction
PlotIN is a minimalist, fast, and academically oriented plotting tool designed for scientific and engineering workflows.  
It transforms pasted tabular data into publication-ready graphs within seconds.

No file imports are required — **copy → paste → preview → adjust → export**.

---

## 2. Data Input (Copy & Paste)
PlotIN accepts data exclusively via **paste**, directly from:
- Excel
- CSV/TSV
- MATLAB
- LabVIEW
- Any tabular plain text

### 2.1 Automatic Column Detection — Complete Logic

PlotIN analyzes both the header and the first data row to determine how to interpret columns as X/Y.

---

## Case 1 — No Header Present
If the first row contains **only numeric values**, PlotIN assumes there is no header.

**Interpretation:**
- First column = **X**
- Remaining columns = **Y1, Y2, Y3…**

Example:
```
0   10   12   14
1   11   13   15
2   12   14   16
```

→ X = col1  
→ Y = col2, col3, col4  

No pair grouping is applied without headers.

---

## Case 2 — Header Present
If headers exist, PlotIN follows **one of two logic paths** depending on the header structure.

---

### Case 2.1 — Pair-Grouping Header Pattern Detected
If headers follow a repeated pairing structure, such as:

```
A*, B*, A*, B*, ...
Left_*, Right_*, Left_*, Right_*, ...
```

→ PlotIN treats columns as **X/Y pairs**:

- (A* = X1, B* = Y1)  
- (next A* = X2, next B* = Y2)  
- etc.

Requirements:
- Columns follow an alternating pattern between two repeating “families” (A*, B*, A*, B*, …)  
- Total column count is even  
- Naming pattern is consistent across the row  

---

### Case 2.2 — Header Does NOT Match Pair Pattern

Examples:
```
A_1, B_7, B
Voltage, Current, Power
Time, Ch1, Ch2
```

→ PlotIN applies classic logic:
- First column = **X**
- All remaining columns = **Y**

---

## 3. Preview Rendering Engine

### 3.1 Auto-Preview
Automatic preview is generated ~200 ms after each change.

### 3.2 Automatic Scaling
PlotIN automatically:
- computes ideal axis limits  
- generates clean, mathematically reasonable tick spacing  
- avoids cluttered decimal formatting  
- maximizes the visible plotting area  

### 3.3 Layout Stability
During preview and export:
- legend position remains stable  
- axes do not shift  
- export uses a “frozen layout” for perfect fidelity  

---

## 4. Graph Navigation

PlotIN provides two main interactive tools: **Pan** and **Zoom to rectangle**.

To ensure cross‑platform consistency, all references use **primary click** and **secondary click** (see macOS note at the end).

---

### 4.1 Zoom Tool – “Zoom to rectangle”
When the zoom tool is active:

- **Primary click + drag** → draw a rectangle to zoom into that region  
- Axis lock modifiers (X/Y) may keep one axis fixed when applicable  

This is standard rectangular zooming.

---

### 4.2 Pan Tool – move and directional zoom
When the pan tool is active:

- **Primary click + drag** → pan (move) the plot  
- **Secondary click + drag horizontally** → zoom only on the **X axis**  
- **Secondary click + drag vertically** → zoom only on the **Y axis**  

This enables fast repositioning and precise axis‑specific zooming.

---

### 4.3 Navigation History
- **Back / Forward** buttons undo/redo pan and zoom changes  

---

### 4.4 Home Reset
Two modes:

**Short press:**  
- returns to auto‑computed view from the initial rendering  
- preserves styles and user adjustments  

**Long press (3 seconds):**  
- full reset  
- restores the exact first‑plot view, ignoring manual changes  

---

## 5. Legend System

### 5.1 Move the Legend
- Hover → primary click + drag  
- Stored in normalized axes space for stable repositioning  

### 5.2 Resize the Legend
- Control/command + drag  

### 5.3 Rename Series
- Double‑click on legend text  
- Supports LaTeX/MathText  
- Syncs with the Individual tab  

### 5.4 Boundary Locking
Legend cannot be dragged outside the plot area.

---

## 6. Global Styling (General Tab)

You can adjust all series simultaneously:

- Line types: solid, dashed, dotted, dash‑dot, markers, line+markers, bars  
- Color palettes: Bright, Soft  
- Grid types: none, solid, dashed, dotted  
- Curve modes: raw, smooth (spline‑like)  
- Axis scales: linear, log, symlog  

---

## 7. Per-Series Styling (Individual Tab)

Each series can override:
- Color  
- Marker type  
- Line width  
- Line style  
- Label (LaTeX supported)

---

## 8. Axes and Tick Control

### 8.1 Axis Visibility
Enable/disable:
- bottom, top, left, right axes  

### 8.2 Centered Axes (Crosshair Mode)
- Axes pass through zero  
- Arrowheads added  
- Smart placement based on data  

### 8.3 Tick Options
- Show/hide major & minor ticks  
- Control major tick count  
- Control minor ticks per interval  
- Clean decimal spacing  

### 8.4 Manual Limits
Allows partial or full:
- xmin/xmax  
- ymin/ymax  

Invalid input is ignored safely.

---

## 9. Smooth Mode
Spline‑like interpolation:
- smooth continuous appearance  
- avoids artificial overshoot  
- preserves monotonic transitions  

---

## 10. Bars Mode
- X is replaced by index (0..N‑1)  
- Bar labels derived from headers  
- Automatic spacing  

---

## 11. Export System

PlotIN exports four formats at once:

- **SVG** (vector)  
- **PDF** (vector)  
- **PNG** (raster)  
- **EMF** (vector, requires Inkscape)  

### EMF Export — Mandatory Inkscape Requirement

PlotIN uses **only Inkscape** to convert SVG → EMF.

- **Windows:** Inkscape must be installed and accessible in PATH  
- **macOS:** Inkscape must exist at:  
  `/Applications/Inkscape.app/Contents/MacOS/inkscape`

Download: https://inkscape.org/release/

### Individual Saves
Any format can also be saved manually.

---

## 12. LaTeX / MathText Support

Examples:
- `V_{out}`  
- `I_{max}`  
- `\alpha`, `\omega`  
- `$10^{-3}$`  
- `$R_{eq}=\frac{V}{I}$`  

Symbols:
- Greek letters  
- Ohm symbol: `\Omega`  
- Celsius: `\deg C`  

Documentation:  
https://matplotlib.org/stable/tutorials/text/mathtext.html

---

## 13. Advanced Features
- Real‑time coordinate tracking  
- Zoom‑on‑legend (Control/command + scroll)  
- Update/donation notifications  

---

## 14. Recommended Workflow
1. Copy data from Excel  
2. Paste into PlotIN  
3. Auto‑preview appears  
4. Adjust styles & axes  
5. Move/resize legend  
6. Inspect via Pan/Zoom  
7. Press Home  
8. Export  
9. Insert into academic documents  

---

## 15. macOS Interaction Notes

To ensure full compatibility with trackpads and Magic Mouse:

- **Primary click** = default click  
  - one‑finger tap  
  - standard mouse click  

- **Secondary click** = right‑click  
  - two‑finger tap  
  - bottom‑right corner click  
  - or **Control + click**  

All Zoom and Pan interactions described above use **primary/secondary click** logic and work identically across macOS and Windows.

---

## 16. Conclusion
PlotIN generates clean, consistent, publication‑ready plots with minimal effort.

**Copy → Paste → Preview → Adjust → Export.**
