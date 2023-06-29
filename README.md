# Amsterdam Internships - Predicting the Deformation of Quay Walls in Amsterdam

This repository containts code for my master's thesis project. The project aims to predict the deformation of quay walls in Amsterdam using soil and satellite data. The soil data contains information on the subsurface of the quay wall, whereas the satellite data provides the subsidence of the ground. The target variable is the tacheometry data of the quay walls, measuring deformation in x, y, and z direction. The predictions will be done with different configurations of BiLSTM models, conforming to early, incremental, and late model fusion.

---

## Project Structure

- EploratoryDataAnalysis.ipynb contains the EDA on all data except for the satellite data.
- LoadMeetbouten.ipynb contains the loading functions and some preprocessing for the building tacheometry data. It yields a preprocessed csv. This was not further used in the project.
- Load_satellite.ipynb contains the loading functions, EDA, and preprocessing for the satellite data. It stores three preprocessed csv for horizontal, vertical and hinterland settlemen in the end. - currently unavailable due to confidential data concerns.
- LoadSoil.ipynb takes input of the XML files obtained through BROLoket: https://www.broloket.nl/ondergrondgegevens. Some minor preprocessing is done. The data is stored in CPT.csv for the CPT data and Bore.csv for the Bore data.
- LoadTacheometry.ipynb loads the tacheometry data from a map containing csv-files for every rack. These files can be downloaded from AIP: https://aip.amsterdam.nl/surveys/map. Some preprocessing is done. The data is stored in three ways:
    tacheometry.csv - contains the columns in shape X{i}, Y{i}, Z{i}, initial idea for structure.
    tacheometry_raw.csv - contains the columns in shape X{date}, Y{date}, Z{date}, for interpolation purposes.
    tacheometry_vis.csv - only contains the object ids and their coordinate, for visualization purposes.
- prepare_cpt.ipynb prepares the CPT data to serve as input for the models. The notebook takes input from CPT.csv, outputted by LoadSoil.ipynb. This notebook determines the overlap between the tacheometry and the CPT data, and creates features. It outputs CPT_train_v2.csv.
- prepare_tcmt.ipynb prepares the tacheometry data to serve as input for the models. The notebook takes input from tacheometry_raw.csv, outputted by LoadTacheometry.ipynb. This notebook mainly removes outliers, aggregates the data per month, and interpolates for missing months. It outputs a csv file for X, Y, and Z.
- Train.ipynb contains functions to train and validate the models. It also contains the experiments and their results.
- Evaluation.ipynb contains the functions to test the models. It also contains the results on the test set.
- ARK validation contains the code to produce the ARK risk category map.

## Installation

For this project, Python 3.9.7 was used.

1) Clone this repository:
    ```bash
    git clone https://github.com/Amsterdam-Internships/QuayWallDeformation/
    ```

2) Install all dependencies:
    ```bash
    pip install -r requirements.txt
    ```
---

## Usage

Explain example usage, possible arguments, etc. E.g.:
To load the data, run notebooks LoadSoil.ipynb, Load_satellite.ipynb, and LoadTacheometry.ipynb.
To preprocess the data, run notebooks prepare_tcmt.ipynb and prepare_cpt.ipynb.
To train, run notebook Train.ipynb
