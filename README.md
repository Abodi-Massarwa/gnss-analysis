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

This approach ensures the notebook runs on any computer without requiring changes to file paths, as long as the directory structure is maintained.

1. Ensure your GNSS log file is located in the appropriate directory (e.g., `data/input_files/Driving/`).
2. The notebook uses relative paths to locate the input file and save the output files.

### Running the Jupyter Notebook

1. Clone the repository:

    ```sh
    git clone https://github.com/your_username/gnss-analysis.git
    cd gnss-analysis
    ```

2. Install the required Python packages:

    ```sh
    pip install -r requirements.txt
    ```

3. Start the Jupyter notebook server:

    ```sh
    jupyter notebook
    ```

4. Open the `EX0.ipynb` notebook and follow the steps to run the code cells.

### Example of Setting File Paths in the Main Function

In your Jupyter notebook, you can set the file paths within the `main` function to ensure they are relative. Here’s an example of how to do this:

```python
import os

def main():
    try:
        base_dir = os.path.dirname(os.path.abspath(__file__))  # Get the directory of the script
    except NameError:
        base_dir = os.getcwd()  # Fallback to current working directory

    # Insert relative path of each file
    input_filepath = os.path.join(base_dir, 'data/input_files/Driving/gnss_log_2024_04_13_19_53_33.txt')
    output_csv = os.path.join(base_dir, 'data/output_parsed_files/csv/calculated_position_driving.csv')
    output_kml = os.path.join(base_dir, 'data/output_parsed_files/kml/KML_driving.kml')

    measurements, android_fixes_df = parse_log_file(input_filepath)
    process_timestamps(measurements)
    calculate_pseudoranges(measurements)
    ecef_array, rms_list, sv_positions, measurements_filtered = process_epochs_rms(measurements)
    save_to_csv(ecef_array, measurements_filtered, sv_positions, output_csv)
    lla_array = np.stack(navpy.ecef2lla(ecef_array), axis=1)
    create_kml_file(lla_array, output_kml)

if __name__ == '__main__':
    main()
```

## Output

The notebook generates two output files:
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
├── EX0.ipynb
├── requirements.txt
└── README.md
```

## Contributing

Feel free to contribute to this project by opening issues or submitting pull requests.

## License

This project is licensed under the MIT License.

---

This README now includes a clear example of how to set the file paths within the `main` function, making it more helpful for users to configure and run the notebook on different systems.
