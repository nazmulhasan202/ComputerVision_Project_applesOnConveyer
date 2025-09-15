# Apple Detection and Counting on Conveyor using YOLO

This project demonstrates how to **fine-tune** the Ultralytics YOLO model for a **_custom application_** of detecting and counting apples on a conveyor belt. The workflow includes model inference on images, model training, evaluation, and real-world application on video data. All steps are documented in [`notebook.ipynb`](notebook.ipynb).

---

## Table of Contents

- Overview
- Project Structure
- Requirements
- Usage
  - 1. Inference on Images
  - 2. Model Training
  - 3. Evaluation After Training
  - 4. Real-World Application: Counting Apples in Video
  - 5. Viewing Results
- Dataset
- Results
- References

---

## Overview

The notebook walks through the following steps:

1. **Inference on a sample image** using a pre-trained YOLO model.
2. **Training a custom YOLO model** on an apple dataset.
3. **Evaluating the trained model** on images.
4. **Applying the trained model to video** for real-time apple counting on a conveyor.
5. **Visualizing results** from both image and video inference.

---

## Project Structure

```
apple.jpg
data.yaml
notebook.ipynb
README.md
requirement.txt
result.avi
video.mp4
yolo11n.pt
dataset/
    train/
        images/
        labels/
        labels.cache
    val/
        images/
        labels/
        labels.cache
    test/
        images/
        labels/
runs/
    detect/
        predict/
        predict2/
        predict3/
        train2/
```

---

## Requirements

- Python 3.8+
- [Ultralytics YOLO](https://docs.ultralytics.com/)
- OpenCV
- IPython, PIL

Install dependencies:
```sh
pip install -r requirement.txt
```

---

## Usage

### 1. Inference on Images

- Loads a pre-trained YOLO model ([`yolo11n.pt`](yolo11n.pt)).
- Runs prediction on [`apple.jpg`](apple.jpg).
- Displays bounding boxes and saves the result in the `runs/detect/predict*` directory.

### 2. Model Training

- Trains a YOLO model using the dataset defined in [`data.yaml`](data.yaml).
- Training parameters: batch size 16, 100 epochs, 1 worker.
- Model weights are saved in `runs/detect/train2/weights/`.

### 3. Evaluation After Training

- Loads the trained model (`yolo11n-apple.pt`).
- The best trained model (`best.pt`) is copied and renamed as `yolo11n-apple.pt` for future reference.
- Runs prediction on [`apple.jpg`](apple.jpg) and displays the results.

### 4. Real-World Application: Counting Apples in Video

- Loads a video ([`video.mp4`](video.mp4)).
- Initializes the YOLO-based object counter.
- Processes the video for a set duration (default: 5 seconds).
- Draws counting lines and overlays results.
- Saves the processed video as [`result.avi`](result.avi).

### 5. Viewing Results

- Opens [`result.avi`](result.avi) and displays a specific frame using OpenCV and PIL.

---

## Dataset

The dataset is organized in YOLO format under the [`dataset`](dataset) directory, with separate folders for `train`, `val`, and `test` splits. Each split contains `images/` and `labels/` subfolders.

- **images/**: Contains `.jpg` files of apples on a conveyor.
- **labels/**: Contains corresponding `.txt` files with YOLO annotations.

The dataset is referenced in [`data.yaml`](data.yaml).

---

## Results

- **Image Inference**: Bounding boxes are drawn around detected apples.
- **Training**: Model performance metrics are printed after training.
- **Video Counting**: Apples are counted as they cross a defined region in the video, and results are visualized in [`result.avi`](result.avi).

---

## References

- [Ultralytics YOLO Documentation](https://docs.ultralytics.com/)
- [OpenCV Documentation](https://docs.opencv.org/)
- [`notebook.ipynb`](notebook.ipynb) for full code and step-by-step workflow.

---

For questions or issues, please refer to the notebook or open an issue in this repository.

## License
This repository is licensed under the [GNU Affero General Public License v3.0](LICENSE).
