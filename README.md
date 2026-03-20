# QGIS Geoscience & Environmental Portfolio

This portfolio brings together three GIS projects I built to sharpen my spatial analysis skills and demonstrate how I think about geoscience problems. Each project tackles a different domain -- oil and gas, environmental contamination, and seismic hazard -- but they share a common thread: taking raw geospatial data, asking the right questions, and producing maps that tell a clear story.

I chose QGIS because it is open-source, widely used across both industry and research, and pairs well with Python for data processing. All datasets are publicly available or modeled on public sources so the work is fully reproducible.

## Projects

### [Project 1: Permian Basin Well Mapping](Project1_Well_Mapping/)

I started here because the Permian Basin is where a huge share of US oil production happens, and well data mapping is a bread-and-butter skill for any geoscientist working in E&P. This project maps 4,380 wells classified by type, operator, and target formation, with density analysis to highlight where drilling activity concentrates and why.

**GIS techniques:** Categorized/graduated symbology, heatmap rendering, attribute-based filtering, CSV-to-point conversion, Print Layout composition

![Well Distribution by Type](Project1_Well_Mapping/maps/Map1_Well_Distribution_By_Type.png)

---

### [Project 2: EPA Superfund Environmental Risk Analysis](Project2_Superfund_Analysis/)

I picked New Jersey for this one because it has the highest Superfund site density in the country, which makes the spatial patterns more compelling. The analysis layers contamination sites with buffer zones, water body proximity, and population density to produce a county-level risk score. It is the kind of work that shows up in environmental consulting and remediation planning.

**GIS techniques:** Buffer/proximity analysis, choropleth mapping, spatial overlay, point-in-polygon, composite risk scoring, multi-layer cartographic composition

![Superfund Buffer Zones](Project2_Superfund_Analysis/maps/Map1_Superfund_Buffer_Zones.png)

---

### [Project 3: Global Earthquake Seismic Hazard Visualization](Project3_Earthquake_Viz/)

This project visualizes 2,800 M4.0+ earthquakes (2020-2025) overlaid on tectonic plate boundaries. I wanted to show that I can work at global scale and handle multiple visualization approaches for the same dataset -- magnitude, depth, density, and temporal distribution. The depth map in particular reveals subduction zone geometry in a way that connects directly to plate tectonics theory.

**GIS techniques:** Graduated/proportional symbols, heatmap density, depth classification, temporal visualization, global-scale data handling

![Seismic Heatmap](Project3_Earthquake_Viz/maps/Map3_Seismic_Heatmap.png)

## Tools

- QGIS 3.38 (spatial analysis and cartographic output)
- Python 3 with matplotlib (data processing and visualization)
- Data formats: GeoJSON, CSV, Shapefile

## About Me

**Ayodeji Aina**
Geoscientist | Technical Data Management | Geospatial Analysis

I work at the intersection of subsurface geology, data systems, and spatial analysis. This portfolio reflects both my technical GIS capabilities and my ability to frame geoscience questions in ways that produce actionable insight. If you would like to discuss any of these projects or my approach, feel free to reach out.

## License

MIT License. Data files are subject to their respective source licenses.
