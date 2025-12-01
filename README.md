#  Route Monitor: Traffic Accident Detection with YOLOv8

This system aims to **automatically detect traffic accidents** from real-time CCTV streams to significantly reduce emergency response times and improve road safety.

---

## 1.  Repository Setup & Environment

The project utilizes Python and the YOLOv8 framework, primarily developed within a **Google Colab** environment for GPU acceleration.

### A. Directory Structure

The repository is organized to separate code, documentation, and local data files:

```text
Route-Monitor-Accident-Detection/
├── data/               # (LOCAL ONLY - Excluded by .gitignore)
├── notebooks/          # Jupyter Notebooks for analysis and training
│   ├── 01_Data_Pipeline_EDA.ipynb
│   └── 02_Baseline_Model_Training.ipynb
├── src/                # Optional: Helper Python scripts
├── dataset.yaml        # YOLOv8 Configuration file
├── .gitignore          # Prevents large files (data/ and runs/) from being committed
└── README.md


## 2.  Data Pipeline & Preprocessing

The project utilizes a dataset ranging from **10,000–30,000 labeled images** sourced from public datasets, CCTV frames, and augmented scenes, all annotated in **YOLO format** (`.txt` + `.jpg`).

### A. Data Preprocessing

1.  **Augmentation:** Various augmentation techniques were applied (e.g., brightness, blur, fog) as detailed in `01_Data_Pipeline_EDA.ipynb` to improve model robustness.
2.  **Train/Validation/Test Split:** To ensure unbiased final evaluation, the initial Validation set was systematically split into dedicated **Test** and **Validation** sets.
3.  **Script Automation:** The script **`src/data_prep.py`** was developed to automate the splitting of the Validation set to create the necessary Test set.

### B. Exploratory Data Analysis (EDA)

EDA was performed to confirm class distribution and object sizing, guiding the choice of the model architecture.



<img width="850" height="475" alt="image" src="https://github.com/user-attachments/assets/f6e0cd13-df09-4b37-a366-8da50513efc9" />




---

## 3.  How to Run the Project (Reproducibility)

Follow these steps to reproduce the environment and run the Baseline Model training:

1.  **Clone the Repository:**
    ```bash
    git clone [Your-Repo-Link]
    cd Route-Monitor-Accident-Detection
    ```
2.  **Install Requirements:** Install all necessary Python dependencies.
    ```bash
    pip install -r requirements.txt
    ```
3.  **Download and Organize Data:** Download the dataset (e.g., from Roboflow) and place the main data folder (e.g., `cctv-accident-4`) inside the **`data/`** directory.
4.  **Prepare the Test Set:** Execute the data preparation script **once** to split the validation data and create the independent Test set.
    ```bash
    python src/data_prep.py
    ```
5.  **Run Training:** Execute the cells sequentially in the Jupyter Notebook **`notebooks/02_Baseline_Model_Training.ipynb`** to load the configuration, train the YOLOv8n model, and view the metrics.

---

## 4.  Baseline Model Performance

The initial model was trained using the simplest and fastest architecture, **YOLOv8 Nano (YOLOv8n)**, for 5 epochs to establish a reliable baseline score.

### A. Results Summary

| Metric | Model | Epochs | Input Size | Score |
| :--- | :--- | :--- | :--- | :--- |
| **mAP@50** | YOLOv8n | 5 | 640 | **0.8660** |

> **Conclusion:** The Mean Average Precision at 50% IoU (**mAP@50**) score of **0.8660** confirms a strong performance for a baseline model, validating the data pipeline and framework selection.

### B. Confusion Matrix

The confusion matrix visually confirms the high accuracy and minimal misclassifications achieved by the baseline.



<img width="3000" height="2250" alt="confusion_matrix" src="https://github.com/user-attachments/assets/b3d777fe-d22e-4629-8a26-568446a83865" />



---

## 5.  Future Work & Next Steps

The project plan includes continuous development focused on achieving higher accuracy and ensuring real-time deployment readiness.

1.  **Model Scaling:** Experiment with larger, more accurate YOLO architectures (e.g., **YOLOv8 Medium** or **Large**) to surpass the current mAP threshold.
2.  **Optimization:** Apply optimization techniques like **Quantization** to reduce the model size and inference time, which is critical for real-time CCTV processing.
3.  **Deployment (Phase II):** Develop a final deployment pipeline using **Docker** for containerization and integrate the model to send real-time alerts to the designated platform (e.g., Android app).
