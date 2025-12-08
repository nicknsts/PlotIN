# PlotIN – User Guide

## 1. Introduction
PlotIN is a minimalist, fast, and academically oriented plotting tool designed for scientific and engineering workflows.  
It converts pasted tabular data into clean, publication-ready scientific figures with almost no effort.

The workflow is intentionally simple:

**Copy → Paste → Preview → Adjust → Export**

PlotIN is:

- 💻 **Portable** – runs from a single executable / app image, no installation required  
- 🔐 **Privacy‑friendly** – no accounts, no login, no email, no cloud dependency  
- 🌐 **Fully functional offline**, with optional online enhancements  
- ⚡ **Optimized for speed**, auto‑preview, and intuitive interactions  

---

## 2. Data Input (Copy & Paste)
PlotIN accepts data exclusively via **paste**, directly from a wide range of scientific and engineering tools:

- Microsoft Excel  
- CSV / TSV  
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
- Any plain‑text tabular output  

No import dialogs. No file browsing. **Pasting is the entire input workflow.**

---

## 3. Automatic Column Detection

PlotIN determines X and Y columns based on header presence and pattern structure.

### **Case 1 — No Header Present**
If the first row contains only numeric values:

- First column → **X**  
- Remaining columns → **Y1, Y2, Y3…**

Example:
```
0   10   12   14
1   11   13   15
```

---

### **Case 2 — Header Present**

Two interpretation modes exist:

#### **3.1 Alternating Pair Pattern**
Headers alternate between two repeating families:

```
A*, B*, A*, B*, ...
Left_*, Right_*, Left_*, Right_* ...
Phase*, Magnitude*, Phase*, Magnitude* ...
```

("*" can be any suffix.)

Interpretation:

- A* → X₁, X₂, X₃…  
- B* → Y₁, Y₂, Y₃…  

This is common for multi‑channel or sweep‑based measurement exports.

#### **3.2 Standard Header (No Pair Pattern)**

Examples:
```
Time, Ch1, Ch2
Voltage, Current, Power
A_1, B_7, B
```

Interpretation:

- First column → **X**  
- Remaining columns → **Y**  

---

## 4. Preview Rendering Engine

PlotIN continuously re-renders the preview ~200 ms after any text change.

Features:
- smart autoscaling  
- clean tick spacing  
- removal of noisy decimal precision  
- stable appearance between preview and export  

Exported figures **match exactly** what you see on screen.

---

## 5. Navigation

PlotIN provides intuitive scientific navigation through **Zoom to Rectangle** and **Pan**.

---

### **5.1 Zoom to Rectangle**
With the zoom tool active:

- **Left click + drag** → zooms into the drawn rectangle

---

### **5.2 Pan (Move + Directional Zoom)**

Common features (Windows & macOS):
- **Left click + drag** → pan the visible window  
- **Legend move** → hover legend + left click + drag  

Platform-specific features:

#### **Windows**
- Horizontal zoom → Pan tool + **Right click + horizontal drag**  
- Vertical zoom → Pan tool + **Right click + vertical drag**  
- Legend resize → hover legend + **Ctrl + scroll**

#### **macOS**
- Horizontal zoom → Pan tool + **Secondary click + horizontal drag**  
- Vertical zoom → Pan tool + **Secondary click + vertical drag**  
- Legend resize → hover legend + **Command (⌘) + scroll**

*(Secondary click = two-finger click, ctrl+click, or mouse right‑click.)*

---

## 6. Home Reset

- **Short press** → return to autoscaled view (keeps styling changes)  
- **Long press (~3 seconds)** → full reset to initial plot state  

---

## 7. Legend Interaction

The legend is fully interactive but explained concisely to avoid redundancy:

### **Move Legend**
- hover → left click + drag

### **Resize Legend**
- Windows → **Ctrl + scroll**  
- macOS → **Command (⌘) + scroll**

### **Rename Series**
- double‑click a legend entry  
- accepts full LaTeX/MathText syntax

### **Boundary Locking**
The legend automatically remains inside plot boundaries.

---

## 8. Global Styling

The **General** tab adjusts all series simultaneously:

- Line styles  
- Marker styles  
- Bar mode  
- Color palettes  
- Grid styles  
- Smooth (spline‑like) mode  
- Axis scale: linear / log / symlog  

Advanced per‑series styling (Individual tab) is not included in this edition.

---

## 9. Axes and Ticks

You may control:

- visibility of each axis (bottom/top/left/right)  
- major/minor tick visibility  
- approximate tick count  
- minor ticks per major interval  
- manual axis limits (`xmin`, `xmax`, `ymin`, `ymax`)  

Invalid entries are ignored safely.

Centered axes (crosshair mode) are not part of this edition.

---

## 10. Smooth Mode

Provides visually enhanced, smoother curves without excessive overshoot.  
Ideal for noisy or experimental datasets.

---

## 11. Bars Mode

- X becomes implicit index (0..N–1)  
- labels come from headers  
- automatic spacing and alignment  

---

## 12. Exporting Figures

Supported formats:

- **PNG**  
- **SVG**  
- **PDF**  
- **EMF** (requires Inkscape)

Exports are saved **one format at a time**.

### **Inkscape Requirement for EMF**
PlotIN uses Inkscape for SVG → EMF conversion:

- Windows → In PATH  
- macOS → `/Applications/Inkscape.app/Contents/MacOS/inkscape`

Download: https://inkscape.org/release/

---

## 13. LaTeX / MathText Examples

PlotIN supports a wide range of LaTeX‑style formatting.

### **Basic**
- `V_{out}`, `I_{max}`, `t^{2}`, `10^{-3}`  
- Greek letters: `\alpha`, `\beta`, `\gamma`, `\omega`

### **Intermediate**
- `$R = \frac{V}{I}$`  
- `$P = I^2 R$`  
- `$E = \frac{1}{2} L I^2$`

### **Advanced**
- RMS:
  `$V_\mathrm{RMS} = \frac{V_\mathrm{peak}}{\sqrt{2}}$`
- Transfer function:
  `$|H(j\omega)| = 20 \log_{10}\left(\frac{V_{out}}{V_{in}}{\right)$`
- Vector notation:
  `\vec{B}`, `\vec{E}`
- Indexed Greek:
  `$I_{\alpha}$`, `$V_{\beta}$`, `$F_{\gamma,1}$`

Full reference:  
https://matplotlib.org/stable/tutorials/text/mathtext.html

---

## 14. Online / Offline Behavior

PlotIN works entirely offline.  
However, **online use is recommended** because:

- the tool can retrieve **update notifications**  
- users may be informed of **fixes and enhancements**  
- documentation links can open automatically

### When offline:
- a small **Offline** button appears  
- after restoring internet, click it to trigger an immediate recheck  
- otherwise, PlotIN automatically attempts reconnection periodically  

No plotting features are restricted in offline mode.

---

## 15. Recommended Workflow

1. Copy data from your tool (Excel, MATLAB, Flux, ANSYS, etc.)  
2. Paste into PlotIN  
3. Preview updates instantly  
4. Adjust styling  
5. Move/resize legend  
6. Zoom/pan for detailed inspection  
7. Reset view with Home  
8. Export your figure  

---

## 16. Conclusion

PlotIN provides a clean, efficient workflow for high‑quality scientific visualization:

**Copy → Paste → Preview → Adjust → Export**

Everything else is handled automatically.
