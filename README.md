# QGIS Geoscience & Environmental Portfolio

A collection of GIS projects demonstrating spatial analysis skills across oil & gas, environmental science, and geohazard assessment domains. Built using QGIS with publicly available datasets.

## Projects

### Project 1: Permian Basin Oil & Gas Well Mapping
Mapping and classification of oil and gas well locations in the Texas Permian Basin using Texas Railroad Commission data. Wells are classified by type (oil, gas, injection, dry hole) and overlaid on geological context layers.

**Skills:** Shapefile handling, CRS management, categorized symbology, attribute filtering, professional map composition

**Data Sources:** Texas Railroad Commission, US Census TIGER/Line, USGS National Map

---

### Project 2: EPA Superfund Site Environmental Risk Analysis
Spatial risk assessment of EPA Superfund (NPL) contamination sites, incorporating buffer analysis, water body proximity, and population exposure mapping.

**Skills:** Buffer/proximity analysis, spatial joins, multi-layer overlay analysis, demographic data integration, environmental risk assessment

**Data Sources:** EPA/SEDAC Superfund Footprints, USGS National Hydrography Dataset, US Census Bureau

---

### Project 3: USGS Earthquake Seismic Hazard Visualization
Global earthquake catalog visualization showing magnitude distribution, depth patterns, and seismic density using USGS data. Includes tectonic plate boundary context and multi-panel map layouts.

**Skills:** CSV-to-spatial conversion, graduated/proportional symbols, heatmap analysis, multi-panel layouts, global-scale dataset handling

**Data Sources:** USGS Earthquake Hazards Program, Natural Earth Data, Tectonic Plates (Hugo Ahlenius)

---

## Repository Structure

```
QGIS_Portfolio/
├── README.md
├── QGIS_Portfolio_Project_Guide.md
├── Project1_Well_Mapping/
│   ├── data/          # Source shapefiles and rasters
│   ├── output/        # Processed/derived data
│   └── maps/          # Exported map images and PDFs
├── Project2_Superfund_Analysis/
│   ├── data/
│   ├── output/
│   └── maps/
├── Project3_Earthquake_Viz/
│   ├── data/
│   ├── output/
│   └── maps/
└── Portfolio_Final/
    └── maps/          # Final polished portfolio maps
```

## Tools & Software
- **QGIS 3.x** (free, open-source GIS)
- **Plugins:** QuickMapServices, DataPlotly
- **Data formats:** Shapefile (.shp), GeoJSON, CSV, GeoTIFF

## Data Sources

All data used in these projects is publicly available:

| Source | URL |
|--------|-----|
| Texas Railroad Commission | https://www.rrc.texas.gov/resource-center/research/data-sets-available-for-download/ |
| US Census TIGER/Line | https://www.census.gov/geographies/mapping-files.html |
| USGS National Map | https://www.usgs.gov/the-national-map-data-delivery/gis-data-download |
| EPA Geospatial Data | https://www.epa.gov/frs/geospatial-data-download-service |
| SEDAC Superfund Footprints | https://sedac.ciesin.columbia.edu/data/collection/superfund |
| USGS Earthquake Catalog | https://earthquake.usgs.gov/earthquakes/search/ |
| Natural Earth Data | https://www.naturalearthdata.com/downloads/ |
| Tectonic Plates | https://github.com/fraxen/tectonicplates |

## Author

**Israel Aina (Ayodeji Aina)**
Production Geologist | Technical Data Management | GIS & Geospatial Analysis

## License

This project is licensed under the MIT License. Data files are subject to their respective source licenses.
