# GNSS Raw Measurements Processing
Created by Nir Meir, Ashraf Hijazi , Abed Massarwa
## Overview

This project focuses on processing GNSS raw measurements from Android devices. It involves parsing GNSS log files, computing positions using a naive RMS (Root Mean Square) algorithm on weighted pseudo-ranges, and converting coordinates to Lat, Lon, Alt. The final output includes a CSV file with calculated positions and a KML file for visualization.

## Features

1. Parse GNSS log files to extract raw measurements.
2. Calculate positions using a naive RMS algorithm.
3. Convert ECEF coordinates (X, Y, Z) to Lat, Lon, Alt.
4. Generate a CSV file with calculated positions.
5. Generate a KML file for visualization.

## Requirements

- Python 3.x
- Pandas
- Numpy
- Matplotlib
- Navpy
- LXML
- Pykml
- GNSSutils (local module)

## Installation

Install the required Python packages using pip:

```bash
pip install pandas numpy matplotlib navpy lxml pykml

## How to run
1. Install the necessary dependencies.
2. Run the Jupyter notebook `EX0.ipynb` and follow the steps.

