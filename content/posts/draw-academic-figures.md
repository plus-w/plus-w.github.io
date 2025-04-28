+++
title = 'Draw Academic Figures'
date = 2025-04-28T18:27:57+08:00
draft = true
+++

From Gemini 2.5 Pro:

The Single Most Important Rule:

ALWAYS consult the specific "Guide for Authors" or "Figure Preparation Guidelines" for the target journal. Nature, Science, Cell, and others have detailed requirements regarding figure sizing, resolution, file formats, fonts, line weights, and sometimes even color palettes. What follows are general best practices, but the journal's instructions are paramount.

I. Creating Data Figures with Python (for Nature/Science Quality)

1. Choosing the Right Libraries:

- Matplotlib: The foundational library. It provides complete control over every aspect of your figure. You'll almost always use it, even if indirectly. Its object-oriented API is powerful for fine-tuning.
- Seaborn: Built on top of Matplotlib, Seaborn provides high-level functions for creating aesthetically pleasing and informative statistical plots. It has excellent default styles and color palettes often suitable for publications. It simplifies complex visualizations (e.g., violin plots, heatmaps, regression plots).
- Plotly: Known for interactive plots, but can export high-quality static images (vector or raster). Less common for direct submission to traditional print journals unless interactivity is specifically desired for online versions, but excellent for exploration and web supplementary.
- (Optional) plotnine: An implementation of the Grammar of Graphics in Python (like R's ggplot2). If you're familiar with ggplot2, this can be a good choice.

Recommendation: Use Matplotlib for fine-grained control and Seaborn for high-level plotting and aesthetics. Often, you'll use Seaborn to generate the basic plot and then use Matplotlib functions to customize details (axis labels, titles, annotations, layout).

2. Key Considerations & Best Practices:

- Figure Size and Layout:
    - Journals specify column widths (e.g., single column ~89mm, double column ~183mm for Nature). Design your figures with these final dimensions in mind from the start.
    - In Matplotlib: Use fig, ax = plt.subplots(figsize=(width_inches, height_inches)) to set the exact size. Convert mm to inches (1 inch = 25.4 mm).
    - Use plt.tight_layout() or fig.subplots_adjust() to prevent labels/titles from overlapping and ensure efficient use of space. constrained_layout=True in plt.subplots is often a better, more automatic alternative.
- Resolution and File Format:
    - Vector formats (PDF, EPS, SVG): Preferred for plots containing text, lines, and points. They scale infinitely without losing quality. Matplotlib saves easily to these formats (plt.savefig('figure.pdf', dpi=300, bbox_inches='tight')).
    - Raster formats (TIFF, PNG): Suitable for images like photographs or complex heatmaps where vector formats are impractical.
    - Resolution: Minimum 300 DPI for raster images, 600 DPI or higher for line art/text combinations (check journal specs!). Even when saving vector formats, specifying a DPI (like 300) helps rasterize certain elements correctly if needed.
    - Avoid JPEG for scientific figures due to its lossy compression, which degrades quality, especially around sharp lines and text.
- Font Family:
    - Standard choices: Sans-serif fonts like Arial or Helvetica are overwhelmingly common and often required by journals for clarity and simplicity. Calibri is sometimes acceptable.
    - Check Guidelines: Some journals explicitly state required or preferred fonts.
    - Consistency: Use the same font family across all figures in your paper (including those made in PowerPoint/Illustrator).
    - Setting in Matplotlib:
```python
import matplotlib.pyplot as plt
plt.rcParams.update({'font.family': 'sans-serif', 'font.sans-serif': 'Arial'})
# Or for specific elements:
# ax.set_xlabel('X-axis Label', fontname='Arial')
```

- Font Size:
    - Target Final Size: Font size must be legible at the final publication size (single or double column width).
    - General Rule: Aim for a final printed size of 6-8 points for the smallest text elements (axis tick labels, legends, annotations). Axis labels might be slightly larger (e.g., 8-9 points), and titles (if used within the figure panel) maybe 9-10 points. Check journal guidelines, as they may specify minimums.
    - Test: Print your figure at the target size or resize it on screen to check readability.
    - Setting in Matplotlib:

```python
import matplotlib.pyplot as plt
plt.rcParams.update({'font.size': 8}) # Global default
# Or customize specific elements:
# fig, ax = plt.subplots()
# ax.set_xlabel('X-axis Label', fontsize=9)
# ax.set_ylabel('Y-axis Label', fontsize=9)
# ax.tick_params(axis='both', which='major', labelsize=7)
# ax.legend(fontsize=7)
# ax.set_title('Panel Title', fontsize=10)
```

- Colors:
    - Purposeful Use: Use color to distinguish categories or highlight key findings, not just for decoration.
    - Accessibility: Choose colorblind-friendly palettes. Matplotlib's 'viridis', 'plasma', 'inferno', 'magma', 'cividis' are excellent examples. Seaborn's defaults are often good. ColorBrewer palettes (accessible via libraries or websites) are specifically designed for maps and data visualization, considering color blindness.
    - Avoid: Relying only on color (use different markers/linestyles too), overly saturated/bright colors, red/green combinations (problematic for common color blindness).
    - Grayscale Compatibility: Check how your figure looks in grayscale; important distinctions should remain visible.
    - Consistency: Use a consistent color scheme throughout your paper for the same variables/conditions.
- Figure Types & Styles:
    - Choose Appropriately: Use the plot type that best conveys your data story (scatter for correlation, bar for comparison, line for trends, box/violin/histogram for distribution, heatmap for matrices). Avoid misleading plots (e.g., 3D pie charts).
    - Clarity & Simplicity: Avoid "chartjunk" – unnecessary grid lines, backgrounds, borders, excessive ticks, or 3D effects. A clean, minimalist style is usually preferred.
    - Matplotlib/Seaborn Styles: plt.style.use() can apply pre-defined styles (e.g., seaborn-v0_8-whitegrid, seaborn-v0_8-ticks, classic). Often, starting with a clean style like seaborn-v0_8-ticks or classic and then customizing is effective.
    - Line Weights & Markers: Ensure lines and markers are clearly visible but not overly thick. Typical line weights might be 0.75-1.5 points. Markers should be distinct if used for different groups.
- Labels, Legends, Annotations:
    - Clear Labels: Label all axes clearly, including units (e.g., "Concentration (μM)").
    - Informative Legends: Clearly identify all elements (lines, points, bars). Place the legend where it doesn't obscure data (use loc='best' or manually place). Consider removing the legend box frame (frameon=False).
    - Annotations: Use arrows or lines to point out specific features of interest directly on the plot if needed.

II. Creating Non-Data Figures (Conceptual, Schematics) with PowerPoint

While dedicated vector graphics software like Adobe Illustrator, Inkscape (free & open-source), or Affinity Designer is strongly recommended for professional-quality schematics (better control, vector export), you can use PowerPoint if necessary, but be careful.

1. Best Practices for PowerPoint:

- Consistency is Key: Match the font family (e.g., Arial, Helvetica) and aim for similar final font sizes (e.g., 6-8pt minimum) as your data figures. Use PowerPoint's font size settings accordingly.
- Page Setup/Slide Size: Set the slide size to roughly match the target print dimensions (e.g., set custom size to 183mm width for a double column figure). This helps you visualize the final layout and text sizes more accurately. Do not just use the default 16:9 slide.
- Use Alignment Tools: Ensure elements are precisely aligned using PowerPoint's alignment and distribution tools for a professional look.
- Keep it Simple: Avoid PowerPoint's flashy effects (shadows, glows, complex gradients, 3D rotations) unless absolutely necessary for clarity. Clean lines and shapes are better.
- Grouping: Group related objects together so they can be moved or resized as a unit.
- Color Palette: Use the same color palette as your data figures if applicable (e.g., representing the same molecules or conditions). Ensure colors are colorblind-friendly.
- Exporting - CRITICAL STEP:
    - Do NOT just "Save As Picture": Default export resolutions are often too low.
    - Option 1: Save As PDF: Go to File -> Save As or File -> Export and choose PDF. This often preserves vector elements (text, shapes) if done correctly. Check the PDF quality afterwards.
    - Option 2: Export as High-Resolution Raster (TIFF): Go to File -> Export -> Change File Type -> TIFF. Before saving, you might need to adjust PowerPoint's export resolution settings (this sometimes requires a Windows Registry edit - search online for "PowerPoint export resolution"). Aim for at least 300 DPI, preferably 600 DPI.
    - Option 3 (Better): Copy/paste elements from PowerPoint into vector graphics software (Illustrator, Inkscape) and finalize/export from there. Compatibility can vary.
- Check Final File: Open the exported file (PDF, TIFF) and zoom in significantly to check for pixelation (raster) or clean lines (vector). Ensure text is sharp and readable.

III. Summary & Final Checks

1. Guidelines First: Read the target journal's author guidelines for figures.
2. Consistency: Maintain uniformity in font, size, colors, and style across all figures.
3. Clarity & Readability: Ensure everything is legible and understandable at the final print size. Avoid clutter.
4. Appropriate Tools: Use Matplotlib/Seaborn for data, preferably vector graphics software (Illustrator/Inkscape) for schematics. Use PowerPoint cautiously with proper export settings if it's the only option.
5. Correct Formats & Resolution: Use vector formats (PDF, EPS) when possible, or high-resolution raster formats (TIFF, PNG at 300-600+ DPI).
6. Accessibility: Use colorblind-friendly palettes and don't rely solely on color.
7. Iterate & Get Feedback: Creating good figures takes practice. Show drafts to colleagues and revise based on feedback.