# Amsterdam Internships - Predicting the Deformation of Quay Walls in Amsterdam

This repository containts code for my master's thesis project. The project aims to predict the deformation of quay walls in Amsterdam using soil and satellite data. The soil data contains information on the subsurface of the quay wall, whereas the satellite data provides the subsidence of the ground. The target variable is the tacheometry data of the quay walls, measuring deformation in x, y, and z direction. The predictions will be done with different configurations of BiLSTM models, conforming to early, incremental, and late model fusion.

---

## Project Structure

- EploratoryDataAnalysis.ipynb contains the EDA on all data except for the satellite data.
- Load_satellite.ipynb contains the loading functions, EDA, and preprocessing for the satellite data. It stores three preprocessed csv for horizontal, vertical and hinterland settlemen in the end.
- LoadMeetbouten.ipynb contains the loading functions and some preprocessing for the building tacheometry data. It yields a preprocessed csv.
- LoadSoil.ipynb contains the loading functions for the soil data, the data is stored in one csv for CPT data and one for Bore data.
- LoadTacheometry.ipynb contains the loading functions for the quay wall tacheometry data. The data is stored in different formats in different csv's, because of changing my mind on the format. - TO DO: make sure only one format remains and is adjusted everywhere appropriately.
- prepare_cpt.ipynb contains functions to preprocess the CPT data. It outputs a preprocessed csv, ready for the training notebook. - TO DO: combine with loadSoil.ipynb for better overview.
- prepare_tcmt.ipynb contains functions to preprocess the tacheometry data. It outputs a preprocessed csv, ready for the training notebook. - TO DO: combine with LoadTacheometry.ipynb for better overview.
- Train.ipynb contains functions to train and evaluate the data. It also contains the experiments and their results.

## Installation

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
