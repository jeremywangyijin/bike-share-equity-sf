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

The analysis integrates transportation, demographic, and spatial datasets:

| Dataset | Description |
|----------|-------------|
| Bay Wheels Station Data | Station locations and dock capacity |
| Bay Wheels Ridership Data | Origin-destination trip patterns |
| U.S. Census ACS 2023 | Socioeconomic characteristics |
| OpenStreetMap | Street network and walking accessibility |

The dataset contains:

- 376 Bay Wheels stations in San Francisco
- Station-level ridership records
- Census tract demographic information
- Street network information


## Methodology

### 1. Network-Based Accessibility Analysis

A pedestrian network was developed to measure realistic walking access to bike share stations.

Accessibility was evaluated using the **Balanced Floating Catchment Area (BFCA)** model, which considers:

- Population demand from Census tracts
- Station supply (number of available docks)
- Walking accessibility between residents and stations

### BFCA Framework

