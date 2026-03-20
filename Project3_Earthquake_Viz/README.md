# Project 3: Global Earthquake Seismic Hazard Visualization

## Objective

Visualize global seismic activity (2020-2025) to reveal spatial patterns in earthquake magnitude, depth, and frequency. The analysis demonstrates how earthquake distribution aligns with tectonic plate boundaries, with the Pacific Ring of Fire dominating as expected. Four distinct visualization approaches highlight different aspects of seismic hazard.

## Data

| Layer | Records | Format | Description |
|-------|---------|--------|-------------|
| Earthquakes | 2,800 | GeoJSON | M4.0+ events with magnitude, depth, time, location |
| Plate Boundaries | 11 | GeoJSON | Convergent, divergent, and transform boundaries |
| World Continents | 6 | GeoJSON | Simplified continent outlines |

**Magnitude distribution:** M4.0-4.9: 2,103 | M5.0-5.9: 556 | M6.0-6.9: 113 | M7.0+: 28

**Data source:** Simulated dataset following Gutenberg-Richter magnitude distribution and real plate boundary geometry. For production use, download from [USGS Earthquake Catalog](https://earthquake.usgs.gov/earthquakes/search/), [tectonic plates GeoJSON](https://github.com/fraxen/tectonicplates), and [Natural Earth Data](https://www.naturalearthdata.com/downloads/).

## Maps

### Map 1: Earthquake Distribution by Magnitude
Graduated symbol map where marker size and color scale with earthquake magnitude. The Ring of Fire, Alpine-Himalayan Belt, and Mid-Atlantic Ridge are clearly delineated by seismic activity.

![Map 1](maps/Map1_Earthquake_Magnitude.png)

### Map 2: Earthquake Depth Distribution
Depth-coded visualization using the plasma colormap. Shallow events (yellow) cluster along ridges and transform faults, while deep events (purple, 300+ km) trace subduction zones in the western Pacific, consistent with the Wadati-Benioff zone pattern.

![Map 2](maps/Map2_Earthquake_Depth.png)

### Map 3: Seismic Density Heatmap
Kernel density visualization on a dark background highlighting concentration zones. Japan, Indonesia, Chile/Peru, and the Aleutians emerge as the highest-density areas globally.

![Map 3](maps/Map3_Seismic_Heatmap.png)

### Map 4: Temporal Distribution by Year
Year-coded scatter showing consistent seismic activity along plate boundaries from 2020 through 2025. Demonstrates that seismic hazard zones are persistent, not transient.

![Map 4](maps/Map4_Temporal_Distribution.png)

## How to Reproduce in QGIS

1. Open `Project3_Earthquake_Viz.qgz` in QGIS 3.x
2. Three layers load: earthquakes (graduated by magnitude), plate boundaries (categorized by type), continents
3. To switch to depth visualization: right-click Earthquakes > Properties > Symbology > Graduated > change column to `depth_km`
4. To create a heatmap: right-click Earthquakes > Properties > Symbology > change renderer to Heatmap, weight by `mag`
5. For temporal view: use categorized symbology on the `year` field

**Layer styling in the .qgz file:**

| Layer | Renderer | Classification |
|-------|----------|----------------|
| Earthquakes | Graduated | `mag` field, 4 size classes (1.5mm to 6mm) |
| Plate Boundaries | Categorized | Convergent (red), Divergent (green), Transform (orange) |
| Continents | Single symbol | Gray fill, 40% opacity |

## GIS Skills Demonstrated

- CSV/GeoJSON to point layer conversion
- Graduated (proportional) symbol mapping
- Heatmap/kernel density rendering
- Categorized line symbology
- Multi-attribute visualization (magnitude, depth, time)
- Global-scale dataset handling (2,800+ features)
- Tectonic and seismological context integration
- Publication-quality cartographic output

## File Structure

```
Project3_Earthquake_Viz/
  Project3_Earthquake_Viz.qgz               QGIS 3.38 project (pre-styled)
  data/
    earthquakes/
      global_earthquakes_2020_2025.geojson   2,800 M4+ events (2020-2025)
    tectonic_plates/
      plate_boundaries.geojson               11 major plate boundaries
    boundaries/
      world_continents.geojson               6 simplified continent outlines
  maps/
    Map1_Earthquake_Magnitude.png
    Map2_Earthquake_Depth.png
    Map3_Seismic_Heatmap.png
    Map4_Temporal_Distribution.png
```
