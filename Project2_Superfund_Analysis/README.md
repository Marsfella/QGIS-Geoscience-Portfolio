# Project 2: EPA Superfund Environmental Risk Analysis

## Why This Project

Environmental site assessment is one of the most common applications of GIS in the geosciences, and it sits at the intersection of geology, public health, and regulatory compliance. I chose to focus on New Jersey because it has the highest density of National Priorities List (NPL) sites in the US -- over 100 active and former Superfund sites in a state smaller than most Texas counties. That density makes the spatial relationships between contamination, water, and population especially visible and analytically interesting.

The core question driving this project: "Which communities face the greatest environmental exposure risk, and how do we quantify that spatially?" The answer requires layering multiple datasets -- site locations, buffer zones, hydrography, and demographics -- which is exactly the kind of multi-layer overlay analysis that environmental consultants and regulators do routinely.

## Data

| Layer | Records | Format | Description |
|-------|---------|--------|-------------|
| Superfund Sites | 30 | GeoJSON | NPL site points with HRS score, contaminants, status |
| 1-Mile Buffers | 30 | GeoJSON | Proximity zones around each site |
| 3-Mile Buffers | 30 | GeoJSON | Extended proximity zones |
| Rivers/Streams | 8 | GeoJSON | Major NJ waterways (line features) |
| County Boundaries | 21 | GeoJSON | NJ counties with population and density |
| State Outline | 1 | GeoJSON | NJ state boundary |
| Risk Assessment | 21 | CSV | Composite risk scores per county |

**Data source:** Site locations based on the EPA National Priorities List (public information). Population data based on US Census estimates. For production use, download from [EPA Geospatial Data](https://www.epa.gov/frs/geospatial-data-download-service), [SEDAC Superfund Footprints](https://sedac.ciesin.columbia.edu/data/collection/superfund), and [USGS NHD](https://www.usgs.gov/national-hydrography/access-national-hydrography-products).

## Maps

### Map 1: Superfund Sites with Buffer Zones
The buffer analysis is the foundation of environmental proximity assessment. The 1-mile buffer (red) represents the zone of highest potential groundwater and soil vapor intrusion risk, while the 3-mile buffer (orange) captures the broader area where contaminant plumes might migrate depending on hydrogeology. Marker size scales with the EPA Hazard Ranking System (HRS) score, so sites like Diamond Alkali (dioxin contamination along the Passaic River) stand out visually. The overlap of buffers in northeastern NJ tells its own story about cumulative exposure.

![Map 1](maps/Map1_Superfund_Buffer_Zones.png)

### Map 2: Population Density with Superfund Overlay
This is where the human dimension enters the analysis. The choropleth reveals that the highest contamination concentrations (northeastern NJ around Hudson, Essex, and Bergen counties) overlap almost perfectly with the highest population densities, some exceeding 14,000 people per square mile. That overlap is not coincidental. These are historically industrial areas where decades of manufacturing left behind contaminated sites now surrounded by dense residential development.

![Map 2](maps/Map2_Population_Density_Overlay.png)

### Map 3: Environmental Risk Assessment
The composite risk map synthesizes site count, population density, and water proximity into a single county-level classification. Hudson, Union, and Essex counties score highest, driven by the combination of multiple NPL sites and extreme population density. Southern NJ counties like Cumberland and Salem score lower, not because they lack contamination, but because lower population density reduces the exposure component. In a full production analysis, I would incorporate groundwater flow direction and aquifer vulnerability to refine these scores.

![Map 3](maps/Map3_Risk_Assessment.png)

### Map 4: Water Body Proximity Analysis
Contamination near surface water is especially concerning because rivers and streams serve as both drinking water sources and contaminant transport pathways. Sites within 3 miles of a major waterway (red markers) represent the highest priority for remediation monitoring. Several sites along the Passaic and Delaware rivers fall into this category, which aligns with known real-world contamination issues in those watersheds.

![Map 4](maps/Map4_Water_Proximity.png)

## Risk Scoring Methodology

The composite risk score per county is calculated as:

```
Risk Score = (Superfund Site Count x 25) + (Pop Density / 500) + Noise Factor
```

Classification thresholds: High (> 50), Medium (25-50), Low (< 25)

This is a simplified screening-level approach. In a production environmental assessment, the scoring would incorporate groundwater flow direction, soil permeability, contaminant transport models, aquifer vulnerability indices, and EPA remediation status data. The point here is to demonstrate the GIS methodology, not to produce a regulatory-grade risk assessment.

## How to Reproduce in QGIS

1. Open `Project2_Superfund_Analysis.qgz` in QGIS 3.x
2. Six layers load pre-configured with buffer styling, county labels, and river rendering
3. To perform buffer analysis from scratch: Vector > Geoprocessing > Buffer
4. For choropleth styling: right-click Counties layer > Properties > Symbology > Graduated > POP_DENSITY_SQMI
5. To run Select by Location: Vector > Analysis > Select by Location (select rivers intersecting buffers)

**Layer styling in the .qgz file:**

| Layer | Renderer | Notes |
|-------|----------|-------|
| Superfund Sites | Categorized by STATUS | Active (dark red), Deleted (green), sized 3-3.5mm |
| 1-Mile Buffer | Single symbol | Red fill 25% opacity, dashed outline |
| 3-Mile Buffer | Single symbol | Orange fill 15% opacity, dashed outline |
| Rivers | Single symbol | Steel blue, 1.2mm width |
| Counties | Single + labels | Light gray fill, county NAME labels |
| State Outline | Single symbol | Thin black border, 10% fill |

## GIS Skills Demonstrated

- Buffer analysis (proximity zone generation)
- Choropleth mapping (graduated color by attribute)
- Spatial overlay analysis (multiple layers)
- Point-in-polygon and distance calculations
- Water body proximity assessment
- Composite risk scoring methodology
- Multi-layer cartographic composition
- Environmental domain knowledge (NPL, HRS scores, contaminant media)

## File Structure

```
Project2_Superfund_Analysis/
  Project2_Superfund_Analysis.qgz       QGIS 3.38 project (pre-styled)
  data/
    superfund/
      nj_superfund_sites.geojson        30 NPL sites with attributes
      buffer_1mile.geojson              1-mile proximity polygons
      buffer_3mile.geojson              3-mile proximity polygons
    hydrography/
      nj_rivers.geojson                 8 major NJ waterways
    boundaries/
      nj_counties.geojson               21 counties with population
      nj_state_outline.geojson          State boundary
    census/
      nj_county_risk_assessment.csv     Risk scores per county
  maps/
    Map1_Superfund_Buffer_Zones.png
    Map2_Population_Density_Overlay.png
    Map3_Risk_Assessment.png
    Map4_Water_Proximity.png
```
