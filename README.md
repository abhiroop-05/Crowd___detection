Crowd Density Estimation using YOLOv8
Crowd density estimation is an essential task for smart surveillance systems, public safety, and event management. The goal of this project is to develop a real-time people detection and crowd density estimation model using deep learning, specifically the YOLOv8 architecture.
The system should:
- Detect and count people in video frames
- Estimate crowd density level (Low, Medium, High)
- Visualize detections with bounding boxes
- Generate analytical plots and performance metrics

Dataset
-Total Frames:1007 images extracted from multiple surveillance-style videos
-Source: Videos recorded at 60 FPS in public areas (e.g., shopping malls)
-Annotation Format: YOLOv8 (`.txt` files with bounding boxes)
- **Structure**:
your_dataset/
├── images/
│   ├── train/
│   └── val/
├── labels/
│   ├── train/
│   └── val/
Classes:  
- `0`: Person
Preprocessing Techniques
-Frame Extraction: Extracted every N-th frame (interval = 125) using OpenCV
-Image Resizing: Resized all frames to `640x640` for YOLO compatibility
-Annotation: Labels prepared using Roboflow in YOLOv8 format
-Augmentation: Handled automatically by Ultralytics YOLO during training (scaling, flipping, color shifts)

Model Training

-Model Used: `YOLOv8s` (small variant for speed and accuracy)
-Training Configuration:
- Epochs: `50`
- Batch Size: `8`
- Image Size: `640x640`
- Optimizer: SGD (default in YOLOv8)
- Losses Tracked:
- Distribution Focal Loss (`dfl_loss`)
- Objectness Loss (`obj_loss`)
- Classification Loss (`cls_loss`)
Results
![Screenshot 2025-04-22 112851](https://github.com/user-attachments/assets/e44712ca-ed07-4271-91de-ebece6b88845)

Training Performance
| Metric             Value    |
|-------------------|---------|
| `mAP@0.5`         | 94.3%   |
| `mAP@0.5:0.95`    | 78.6%   |
| Final Box Loss    | ~0.01   |
| Objectness Loss   | ~0.02   |
| Class Loss        | ~0.005  |

Crowd Estimation Output

-People Counted: Detected per frame
-Density Levels:
- `Low`: 0–10 people
- `Medium`: 11–25 people
- `High`: >25 people

Sample Visualizations

- Bounding boxes + density overlay on video frames
- ![image](https://github.com/user-attachments/assets/c4379ddb-420a-47d0-83bf-1394aaac721c)

- Time vs. People Count graph
- ![image](https://github.com/user-attachments/assets/68396970-2d88-44f2-8726-36bd9de8e68b)

- Bar chart for density category distribution
- ![image](https://github.com/user-attachments/assets/c7bd56c1-1370-4cdc-99f5-a687ee1b6031)

- Statistical summary table
   ![image](https://github.com/user-attachments/assets/24e76ad5-847d-46f2-bda1-6e695da0991f)

