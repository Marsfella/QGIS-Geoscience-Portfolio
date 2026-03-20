# Project 1: Permian Basin Oil & Gas Well Mapping

## Why This Project

The Permian Basin is the most actively drilled hydrocarbon province in the United States, and understanding well distribution patterns is fundamental to production geology, lease evaluation, and field development planning. I built this project because it mirrors the kind of spatial data work that comes up routinely in E&P roles: loading regulatory well data, classifying wells by type and status, identifying drilling trends by operator and formation, and producing maps that support subsurface decision-making.

The choice to visualize by four different attributes (type, density, operator, formation) is deliberate. Each view answers a different question that a geoscientist or asset team might ask about a basin.

## Data

| Layer | Records | Format | Description |
|-------|---------|--------|-------------|
| Well Locations | 4,380 | GeoJSON | Point data with 14 attributes per well |
| County Boundaries | 17 | GeoJSON | Permian Basin county polygons |
| Basin Outline | 1 | GeoJSON | Permian Basin extent boundary |

Well attributes include: API number, well name, operator, well type (oil/gas/injection/dry hole/plugged), status, county, coordinates, total depth, target formation, spud date, basin, and elevation.

**Data source:** Simulated dataset modeled on real Permian Basin geographic distributions and Texas Railroad Commission (RRC) data patterns. The well type ratios, operator mix, and formation targets are calibrated to reflect actual basin activity. Real data can be downloaded from the [Texas RRC](https://www.rrc.texas.gov/resource-center/research/data-sets-available-for-download/) or [HIFLD Open Data](https://hifld-geoplatform.opendata.arcgis.com/datasets/oil-and-natural-gas-wells/).

## Maps

### Map 1: Well Distribution by Type
The first question in any basin review is "what kind of wells are here?" This map uses categorized symbology with distinct shapes per type -- circles for oil, diamonds for gas, triangles for dual-completion, squares for injection, and cross markers for dry holes and plugged wells. The shape differentiation matters because color alone is insufficient when maps are printed in grayscale or viewed by colorblind reviewers.

![Map 1](maps/Map1_Well_Distribution_By_Type.png)

### Map 2: Well Density Heatmap
Density mapping reveals what point scatter cannot: where drilling activity actually concentrates. The Midland-Ector corridor and Reeves County (Delaware Basin) stand out as primary hotspots, which aligns with the real-world focus on Wolfcamp and Bone Spring horizontal development in those areas. This kind of heatmap is useful for identifying infill drilling opportunities and lease competition.

![Map 2](maps/Map2_Well_Density_Heatmap.png)

### Map 3: Wells by Operator
Operator footprints tell a story about leasehold strategy. The top 6 operators each show geographic clustering that reflects how acreage positions get built -- through acquisition, farmouts, and competitive leasing. In practice, this map helps answer "who are the active players in this area?" which is a question that comes up in joint venture discussions and competitive intelligence.

![Map 3](maps/Map3_Wells_By_Operator.png)

### Map 4: Wells by Target Formation
This is where subsurface geology meets the map. The Wolfcamp (A and B benches), Bone Spring, Spraberry, and San Andres formations each cluster in different geographic areas because the geology changes across the basin. The Wolfcamp dominates the Delaware sub-basin to the west, while the Spraberry and San Andres are more prominent in the Midland sub-basin. A geoscientist looking at this map can immediately connect surface location patterns to subsurface stratigraphy.

![Map 4](maps/Map4_Wells_By_Formation.png)

## How to Reproduce in QGIS

1. Open QGIS 3.x and double-click `Project1_Well_Mapping.qgz` to load the pre-configured project
2. All three layers load with categorized symbology and county labels already applied
3. To modify symbology: right-click a layer > Properties > Symbology
4. To create a Print Layout: Project > New Print Layout, add map frame, legend, scale bar, north arrow
5. Export at 300 DPI via Layout > Export as Image

**Layer styling in the .qgz file:**

| Layer | Renderer | Classification |
|-------|----------|----------------|
| Permian Basin Wells | Categorized | WELL_TYPE field, 6 classes with unique markers |
| County Boundaries | Single symbol | Gray outline, beige fill, bold NAME labels |
| Basin Outline | Single symbol | Dashed brown border, 15% opacity fill |

## GIS Skills Demonstrated

- Loading and managing vector data (GeoJSON, CSV with coordinates)
- Categorized symbology with custom marker shapes and color schemes
- Heatmap/density analysis for spatial pattern identification
- Multi-attribute spatial analysis (type, operator, formation)
- Cartographic composition with legend, scale bar, north arrow, attribution
- CRS management (WGS 84 / EPSG:4326)
- QGIS Print Layout for publication-quality export

## File Structure

```
Project1_Well_Mapping/
  Project1_Well_Mapping.qgz          QGIS 3.38 project (pre-styled)
  data/
    wells/
      permian_basin_wells.geojson     4,380 well points, 14 attributes
    boundaries/
      permian_basin_counties.geojson  17 county polygons
      permian_basin_outline.geojson   Basin extent polygon
  maps/
    Map1_Well_Distribution_By_Type.png
    Map2_Well_Density_Heatmap.png
    Map3_Wells_By_Operator.png
    Map4_Wells_By_Formation.png
```
