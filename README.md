# Assessing Accessibility and Equity of Bay Wheels Bike Share Stations in San Francisco

## Table of Contents

<ol>
  <li><a href="#overview">Overview</a></li>
  <li><a href="#research-questions">Research Questions</a></li>
  <li><a href="#data-sources">Data Sources</a></li>
  <li><a href="#methodology">Methodology</a></li>
</ol>

## Overview

This project evaluates the spatial accessibility and equity of the **Bay Wheels bike share system in San Francisco**.

While bike share provides an affordable and sustainable mobility option, accessibility depends heavily on station locations, walking distance, dock capacity, and integration with surrounding land uses. This study aims to:

- Measure current bike share accessibility across San Francisco
- Identify accessibility disparities across socioeconomic groups
- Develop a data-driven framework for prioritizing future bike station locations

**Key Finding:**  
A GIS-based station siting model identified **10 potential equity-focused bike stations**, improving accessibility by up to **13%** for underserved communities.


## Research Questions

1. How accessible are Bay Wheels stations across different neighborhoods?
2. Do low-income communities experience different levels of bike share accessibility?
3. Where should future stations be located to maximize equity improvements?

## Data Sources

The analysis integrates transportation, demographic, spatial, and points-of-interest (POI) datasets:

| Dataset | Description | Purpose |
|----------|-------------|---------|
| Bay Wheels Station Data | Station locations and dock capacity | Bike share accessibility analysis |
| Bay Wheels Ridership Data | Origin-destination trip patterns | Travel demand and usage analysis |
| U.S. Census ACS 2023 | Socioeconomic characteristics | Equity analysis and demographic evaluation |
| OpenStreetMap | Street network and walking accessibility | Network-based accessibility modeling |
| Registered Business Locations (DataSF) | Business locations across San Francisco | Spatial reference points for accessibility modeling |
| SF Mid Block Points (DataSF) | Street block midpoint locations | Spatial reference points for accessibility modeling |
| Muni Stops - San Francisco (DataSF) | Public transit stop locations | Spatial reference points for accessibility modeling |

The final dataset includes:

- 376 Bay Wheels stations in San Francisco
- Station-level ridership records
- Census tract demographic information
- Street network information
- Points-of-interest (POI) locations including businesses, transit stops and mid-blocks


## Methodology

### 1. Bike Share Network and Demand Flow Analysis

A station-level network was constructed to analyze Bay Wheels user travel patterns and visualize origin-destination (OD) flows across San Francisco.

The network was defined as:

- **Nodes:** 376 Bay Wheels stations in San Francisco
- **Links:** Station pairs connected by at least one recorded trip
- **Edge Weight:** Total number of trips between each station pair

Separate networks were developed for **member** and **casual** users to compare differences in travel behavior and demand patterns.

![Member user OD flow](assets/member_OD_flow.png)

![Casual user OD flow](assets/casual_OD_flow.png)

A dynamic Origin-Destination (OD) flow map was developed at the San Francisco neighborhood level to provide initial insights into:

- Dominant neighborhood-to-neighborhood travel patterns
- Spatial differences between member and casual users
- High-demand corridors and station connections

![OD Flow Map](assets/OD_flow_map.png)


### 2. BFCA Framework

The accessibility scoring system is designed to evaluate each census tract in San Fancisco.

**Balanced Floating Catchment Area (BFCA) Model**

The BFCA model evaluates accessibility by considering both population demand and bike station supply within a given travel time threshold.

Where:

- $P_i$ = population at Census tract $i$
- $S_j$ = supply (number of docks) at station $j$
- $w_{ij}$ = 1 when travel time is smaller than the relevant threshold, otherwise = 0

Step 1: Distribute each tract's population across reachable stations

$$
P_j = \sum_{i=1}^{n} P_i w_{ij}
$$

Step 2: Distribute each station's supply back to all reachable tracts

$$
w_{ij}^{j} = \frac{w_{ij}}{\sum_i w_{ij}}
$$

Step 3: Calculate accessibility for each tract

$$
A_i = \sum_{j=1}^{J}
\frac{S_j w_{ij}^{j}}
{\sum_{i=1}^{n} P_i w_{ij}^{j}}
$$

The accessibility measure satisfies:

$$
\sum_i A_i P_i = \sum_j S_j
$$

### 3. Equity-Based Station Siting Model

A GIS-based suitability model was developed to identify priority locations for future bike stations.

Candidate locations were evaluated using:

### Demand Indicators

- Low-income population percentage
- Existing bike share trip flows

### Accessibility Indicators

- Distance to essential destinations
- Public transit accessibility
- Nearby points of interest (POIs)

A final suitability score was calculated to rank candidate locations.

![Station suitability model](figures/station_suitability.png)


## Results

### Existing Accessibility Gaps

The analysis identified spatial disparities in bike share accessibility across San Francisco.

Key observations:

- Some low-income communities had limited access to bike share stations.
- Several high-demand corridors lacked nearby station access.
- Accessibility gaps were concentrated in specific Census tracts.

![Current accessibility map](figures/current_accessibility.png)


### Proposed Equity Stations

Based on accessibility gaps and demand patterns, **10 equity-focused station locations** were proposed.

The candidate stations were selected based on:

- High transportation demand
- Low existing accessibility
- Strong improvement potential

![Proposed equity stations](figures/proposed_stations.png)


### Accessibility Improvement

After adding the proposed stations:

- Accessibility improved by up to **13%**
- Improvements were concentrated in underserved neighborhoods

![Before and after comparison](figures/accessibility_comparison.png)


## Tools & Technologies

### Programming

- Python
  - Data processing
  - Network analysis
  - Statistical modeling

### GIS

- ArcGIS
- QGIS

### Analysis Methods

- Network accessibility analysis
- Balanced Floating Catchment Area (BFCA)
- Origin-Destination analysis
- GIS suitability modeling
- Equity-based transportation planning


## Project Structure


