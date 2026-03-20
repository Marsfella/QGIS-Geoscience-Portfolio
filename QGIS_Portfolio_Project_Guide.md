# QGIS Portfolio Project Guide
## 3 Projects for Geoscience & Environmental Roles

---

## Overview

This guide walks through 3 portfolio projects designed to demonstrate GIS competency across oil & gas, environmental, and geospatial analysis domains. Each project uses free public data and builds progressively on QGIS skills.

| # | Project | Domain | Key Skills |
|---|---------|--------|------------|
| 1 | Permian Basin Well Data Mapping | Oil & Gas / Subsurface | Shapefile loading, symbology, attribute queries, map composition |
| 2 | EPA Superfund Site Environmental Risk Analysis | Environmental | Spatial analysis, buffer zones, proximity analysis, thematic mapping |
| 3 | USGS Earthquake Seismic Hazard Visualization | Geoscience / Hazards | CSV-to-point conversion, heatmaps, graduated symbols, spatial joins |

---

## Project 1: Permian Basin Oil & Gas Well Data Mapping

### Objective
Create a professional map of oil and gas well locations in the Texas Permian Basin, classified by well type (oil, gas, injection, dry hole), overlaid on geological context layers.

### Data Sources (All Free)

| Dataset | Source | Format | URL |
|---------|--------|--------|-----|
| Texas Well Locations | Texas Railroad Commission | Shapefile (.shp) | https://www.rrc.texas.gov/resource-center/research/data-sets-available-for-download/ |
| US State Boundaries | US Census Bureau TIGER/Line | Shapefile | https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.html |
| Geological Map of Texas | USGS National Map | GeoTIFF / Shapefile | https://www.usgs.gov/the-national-map-data-delivery/gis-data-download |
| County Boundaries (TX) | US Census TIGER/Line | Shapefile | Same as state boundaries |

### Step-by-Step Workflow

**Step 1: Download & Organize Data**
- Download Texas RRC well shapefile from their Data Sets page
- Download Texas county boundaries from Census TIGER/Line
- Create a project folder structure:
  ```
  Project1_Well_Mapping/
  ├── data/
  │   ├── wells/
  │   ├── boundaries/
  │   └── geology/
  ├── output/
  └── project.qgz
  ```

**Step 2: Load Data into QGIS**
- Open QGIS > New Project
- Layer > Add Vector Layer > Browse to each shapefile
- Set CRS to EPSG:4326 (WGS 84) or EPSG:3857 (Web Mercator)

**Step 3: Filter to Permian Basin**
- Use Select by Expression to filter wells to Permian Basin counties (Midland, Ector, Andrews, Loving, Ward, Reeves, Pecos, Crane, Upton, Reagan, etc.)
- Right-click layer > Export > Save Selected Features As... to create a Permian Basin subset

**Step 4: Classify Wells by Type**
- Right-click well layer > Properties > Symbology
- Change from "Single Symbol" to "Categorized"
- Select the well type field (e.g., WELL_TYPE or similar)
- Choose a color ramp: Oil = green, Gas = red, Injection = blue, Dry Hole = gray
- Adjust point size to 1.5-2.0mm

**Step 5: Add Context Layers**
- Add county boundaries with no fill, black outline
- Add labels for county names (Layer Properties > Labels > Single Labels)
- Optionally add a basemap: Web > QuickMapServices > OSM Standard (install QuickMapServices plugin first)

**Step 6: Create Map Layout**
- Project > New Print Layout
- Add Map, Legend, Scale Bar, North Arrow, Title
- Title: "Oil & Gas Well Distribution - Permian Basin, Texas"
- Add data source attribution in a text box
- Export as PNG (300 DPI) and PDF

### Skills Demonstrated
- Shapefile data loading and management
- Coordinate Reference System (CRS) handling
- Attribute-based filtering and selection
- Categorized symbology and classification
- Professional map composition with cartographic elements
- Data from regulatory sources (industry-relevant)

---

## Project 2: EPA Superfund Site Environmental Risk Analysis

### Objective
Map EPA Superfund (NPL) sites in a selected state, perform buffer analysis around contamination sites, and overlay with water bodies and population data to assess environmental risk exposure.

### Data Sources (All Free)

| Dataset | Source | Format | URL |
|---------|--------|--------|-----|
| Superfund Site Boundaries | EPA / SEDAC Columbia | Shapefile | https://sedac.ciesin.columbia.edu/data/collection/superfund |
| EPA FRS Facility Data | EPA Geospatial Download | Shapefile | https://www.epa.gov/frs/geospatial-data-download-service |
| National Hydrography Dataset | USGS NHD | Shapefile/GDB | https://www.usgs.gov/national-hydrography/access-national-hydrography-products |
| Population / Census Tracts | US Census Bureau | Shapefile + CSV | https://data.census.gov and TIGER/Line files |
| State Boundaries | Census TIGER/Line | Shapefile | https://www.census.gov/geographies/mapping-files.html |

### Step-by-Step Workflow

**Step 1: Choose a State and Download Data**
- Pick a state with notable Superfund activity (e.g., New Jersey, California, Texas, Pennsylvania)
- Download Superfund site footprints from SEDAC
- Download state hydrography (rivers, streams, lakes) from USGS NHD
- Download Census tract boundaries and population data

**Step 2: Load and Organize Layers**
- Load all layers into QGIS
- Reproject everything to the same CRS (use a state-appropriate UTM zone for accurate distance calculations, e.g., EPSG:32618 for NJ)

**Step 3: Create Buffer Zones Around Superfund Sites**
- Vector > Geoprocessing Tools > Buffer
- Create 1-mile (1609m) and 3-mile (4827m) buffer zones around each site
- Style buffers with transparent fill and dashed outlines (red for 1-mile, orange for 3-mile)

**Step 4: Identify At-Risk Water Bodies**
- Vector > Analysis Tools > Select by Location
- Select water features that intersect the buffer zones
- Highlight affected water bodies in a contrasting color

**Step 5: Overlay Population Data**
- Join Census population data to Census tract polygons
- Use graduated symbology to show population density
- Run Vector > Analysis > Count Points in Polygon to count Superfund sites per tract

**Step 6: Calculate Risk Score (Optional Advanced Step)**
- Use Field Calculator to create a composite risk score:
  - Distance to nearest Superfund site (inverse)
  - Population within buffer
  - Proximity to water bodies
- Classify tracts as High / Medium / Low risk using the score

**Step 7: Create Professional Map**
- Print Layout with:
  - Main map showing Superfund sites, buffers, water bodies, population density
  - Inset map showing state context
  - Legend, scale bar, north arrow
  - Title: "Environmental Risk Assessment: Superfund Site Proximity Analysis - [State]"
- Export at 300 DPI

### Skills Demonstrated
- Buffer analysis (proximity analysis)
- Spatial joins and selections
- Multi-layer overlay analysis
- Population/demographic data integration
- Environmental risk assessment methodology
- Advanced cartographic design with inset maps

---

## Project 3: USGS Earthquake Seismic Hazard Visualization

### Objective
Download global earthquake catalog data from USGS, convert CSV to point data, create a multi-layered seismic hazard visualization showing earthquake magnitude, depth, and frequency patterns.

### Data Sources (All Free)

| Dataset | Source | Format | URL |
|---------|--------|--------|-----|
| Earthquake Catalog | USGS Earthquake Hazards | CSV (lat/lon) | https://earthquake.usgs.gov/earthquakes/search/ |
| Tectonic Plate Boundaries | GitHub / Fraxen | GeoJSON | https://github.com/fraxen/tectonicplates |
| World Country Boundaries | Natural Earth | Shapefile | https://www.naturalearthdata.com/downloads/ |
| USGS Fault Lines (US) | USGS | Shapefile | https://www.usgs.gov/programs/earthquake-hazards/faults |

### Step-by-Step Workflow

**Step 1: Download Earthquake Data**
- Go to https://earthquake.usgs.gov/earthquakes/search/
- Set parameters:
  - Date range: Last 5 years (or 2020-2025)
  - Magnitude: 4.0+ (to keep data manageable)
  - Region: Global (or focus on Pacific Ring of Fire, California, etc.)
  - Output: CSV
- Download the CSV file

**Step 2: Import CSV as Point Layer**
- Layer > Add Delimited Text Layer
- Select your CSV file
- Set X field = longitude, Y field = latitude
- Set CRS to EPSG:4326
- This creates a point layer from the earthquake records

**Step 3: Add Context Layers**
- Load tectonic plate boundaries (GeoJSON from GitHub)
- Load Natural Earth country boundaries
- Style plate boundaries as bold red lines
- Style countries with light gray fill, thin borders

**Step 4: Graduated Symbol Map (Magnitude)**
- Open earthquake layer Properties > Symbology
- Choose "Graduated" classification
- Column: magnitude (mag)
- Create classes: 4.0-4.9, 5.0-5.9, 6.0-6.9, 7.0+
- Use graduated circle sizes (small to large) and a warm color ramp (yellow to red)

**Step 5: Create Depth Visualization**
- Duplicate the earthquake layer
- On the copy, use "Graduated" symbology on the depth field
- Use a cool color ramp (light blue = shallow, dark blue/purple = deep)
- This shows subduction zone patterns

**Step 6: Heatmap Layer**
- Duplicate the earthquake layer again
- Change renderer to "Heatmap"
- Set radius to appropriate value (experiment with 50-100km equivalent)
- Weight by magnitude field
- Use a red-yellow color ramp
- This highlights earthquake cluster zones

**Step 7: Create Multi-Panel Map Layout**
- Print Layout with 3 panels:
  - Panel 1: Earthquake locations by magnitude (graduated symbols)
  - Panel 2: Earthquake depth distribution
  - Panel 3: Earthquake density heatmap
- Add overall title: "Global Seismic Hazard Analysis: Earthquake Distribution, Depth & Density (2020-2025)"
- Include legend for each panel, scale bar, data attribution

### Skills Demonstrated
- CSV to spatial data conversion
- Graduated and proportional symbol mapping
- Heatmap / density analysis
- Multi-panel map layouts
- Temporal data handling
- Tectonic/geological context integration
- Working with global-scale datasets

---

## General QGIS Tips for All Projects

### Essential Plugins to Install
Go to Plugins > Manage and Install Plugins:
- **QuickMapServices** - adds basemaps (OSM, satellite, etc.)
- **qgis2web** - export maps to web (optional portfolio enhancement)
- **DataPlotly** - create charts from attribute data

### Export Settings for Portfolio
- Always export maps at **300 DPI** for print quality
- Save as both **PNG** (for web/portfolio) and **PDF** (for documents)
- Use consistent fonts across all maps (Arial or similar sans-serif)

### File Organization
```
QGIS_Portfolio/
├── Project1_Well_Mapping/
│   ├── data/
│   ├── output/
│   └── Project1.qgz
├── Project2_Superfund_Analysis/
│   ├── data/
│   ├── output/
│   └── Project2.qgz
├── Project3_Earthquake_Viz/
│   ├── data/
│   ├── output/
│   └── Project3.qgz
└── Portfolio_Final/
    ├── maps/
    └── QGIS_Portfolio.pdf
```

---

## Next Steps

1. Start with Project 1 (simplest, builds foundational skills)
2. Progress to Project 2 (adds spatial analysis)
3. Finish with Project 3 (most visually impressive)
4. Compile all outputs into a final portfolio PDF

Each project should take 2-4 hours to complete depending on familiarity with QGIS.
