# Post-Fire Landslide Susceptibility Modeling — Nacimiento, Chile

Post-fire landslide susceptibility assessment for Nacimiento commune, Biobío Region, Chile, combining burn severity, terrain, geology, and land cover into a single weighted overlay model.

## About

This project models landslide susceptibility in Nacimiento commune following the February 2023 "Santa Ana" wildfire, one of Chile's most severe recent fire events. Vegetation loss, root cohesion reduction, and ash-induced soil hydrophobicity following wildfires are well-documented drivers of increased landslide and debris flow susceptibility during the following rainy seasons.

Using a weighted overlay (multicriteria analysis) approach — the appropriate method in the absence of a historical landslide inventory for the study area — four conditioning variables were combined into a single susceptibility index: burn severity (dNBR), slope, geology, and land use/land cover.

This project builds directly on a companion project, [`nacimiento-wildfire-2023`](https://github.com/conimoralesg/nacimiento-wildfire-2023), which mapped the burn severity of the same fire event.

## Key Results

- **Method:** Weighted overlay (multicriteria analysis), with weights informed by landslide susceptibility literature
- **Weights:** Slope (0.35), dNBR (0.30), Geology (0.20), Land Use (0.15)
- **Susceptibility distribution:** Very Low (61.4%), Low (30.2%), Moderate (8.4%), High (0.1%), Very High (0%)
- The absence of "Very High" susceptibility areas indicates that the most extreme conditions across all four variables do not spatially coincide within the study area — a genuine finding of the analysis

## Interactive Map

🔗 [View live interactive map](https://conimoralesg.github.io/nacimiento-landslide-susceptibility/nacimiento_landslide_susceptibility_map.html)

The map displays the final susceptibility classification over an Esri satellite basemap, with five classes ranging from Very Low to Very High.

## Data Sources

- **Burn severity (dNBR):** Sentinel-2 Surface Reflectance (Copernicus/S2_SR_HARMONIZED), pre-fire (Jan 28, 2023) and post-fire (Apr 3, 2023) imagery, via Google Earth Engine
- **Slope:** SRTM Digital Elevation Model, 30m resolution (USGS/SRTMGL1_003)
- **Geology:** GLiM (Global Lithological Map v1.1). Hartmann, J., Moosdorf, N. (2012). *The new global lithological map database GLiM: A representation of rock properties at the Earth surface*. Geochemistry, Geophysics, Geosystems, 13, Q12004. https://doi.org/10.1029/2012GC004370
- **Land use/land cover:** ESA WorldCover v200 (2021), 10m resolution
- **Administrative boundary:** GADM v4.1, level 3 (commune)

## Tools

- Google Earth Engine (Python API)
- geemap
- geopandas
- rasterio
- folium
- numpy / matplotlib

## Methodology Notes & Limitations

- **No historical landslide inventory:** weighted overlay was selected as the appropriate method given the absence of a historical landslide inventory for Nacimiento, which precludes statistical/data-driven approaches (e.g., logistic regression, frequency ratio) and quantitative validation (e.g., AUC) of the resulting susceptibility map.
- **Weights:** derived by synthesizing weight ranges reported across multiple landslide susceptibility studies (general and post-fire literature), rather than adopted from a single study using an identical variable combination.
- **Geology (GLiM) resolution:** GLiM's average mapping scale (~1:3,750,000) is considerably coarser than detailed local geological mapping, which may underrepresent fine-scale lithological heterogeneity within the study area.
- **Road cut slopes not modeled:** artificial road cut slopes (taludes) — geotechnically distinct from natural hillslopes due to their engineered angles, sparse vegetation, and concentrated runoff — are not explicitly modeled, as resolving features only a few meters wide would require a higher-resolution DEM than SRTM (30m).

## Author

Constanza Morales Gajardo
[GitHub](https://github.com/conimoralesg) · [LinkedIn](https://linkedin.com/in/constanzamoralesgajardo)
