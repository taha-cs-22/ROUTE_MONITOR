# 🚨 Route Monitor: Traffic Accident Detection with YOLOv8

This system aims to **automatically detect traffic accidents** from real-time CCTV streams to significantly reduce emergency response times and improve road safety.

---

## 1. ⚙️ Repository Setup & Environment

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
