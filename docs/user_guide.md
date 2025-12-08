# PlotIN – User Guide

## 1. Introduction
PlotIN is a minimalist, fast, and academically oriented plotting tool designed for scientific and engineering workflows.  
It converts pasted tabular data into clean, publication-ready scientific figures with very little effort.

The workflow is intentionally simple:

**Copy → Paste → Preview → Adjust → Export**

PlotIN is:

- 💻 **Portable** – runs from a single executable / app image, no installation required  
- 🔐 **Privacy-friendly** – no accounts, no login, no email, no cloud dependency  
- 🌐 **Fully functional offline**, with optional online enhancements  
- ⚡ **Optimized for speed**, auto-preview, and intuitive interactions  

At the top of the main window you will also find:

- a **Donate** button (optional support, has no impact on functionality)  
- a **Help** button that opens the online documentation and useful links  

---

## 2. Data Input (Copy & Paste)
PlotIN accepts data exclusively via **paste**, directly from a wide range of scientific and engineering tools:

- Microsoft Excel  
- CSV / TSV files  
- MATLAB  
- Simulink  
- LabVIEW  
- Altair Flux  
- ANSYS (Mechanical, Maxwell, Fluent, Twin Builder, Electronics Desktop…)  
- COMSOL Multiphysics  
- LTspice / PSpice / HSPICE  
- DSpace ControlDesk  
- NI Veristand  
- Keysight / Tektronix oscilloscope & DAQ exports  
- Any plain-text tabular output  

No import dialogs. No file browsing. **Pasting is the entire input workflow.**

The upper text area in the GUI displays the pasted table exactly as PlotIN will interpret it.

---

## 3. Automatic Column Detection

PlotIN determines X and Y columns based on header presence and pattern structure.

### 3.1 Case 1 — No Header Present
If the first row contains only numeric values:

- First column → **X**  
- Remaining columns → **Y1, Y2, Y3…**

Example:
```text
0   10   12   14
1   11   13   15
```

---

### 3.2 Case 2 — Header Present

Two interpretation modes exist:

#### 3.2.1 Alternating Pair Pattern
Headers alternate between two repeating families:

```text
A*, B*, A*, B*, ...
Left_*, Right_*, Left_*, Right_* ...
Phase*, Magnitude*, Phase*, Magnitude* ...
```

("*" can be any suffix.)

Interpretation:

- A* → X₁, X₂, X₃…  
- B* → Y₁, Y₂, Y₃…  

This is common for multi-channel or sweep-based measurement exports.

#### 3.2.2 Standard Header (No Pair Pattern)

Examples:
```text
Time, Ch1, Ch2
Voltage, Current, Power
A_1, B_7, B
```

Interpretation:

- First column → **X**  
- Remaining columns → **Y**  

---

## 4. Preview Rendering Engine

PlotIN continuously re-renders the preview ~200 ms after any change.

Features:
- smart autoscaling  
- clean tick spacing  
- removal of noisy decimal precision  
- stable appearance between preview and export  

Exported figures **match exactly** what you see on screen.

The lower part of the main window contains the live Matplotlib canvas where the preview and the final figure are displayed.

---

## 5. Navigation

PlotIN provides intuitive scientific navigation through **Zoom to Rectangle** and **Pan**, using the Matplotlib-style toolbar above the figure.

---

### 5.1 Zoom to Rectangle
With the zoom tool active:

- **Left click + drag** → zooms into the drawn rectangle

---

### 5.2 Pan (Move + Directional Zoom)

Common behaviour (Windows & macOS):

- **Left click + drag** → pan the visible window  
- **Legend move** → hover legend + left click + drag  

Platform-specific details:

#### Windows
- Horizontal zoom → Pan tool + **Right click + horizontal drag**  
- Vertical zoom → Pan tool + **Right click + vertical drag**  
- Legend resize → hover legend + **Ctrl + scroll**

#### macOS
- Horizontal zoom → Pan tool + **Secondary click + horizontal drag**  
- Vertical zoom → Pan tool + **Secondary click + vertical drag**  
- Legend resize → hover legend + **Command (⌘) + scroll**

*(Secondary click = two-finger click, ctrl+click, or mouse right-click.)*

---

## 6. Home Reset

- **Short press** on Home → return to autoscaled view (keeps styling changes)  
- **Long press (~3 seconds)** → full reset to the initial plot state  

---

## 7. Legend Interaction

The legend is fully interactive:

- **Move** – hover the legend and drag with left click  
- **Resize** – hover the legend and  
  - on Windows: use **Ctrl + scroll**  
  - on macOS: use **Command (⌘) + scroll**  
- **Rename series** – double-click a legend entry and edit the label  
- **Boundary locking** – the legend automatically remains inside the plot area  

LaTeX / MathText syntax is supported in legend labels (see section 13).

---

## 8. Figure Options – General Tab

Clicking the **Figure options** button opens a dialog with two tabs: **General** and **Axes & Ticks**.

The **General** tab shows:

- **Plot type** – solid, markers, line+markers, bars, etc.  
- **Curve shape** – raw (straight lines) or smooth (spline-like)  
- **X scale** – linear / log / symlog  
- **Y scale** – linear / log / symlog  

### 8.1 Axis Ranges (Manual Limits)
Still in the **General** tab:

- **X axis range** – two fields: minimum and maximum X  
- **Y axis range** – two fields: minimum and maximum Y  

These fields allow manual control of axis limits.  
Leaving a field empty lets PlotIN choose the limit automatically. Invalid values are ignored safely.

### 8.2 Axis Titles
Also in the **General** tab:

- **X axis title**  
- **Y axis title**  

Both support LaTeX / MathText notation.

### 8.3 Styling Controls
Remaining controls in the **General** tab:

- **Line width** – global line width for all curves  
- **Color palette** – e.g. “Bright colors”, “Soft colors”  
- **Grid style** – no grid / solid / dashed / dotted  
- **Axis titles font size** – for X/Y labels  
- **Tick labels font size** – for numeric axis ticks  

All these options apply globally to the current figure.

---

## 9. Figure Options – Axes & Ticks Tab

The **Axes & Ticks** tab controls which axes and tick types are visible, plus the target number of ticks.

### 9.1 Axis Visibility

You will see four groups: **X top**, **Y left**, **Y right**, **X bottom**.  
Each group has three checkboxes:

- **Axis** – show or hide the axis line itself  
- **Major ticks** – show or hide major tick marks and labels  
- **Minor ticks** – show or hide minor tick marks  

For example, you can:

- hide the right Y axis completely  
- keep only bottom X axis with major ticks  
- show minor ticks only on the left Y axis, etc.

### 9.2 Tick Counts

The central “Ticks counts” group contains:

- **X major ticks** – target number of major tick locations on X  
- **X minor / interval** – number of minor ticks per X interval  
- **Y major ticks** – target number of major tick locations on Y  
- **Y minor / interval** – number of minor ticks per Y interval  

PlotIN uses these targets to choose mathematically clean and visually readable tick positions.

---

## 10. Smooth Mode

The **Curve shape** option in the General tab provides:

- **raw (straight lines)** – direct connection between data points  
- **smooth** – spline-like interpolation for a visually smoother curve  

Smooth mode is especially useful for noisy or dense data.

---

## 11. Bars Mode

When **Plot type** is set to “bars”:

- X values become implicit indices (0..N–1)  
- Labels are taken from headers where appropriate  
- Bar spacing and width are handled automatically  

---

## 12. Exporting Figures

PlotIN can export the current figure to:

- **PNG** (raster)  
- **SVG** (vector)  
- **PDF** (vector)  
- **EMF** (vector, through Inkscape)
- **Others** 

Exports are saved **one format at a time**, using the save button in the toolbar.

### 12.1 Inkscape Requirement for EMF
PlotIN uses Inkscape to convert SVG → EMF:

- **Windows** – Inkscape must be in the system PATH  
- **macOS** – Inkscape must be at  
  `/Applications/Inkscape.app/Contents/MacOS/inkscape`

Download: https://inkscape.org/release/

If Inkscape is not available, EMF export will not be performed, but other formats remain available.

---

## 13. LaTeX / MathText Examples

PlotIN supports a wide range of LaTeX-style formatting in axis titles and legend labels.

### 13.1 Basic
- `V_{out}`, `I_{max}`, `t^{2}`, `10^{-3}`  
- Greek letters: `\alpha`, `\beta`, `\gamma`, `\omega`

### 13.2 Intermediate
- `$R = \frac{V}{I}$`  
- `$P = I^2 R$`  
- `$E = \frac{1}{2} L I^2$`

### 13.3 Advanced
- RMS:
  `$V_\mathrm{RMS} = \frac{V_\mathrm{peak}}{\sqrt{2}}$`
- Transfer function:
  `$|H(j\omega)| = 20 \log_{10}\left(\frac{V_{out}}{V_{in}}\right)$`
- Vector notation:
  `\vec{B}`, `\vec{E}`
- Indexed Greek:
  `$I_{\alpha}$`, `$V_{\beta}$`, `$F_{\gamma,1}$`

Full reference:  
https://matplotlib.org/stable/tutorials/text/mathtext.html

---

## 14. Online / Offline Behavior

PlotIN works online and offline.  
However, **online use is recommended** because:

- the tool can retrieve **update notifications**  
- you may be informed about **bug fixes and new features**  
- documentation links (Help button) can open directly in the browser  

### When offline:
- a small **Offline** button appears in the GUI  
- after restoring your internet connection, click this button if you want PlotIN to check for updates immediately  
- otherwise, PlotIN will periodically attempt to re-check connectivity automatically  

No plotting features are restricted in offline mode.

---

## 15. Recommended Workflow

1. Copy data from your tool (Excel, MATLAB, Flux, ANSYS, etc.)  
2. Paste into the top text area in PlotIN  
3. Wait for the automatic preview in the lower figure area  
4. Open **Figure options** to adjust General and Axes & Ticks settings  
5. Move and resize the legend as needed  
6. Use Zoom and Pan to inspect details  
7. Reset the view with the Home button  
8. Export your figure in the desired format  

---

## 16. Conclusion

PlotIN provides a clean, efficient workflow for high-quality scientific visualization:

**Copy → Paste → Preview → Adjust → Export**

Everything else is handled automatically.
