# Syria Displacement and Return Atlas

Settlement-level displacement and return atlas for Syria built with Python, Pandas, GeoPandas and Folium by integrating humanitarian datasets from the International Organization for Migration (IOM) and OpenStreetMap.

This project demonstrates a complete humanitarian GIS workflow, from data validation and settlement matching to interactive web mapping, using real-world population and displacement datasets.

## Project Overview

Humanitarian population indicators and geographic settlement data are often published as separate datasets, making direct spatial analysis difficult.

This project addresses that challenge by integrating population and displacement indicators from the International Organization for Migration (IOM) with settlement geometries from OpenStreetMap through a structured data harmonisation workflow.

The resulting interactive atlas visualises settlement-level information on residents, internally displaced persons (IDPs), returnees and total population, providing a reproducible example of humanitarian geospatial data integration using Python.

## Workflow

The project follows a structured humanitarian geospatial data integration workflow:

1. IOM baseline population data

2. HOT OpenStreetMap settlement data

3. Data cleaning and column standardisation

4. ADM3 PCode validation

5. Settlement name normalisation

6. Settlement matching within common ADM3 areas

7. String similarity scoring

8. Match quality classification

9. HOT settlement geometry integration

10. Geo DataFrame creation

11. High-confidence record selection

12. Interactive Folium atlas

This workflow separates data validation, matching, quality control and mapping into distinct stages, allowing each step to be inspected and reproduced independently.

## Datasets

This project integrates humanitarian population indicators with open-source settlement geometry to create a settlement-level displacement atlas for Syria.

### International Organization for Migration (IOM)

**Dataset**

- Baseline Assessment (April 2026)

**Purpose**

Humanitarian population indicators including:

- Residents
- Internally Displaced Persons (IDPs)
- IDP Returnees
- Total Population

The dataset provides demographic and displacement information but does not include settlement geometries for interactive mapping.

---

### HOT OpenStreetMap (HOTOSM)

**Dataset**

- Populated Places (OpenStreetMap)

**Purpose**

Settlement-level geographic information including:

- Settlement names
- ADM3 administrative codes
- Settlement type
- Point geometry

This dataset provides geographic locations but does not contain humanitarian population indicators.

---

### Administrative Boundaries

**Source**

- HDX OCHA
- Syrian Arab Republic – Subnational Administrative Boundaries

**Purpose**

Administrative validation and map visualisation.

ADM3 administrative codes were used to restrict settlement matching within common administrative areas.

---

### Hydrography

**Source**

- HDX Humanitarian OpenStreetMap Team

**Layers**

- Rivers
- Lakes

These layers provide geographic context for the final interactive atlas.


## Processing Steps

The humanitarian datasets were processed through a reproducible Python workflow consisting of the following stages:

### 1. Data Preparation

- Imported IOM baseline assessment tables
- Imported HOT OpenStreetMap settlement data
- Standardised column names
- Selected relevant population indicators

---

### 2. Data Validation

- Verified ADM3 administrative codes
- Removed incomplete records
- Checked settlement name consistency
- Confirmed common administrative areas between datasets

---

### 3. Settlement Matching

- Normalised settlement names
- Performed settlement matching within shared ADM3 areas
- Calculated string similarity scores
- Assigned match quality categories

---

### 4. Spatial Integration

- Joined validated settlement geometries
- Created a GeoDataFrame (EPSG:4326)
- Prepared spatial attributes for mapping

---

### 5. Interactive Mapping

- Filtered high-confidence matches
- Generated interactive Folium layers
- Added administrative boundaries
- Added rivers and lakes
- Exported the final interactive atlas

## Features

The completed atlas provides the following capabilities:

- Interactive settlement-level visualisation
- Residents, IDPs, IDP Returnees and Total Population layers
- Layer switching using Folium LayerControl
- Administrative boundary overlays
- River and lake overlays for geographic context
- Hover tooltips and interactive pop-up information
- High-confidence settlement matching
- Reproducible humanitarian GIS workflow
- Settlement-level humanitarian data integration

## Technologies

### Programming Language

- Python

### Data Analysis

- Pandas

### Geospatial Analysis

- GeoPandas
- Shapely

### Interactive Mapping

- Folium

### Similarity Analysis

- difflib (SequenceMatcher)

## Techniques Demonstrated

- Data harmonisation across multiple humanitarian datasets
- Column standardisation and schema alignment
- Administrative boundary validation using ADM3 Pcodes
- Settlement name normalisation
- String similarity matching (SequenceMatcher)
- Match quality classification
- Settlement-level data integration
- GeoDataFrame creation
- Coordinate Reference System (EPSG:4326) management
- Interactive web mapping with Folium
- Layer management and visualisation
- Reproducible humanitarian GIS workflow

## Results

The integration workflow successfully combined humanitarian population indicators with settlement-level geographic data to produce an interactive displacement and return atlas for Syria.

### Integration Summary

| Item | Result |
|------|--------:|
| IOM assessment records | ~33,000 |
| HOT OpenStreetMap settlements | ~9,300 |
| Shared ADM3 administrative areas | 268 |
| High-confidence matched settlements | 29.1% of processed records |

### Population Indicators Included

- Residents
- Internally Displaced Persons (IDPs)
- IDP Returnees (from December 2024)
- Total Population

### Atlas Outputs

- Interactive Folium web atlas
- Settlement-level humanitarian visualisation
- Layer switching for four population indicators
- Administrative boundary overlays
- River and lake overlays
- Hover tooltips and pop-up information

The project demonstrates that independent humanitarian and geographic datasets can be integrated into a reproducible settlement-level GIS workflow through systematic validation, data harmonisation and quality-controlled matching.

## Future Development

This atlas represents the first stage of a broader humanitarian geospatial analysis framework for Syria.

Future developments may include:

- Integration of additional humanitarian assessment datasets
- Time-series analysis of displacement and return trends
- Multi-source humanitarian data integration
- Climate hazard and displacement interaction analysis
- Automated data update workflows
- Expansion to additional humanitarian indicators

The workflow developed in this project provides a reproducible foundation for future humanitarian GIS analyses.

## Closing Statement

This project demonstrates how independent humanitarian datasets can be transformed into reproducible geospatial information through systematic validation, integration and interactive mapping.

The atlas was developed as part of a continuing effort to apply open-source geospatial technologies to humanitarian analysis and decision support.
