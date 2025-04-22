
# 👥 Crowd Density Estimation using YOLOv8

<div align="center">
  <img src="Screenshot 2025-04-22 172514.png" alt="Crowd Detection Example" width="60%" />
  <h3>Smart City Monitoring - Real-time Crowd Detection & Density Estimation</h3>
  <p>Automatically count people and visualize crowd levels using deep learning.</p>

  [![Python](https://img.shields.io/badge/Python-3.10-blue?style=flat-square&logo=python)](https://www.python.org/)
  [![YOLOv8](https://img.shields.io/badge/YOLOv8-Ultralytics-red?style=flat-square&logo=ultralytics)](https://github.com/ultralytics/ultralytics)
  </div>

---

## 🧩 Problem Statement

In rapidly urbanizing environments, real-time crowd monitoring is essential for safety, resource allocation, and emergency management. Traditional manual monitoring methods are labor-intensive and inefficient. This project aims to automate **crowd density estimation** using deep learning—detecting and counting people in video feeds and classifying density as **Low**, **Medium**, or **High**.

---

## 📁 Dataset

- **Source**: Custom videos recorded in public places (e.g., shopping malls)
- **Frame Extraction**: 30+ videos processed with OpenCV at `interval = 125`
- **Images**: Over **1000+ frames**
- **Annotations**: YOLOv8 format using Roboflow
- **Classes**:  
  - `0`: Person

```
Crowd Dataset/
├── images/
│   ├── train/
│   └── val/
├── labels/
│   ├── train/
│   └── val/
```

---

## 🧼 Preprocessing Techniques

- 🎞 **Video to Frame Conversion** using OpenCV
- 📐 **Resized Images** to 640×640 for YOLO compatibility
- 🏷 **Labeling** with Roboflow in YOLOv8 format
- 🧠 **Augmentation**: Random scaling, flipping, color shifting (YOLOv8-native)

---

## 🧠 Model Training

- **Model**: YOLOv8s
- **Framework**: Ultralytics YOLOv8 (PyTorch-based)
- **Training Parameters**:
  - `epochs = 50`
  - `batch = 8`
  - `imgsz = 640`

#### 🎯 Performance Metrics:
| Metric              | Value   |
|---------------------|---------|
| mAP@0.5             | 94.3%   |
| mAP@0.5:0.95        | 78.6%   |
| Final Box Loss      | ~0.01   |
| Objectness Loss     | ~0.02   |
| Classification Loss | ~0.005  |

---

## 📊 Results

- ✅ People counted per frame
- 🟢 Density levels:  
  - `Low`: ≤ 10 people  
  - `Medium`: 11–25 people  
  - `High`: > 25 people

### 📈 Visual Outputs

#### 🔹 Summary Table and Sample Data
<img src="Screenshot 2025-04-22 113648.png" width="600"/>

#### 🔹 Density Category Distribution
<img src="Screenshot 2025-04-22 113323.png" width="600"/>

#### 🔹 Time vs People Count
<img src="Screenshot 2025-04-22 113249.png" width="600"/>

#### 🔹 Annotated Frame Output
<img src="Screenshot 2025-04-22 113211.png" width="600"/>

#### 🔹 Training Loss & Accuracy Graphs
<img src="Screenshot 2025-04-22 112851.png" width="800"/>

---

## ▶️ Sample Inference

```bash
python crowd_estimator.py --video "video_path.mp4"
```

---

## 📦 Requirements

```bash
pip install ultralytics opencv-python pandas matplotlib
```

---

## 🛠️ Technologies Used

- Python 3.10
- Ultralytics YOLOv8
- OpenCV
- Matplotlib + Pandas
- Jupyter Notebook

---


---

<div align="center">
  <p>🚀 Developed by <strong>Abhi</strong> for crowd-aware smart surveillance systems</p>
  <p>⭐ Star this repo if you find it helpful!</p>
</div>
