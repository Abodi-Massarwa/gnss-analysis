Sure, I'll update your README to include instructions for handling relative paths and running the script. Here's the modified README:

---

# GNSS Raw Measurements Processing
Created by Nir Meir, Ashraf Hijazi, Abed Massarwa

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
```

## How to Run

### Using Relative Paths

This approach ensures the script runs on any computer without requiring changes to file paths, as long as the directory structure is maintained.

1. Ensure your GNSS log file is located in the appropriate directory (e.g., `data/input_files/Driving/`).
2. The script uses relative paths to locate the input file and save the output files.

### Running the Script

1. Clone the repository:

    ```sh
    git clone https://github.com/your_username/gnss-analysis.git
    cd gnss-analysis
    ```

2. Install the required Python packages:

    ```sh
    pip install -r requirements.txt
    ```

3. Run the script:

    ```sh
    python gnss_analysis.py
    ```

## Example

Here is an example of how to run the script using relative paths:

```sh
$ python gnss_analysis.py
```

## Output

The script generates two output files:
1. **CSV File**: Contains the calculated positions along with satellite information.
2. **KML File**: Can be opened with Google Earth to visualize the computed path.

## Project Structure

```
gnss-analysis/
├── data/
│   ├── input_files/
│   │   └── Driving/
│   │       └── gnss_log_2024_04_13_19_53_33.txt
│   └── output_parsed_files/
│       ├── csv/
│       └── kml/
├── gnss_analysis.py
├── requirements.txt
└── README.md
```

## Contributing

Feel free to contribute to this project by opening issues or submitting pull requests.

## License

This project is licensed under the MIT License.

---

This README provides clear instructions on how to install dependencies, run the script, and handle file paths, ensuring the project is portable across different systems.
