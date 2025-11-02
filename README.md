# WORK 2: Classification with Lazy Learning and SVM


## Team Members

* Ricard Garcia - ricard.garcia@estudiantat.upc.edu
* Laia Barcenilla - laia.barcenilla@estudiantat.upc.edu
* Núria Cardona - nuria.cardona@estudiantat.upc.edu
* Antonio Arcas - antonio.arcas@estudiantat.upc.edu


## Project Description

The project compares the performance of lazy learning, such as **k-instance-based learning**, with eager learning, like **Support Vector Machines**, in various classification tasks. We test different configurations for the **Hepatitis** and **Hypothyroid** datasets from the *UCI repository* using different **kIBL similarity metrics and instance reduction techniques**, as well as with **different SVM kernels**. The best machine learning configuration for each dataset is determined with appropriate **statistical validation** in terms of classification accuracy, efficiency, and storage.

## File Structure

Here is an overview of the important files and folders included in the `code` directory:

```plaintext
Code/
│
├── data/
│   ├── hepatitis/                # Original hepatitis 10-fold cross-validation (.arff) files
│   ├── hypothyroid/              # Original hypothyroid 10-fold cross-validation (.arff) files
│   ├── hepatitis_preprocessed/   # Preprocessed hepatitis data folds (.csv)
│   └── hypothyroid_preprocessed/ # Preprocessed hypothyroid data folds (.csv)
│
├── out_kIBL/
│   └── (Contains all experiment outputs for kIBL: .csv reports, .txt configs, and .png plots)
│
├── out_SVM/
│   └── (Contains all experiment outputs for SVM: .csv reports and .txt configs)
│
├── main.py                       # Primary main script to execute the experiments
│
├── kIBLAlgorithm.py              # Core implementation of the k-IBL algorithm
├── fw_KIBLAlgorithm_nuria.py     # Core implementation of the k-IBL algorithm with feature weighting
├── ir_KIBLAlgorithm.py           # Implementation of instance reduction (IB3, MENN, MCNN)
├── svmAlgorithm.py               # Script defining and running the SVM experiments
│
├── preprocessing.py              # Contains functions for data loading and preprocessing
├── statistical_analysis.py       # Script to perform statistical tests on results
├── helper_functions.py           # Utility functions used by other scripts
│
└── requirements.txt              # All required Python packages     
```




## Setup and Installation

Follow these steps to set up the Python environment and install the required dependencies.

1.  **Navigate to the Code Folder**
    Open a terminal and change the directory to the project's `code` folder.
    ```bash
    cd <root_folder_of_project>/Code/
    ```

2.  **Create a Virtual Environment**
    We recommend using a virtual environment to manage dependencies.
    ```bash
    python3 -m venv venv
    ```

3.  **Activate the Virtual Environment**

    * On **macOS / Linux**:
        ```bash
        source venv/bin/activate
        ```
    * On **Windows**:
        ```bash
        .\venv\Scripts\activate
        ```

4.  **Install Required Dependencies**
    Install all packages listed in `requirements.txt`.
    ```bash
    pip install -r requirements.txt
    ```
    Check if dependencies were installed by running `pip list`.

5.  **Close the Virtual Environment**
    ```bash
    deactivate
    ```


## How to Run the Code

Make sure you have completed the previous setup steps.

1.  **Activate the Virtual Environment (if not already active)**
    * On **macOS / Linux**:
        ```bash
        source venv/bin/activate
        ```
    * On **Windows**:
        ```bash
        .\venv\Scripts\activate
        ```

2.  **Run the Main Experiment Script**

    The `main.py` script is designed to run the complete set of experiments for **one** dataset at a time.

    > **IMPORTANT:** Before running, you must configure which dataset to use by **editing the `main.py` file**.
    >
    > 1.  Open `main.py` in a text editor.
    > 2.  Go to the `if __name__ == "__main__":` block (near the end of the file).
    > 3.  Modify the `dataset` variable on this line:
    >
    >     ```python
    >     # Select dataset
    >     dataset = ['hepatitis', 'hypothyroid'][1] # 0 --> hepatitis, 1 --> hypothyroid
    >     ```
    >
    > * To run the **Hepatitis** dataset, change the `[1]` to `[0]`.
    > * To run the **Hypothyroid** dataset, leave it as `[1]`.

    Once the dataset is configured, run the script from your terminal:

    ```bash
    python3 main.py
    ```

    * **What this script does:**
        This single command executes the *entire* experimental pipeline for the selected dataset. This process will take a significant amount of time as it performs a full 10-fold cross-validation. It automatically:
        * Preprocesses the data.
        * Loops through all models (`SVM`, `kIBL`, `kIBL_fw`).
        * Loops through all instance reduction (IR) techniques (`IB3`, `MCNN`, `MENN`, and `None`).
        * Tests all hyperparameter combinations defined in the script for each model.

    * **Expected Output:**
        * The terminal will print progress updates as it runs each model, IR method, and fold.
        * All detailed results, including fold-by-fold metrics, mean accuracies, and the best hyperparameter configurations, will be saved as new `.csv` and `.txt` files inside the `out_SVM/` and `out_kIBL/` directories.

3.  **Deactivate the Virtual Environment**
    Once the script has finished running, you can close the virtual environment.
    ```bash
    deactivate
    ```

## Requirements

```plaintext
contourpy==1.3.3
cycler==0.12.1
fonttools==4.60.0
joblib==1.5.2
kiwisolver==1.4.9
matplotlib==3.10.6
numpy==2.3.3
packaging==25.0
pandas==2.3.2
pillow==11.3.0
pyparsing==3.2.5
python-dateutil==2.9.0.post0
pytz==2025.2
scikit-learn==1.7.2
scipy==1.16.2
scipy-stubs==1.16.2.0
seaborn==0.13.2
six==1.17.0
threadpoolctl==3.6.0
tzdata==2025.2
```
