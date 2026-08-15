# HWTT Analyzer User Manual

## Quick Start

1. Open the `HWTTAnalyzer` folder.
2. Double-click `HWTTAnalyzer.exe`.
3. Choose the source type.
4. Select the input file or Instrotech left/right pair.
5. Choose Metric or U.S. customary display units from `Settings > Units`.
6. Enter optional project details and test temperature.
7. Choose which figure files and Excel workbook sections should be saved.
8. Pick plot colors if needed.
9. Click Analyze.
10. Review Summary, Fit Review, Plots, and exported Excel output.
11. Use `Plot Comparison` to overlay measured or CRD curves from multiple analysis workbooks.

## Input Templates

- `PTI_Equipment_Output_Example.xlsm`: PTI equipment-output example with a `RawData` sheet.
- `Troxler_Equipment_Output_Example.xls`: Troxler equipment-output example with `TEMPSET`, `PASSNUM`, `L4-L8`, and `R4-R8`.
- `Instrotech_LEFT_Equipment_Output_Example.txt` and `Instrotech_RIGHT_Equipment_Output_Example.txt`: paired Instrotech equipment-output examples with `[GRAPH]` data rows.
- `Custom_Excel_Template.xlsx`: simple workbook with `Number of Passes`, `Left Rut Depth (mm)`, `Right Rut Depth (mm)`, and optional `Test Temperature (°C)`.

The equipment examples are sanitized and do not include real project identifiers. All imported files remain metric: rut depth is interpreted as millimeters and temperature as degrees Celsius, regardless of the display-unit setting.

## Batch Folder Analysis

Choose `Auto detect` when one folder contains one or more HWTT input files. The analyzer scans the selected folder for PTI, Troxler, custom Excel, and complete Instrotech left/right pairs, then identifies the supported source type for each case.

- Each recognized workbook is one case; a matched Instrotech left/right pair is one case.
- With multiple cases, every case is written to a separate result subfolder and `HWTT_Batch_Summary.xlsx` is written in the selected output folder.
- If one case fails, the remaining cases continue. Review the batch summary for `Completed` or `Failed` status and the detected file type.
- The progress indicator appears after Analyze is clicked and shows the current batch stage until processing finishes.

## Unit Settings

Use `Settings > Units` to choose `Metric (mm, °C)` or `U.S. customary (in., °F)`. The choice applies to dashboard values, live fit previews, generated plots, project details, and newly exported Excel files. The manual test-temperature field follows the selected unit and is converted to Celsius before analysis.

Changing units after an analysis reruns the last completed configuration and regenerates the enabled outputs. Calculations always remain in canonical millimeters and Celsius, so pass counts, RRI, R-squared, slope ratios, SIP, SN, fit selection, and classifications remain unchanged.

## Standalone Use

Copy the whole `HWTT_Analyzer_Share_Package` folder to another Windows computer, or copy the complete `HWTTAnalyzer` folder inside it. Do not separate `HWTTAnalyzer.exe` from `_internal`.

## Outputs

The app can write PNG plots and an Excel workbook to the selected output folder. Use `Saved Figures` to choose whether to save no figures, selected-fit figures, full 20k figures, selected plus full 20k figures, or all candidate-fit figures. Use `Excel Outputs` to choose whether to save the workbook and which sheets to include.

Simple mode focuses the workbook on the main reporting sheets. Advanced Research mode can include the detailed Fit Windows sheet when selected.

In `Average Rut Depth Data`, measured values stop at the reporting endpoint. Measured cells remain blank after that endpoint, while modeled CRD continues through 20,000 passes. The `Data Region` column identifies measured and `CRD extrapolation` rows.

## Comparing Multiple Runs

Open `Plot Comparison` or choose `Tools > Plot Comparison`.

1. Click `Add Workbooks` to select one or more HWTT output workbooks, or use `Add Current Results` after analysis.
2. Use one row per plotted line. Use `Duplicate Selected Line` when one workbook should provide multiple curves.
3. For each line, choose `Measured rut depth` or `CRD`, then choose `Average`, `Left`, or `Right`.
4. Edit the legend name, line color, and line style.
5. Select one table row. The highlighted row, numbered `Legend Order` column, and `Selected line` banner identify exactly which line will move. Use the arrow-labeled `Move Up` or `Move Down` button to set its legend position. Legend entries follow the numbered table order from top to bottom.
6. Use `Export Excel` to save the Comparison Line Details rows for reuse. Edit the exported workbook if needed, then use `Import Excel` to replace the current line table. The workbook stores only line order, enabled state, source-workbook path, data type, series, legend name, color, and line style; it does not store plot titles, axes, or other plot settings.
7. Customize plot and axis titles, axis limits, depth-axis direction, grid visibility, legend location, and font sizes for the chart title, axis titles, tick labels, and legend.
8. Click `Refresh Preview`, then save the comparison as SVG, PNG, or PDF.

Metric and U.S.-unit output workbooks can be mixed. The app normalizes each workbook from its depth-column header and displays the comparison in the currently selected unit system.

## Help Menu

The Help menu opens documentation and support resources included with the app package:

- `User Manual`: opens the local user manual, using the Word document when available and Markdown as a fallback.
- `Analysis Background`: opens the background documentation for data analysis and modeling.
- `Open Examples Folder`: opens the packaged examples folder.
- `Support Contact`: shows `Morshed Washif Hasan` and `mwhauvi@gmail.com`.
- `About HWTT Analyzer`: summarizes the app purpose and documentation location.
