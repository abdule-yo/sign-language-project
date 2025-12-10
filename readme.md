````markdown
# MSL Recognition Model Training: Setup Guide

This document outlines the necessary steps for accessing the shared dataset and stabilizing the Google Colab environment to successfully run the `Sign_Language_Model.ipynb` notebook. **This is critical for all group members, especially the AI Engineer and Data Preprocessing Officer.**

---

## 1. 📂 Shared Dataset Access (MANDATORY)

The entire project's data (raw videos and processed landmark files) is stored in a shared Google Drive folder (e.g., `MSL_Project`). You must add a shortcut to this folder for Colab to find the data.

### **ACTION: Add Shortcut to My Drive**

1.  Open your Google Drive in a web browser.
2.  Navigate to **"Shared with me"** on the left sidebar.
3.  Locate the main project folder (e.g., **`MSL_Project`** or **`BIM`**).
4.  **Right-click** the folder and select **Organize** -> **Add shortcut**.
5.  Place the shortcut directly into your top-level **"My Drive"** folder. The correct path for Colab will be `/content/drive/MyDrive/MSL_Project`.

---

## 2. ⚙️ Colab Environment Stabilization

You must install specific versions of `mediapipe` and `numpy` to avoid internal dependency errors.

### **ACTION 2.1: Install Dependencies**

Run the following commands in a **new code cell** at the beginning of your notebook:

```python
# 1. Install required mediapipe version to fix internal NameError
!pip install mediapipe==0.10.21

# 2. Force the compatible numpy version (1.26.4) to resolve conflicts
!pip install numpy==1.26.4 --force-reinstall
```
````

### **ACTION 2.2: Restart Runtime (CRITICAL STEP)**

After the installation completes, you **must** reset the Python session to load the new library versions:

1.  Go to the Colab menu bar.
2.  Click **Runtime** -\> **Restart session**.

---

## 3\. ☁️ Google Drive Mounting

After restarting the runtime, you must re-mount your Google Drive.

### **ACTION: Mount Drive**

Run the following code in the next cell:

```python
from google.colab import drive
drive.mount('/content/drive')
```

_Follow the prompts and click the link to authorize access._

---

## 4\. 📝 Verify File Paths

The notebook requires correct paths to your data. Locate the setup cell in the notebook (after the imports) and ensure the paths point to your newly created shortcut.

### **ACTION: Confirm Path Variables**

Verify that your primary path variables correctly point to the mounted shortcut:

```python
import os

# Example paths to confirm (adjust 'BIM' or 'MSL_Project' if your folder name is different)
DATA_PATH = os.path.join('/content/drive/MyDrive/MSL_Project/train_dataset')
# OR: DATA_PATH = os.path.join('/content/drive/MyDrive/MSL_Project/processed_data')

# Example of a video input path
# VIDEO_PATH = os.path.join('/content/drive/MyDrive/MSL_Project/videos')
```

Once all steps are complete, you can proceed to execute the **Data Acquisition/Pre-processing** loops and the **Model Training** sections of the notebook.

```

```
