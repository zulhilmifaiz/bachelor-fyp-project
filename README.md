# FYP - Speed Bump Detection

Comparative study of three object detection models for speed bump detection using a custom dataset of 9,489 images.

## Results

| Model        | mAP@0.5 | mAP@0.5:0.95 | Precision | Recall | F1    |
|--------------|---------|--------------|-----------|--------|-------|
| YOLOv11      | 0.976   | 0.757        | 0.964     | 0.964  | 0.964 |
| Faster R-CNN | 0.882   | 0.489        | 0.882     | 0.567  | 0.691 |
| SSD300       | 0.743   | 0.515        | 0.743     | 0.571  | 0.646 |

**YOLOv11 achieves the best performance** across all metrics.

## Project Structure

```
FYP-SpeedBump/
├── data/                    # Dataset (not tracked in git — see below)
│   ├── data.yaml            # YOLO dataset config
│   ├── train/               # 6,981 images + labels
│   ├── valid/               # 1,672 images + labels
│   └── test/                # 836 images + labels
├── models/                  # Model weights (not tracked in git)
│   ├── faster_rcnn/
│   ├── ssd/
│   └── yolov11/
├── notebooks/
│   ├── eda.ipynb            # Exploratory data analysis
│   ├── yolov11.ipynb        # YOLOv11 training
│   ├── faster_rcnn.ipynb    # Faster R-CNN training
│   ├── ssd.ipynb            # SSD training
│   ├── comparison.ipynb     # Side-by-side model comparison
│   └── main.ipynb           # Final evaluation (all models)
├── results/                 # JSON metrics and sample detections
│   ├── faster_rcnn/
│   ├── ssd/
│   └── yolov11/
└── docs/                    # FYP report and poster
```

## Setup

```bash
# 1. Clone the repo
git clone https://github.com/<your-username>/FYP-SpeedBump.git
cd FYP-SpeedBump

# 2. Install dependencies
pip install -r requirements.txt

# 3. Download the dataset and model weights separately
#    (place them in data/ and models/ respectively)
```

## Dataset

- **Classes**: 1 (`speed_bump`)
- **Format**: YOLO + COCO dual format
- **Split**: 73.6% train / 17.6% val / 8.8% test
- **Image size**: 640×640

> The dataset is not included in this repository due to its size (678 MB).

## Models

| Model       | Description                              |
|-------------|------------------------------------------|
| YOLOv11     | Real-time one-stage detector (Ultralytics)|
| Faster R-CNN| Two-stage anchor-based detector          |
| SSD300      | Single-shot multibox with VGG16 backbone |

## Usage

Open and run the notebooks in this order:
1. `eda.ipynb` — understand the dataset
2. `yolov11.ipynb` / `faster_rcnn.ipynb` / `ssd.ipynb` — train each model
3. `comparison.ipynb` — compare results
4. `main.ipynb` — final evaluation
