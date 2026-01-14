🕳️ Pothole Detection using YOLOv8

Multi-City Road Damage Analysis with Confidence Threshold Tuning

📌 Project Overview

Poor road conditions and potholes are a major cause of accidents, vehicle damage, and traffic inefficiencies—especially in urban environments.
This project explores a computer vision–based pothole detection system using YOLOv8, trained on public road damage datasets and evaluated on real dashcam videos from multiple Indian cities.

Instead of just training a model, this project focuses on:

Dataset engineering

False-positive analysis

Confidence threshold tuning

Cross-city generalization

This makes it closer to a real-world deployment workflow rather than a toy ML demo.

🎯 Objectives

Build a pothole detection model using YOLOv8

Convert RDD 2022 (India + Japan) annotations into YOLO format

Train a unified model focusing on D40 (pothole) class

Evaluate performance on real dashcam videos

Analyze and reduce false positives using confidence threshold tuning

Compare baseline vs tuned predictions visually and qualitatively

📂 Datasets Used
🔹 RDD 2022 (Road Damage Dataset)

Source: Road Damage Detection Challenge

Countries used:

🇮🇳 India

🇯🇵 Japan

Annotation format: Pascal VOC (XML)

Damage classes: D00, D10, D20, D40, …

⚠️ This project focuses exclusively on class D40, which corresponds to potholes, to reduce ambiguity and improve detection reliability.

## Dataset: Road Damage Dataset (RDD 2022)

This project uses the **Road Damage Dataset (RDD 2022)**, a large-scale, multi-country dataset designed for automated road damage detection.

- **Source**: RDD 2022 (India & Japan)
- **Annotation format**: Pascal VOC (XML)
- **Damage classes**: D00, D10, D20, D40
- **Focus class**: **D40 (Potholes)**

### Official Resources
- 🔗 Dataset Repository: https://github.com/sekilab/RoadDamageDetector  
- 📄 Research Paper: https://arxiv.org/abs/2109.02795  
- 📦 Kaggle Mirror: https://www.kaggle.com/datasets/ariyadey/rdd2022-road-damage-detection  

> ⚠️ Due to dataset size and licensing constraints, the dataset is **not included** in this repository.  
> Users should download the dataset from the official sources above and follow the directory structure described in this project.


🧠 Methodology
1️⃣ Unified Dataset Preparation (India + Japan)

A single, country-agnostic pipeline is used for both datasets.

Steps:

Parse Pascal VOC XML annotations

Filter objects to keep only D40

Convert bounding boxes to YOLO format

Remove images with no pothole annotations

Create train/validation split (80/20)

This ensures:

Consistency across countries

Fair training distribution

Clean YOLO-ready dataset

2️⃣ Model Training

Model: YOLOv8n

Framework: Ultralytics YOLO

Input size: 640×640

Training data:

Combined India + Japan dataset

Output:

Trained weights for pothole detection

3️⃣ Inference on Real Dashcam Videos

Dashcam videos were collected from four Indian cities:

  **City**	                **Environment Type**
Chandigarh	               Wide urban roads
Chennai	                   Dense traffic & markings
Patna	                   Uneven roads & speed breakers
Vijayawada	               Lane markings & curbs

For each city:

Same video frames used for baseline and tuned inference

Ensures fair, frame-by-frame comparison

4️⃣ Confidence Threshold Tuning

Two configurations were compared:

Baseline: conf = 0.25

Proposed: conf = 0.50

Goal:

Reduce false positives while preserving true pothole detections.

5️⃣ Visual Comparison & False-Positive Analysis

For every city:

Baseline and tuned outputs placed side-by-side

False positives were manually inspected and categorized

Observed Baseline False Positives
**City**	        **False Positives**
Chandigarh	         Car stereo, repaired road patches
Chennai	             Road signs, zebra crossings
Patna	             Speed breakers, flat road patches
Vijayawada	         Lane markings, curbs

📊 Results
✅ Key Outcomes

Increasing confidence threshold:

Significantly reduced false positives

Improved visual clarity of detections

No major loss of true pothole detections observed

Model generalized reasonably well across cities

📌 Qualitative Insight

This project highlights that confidence tuning is a critical deployment step, often more impactful than changing the model architecture itself.

🧪 Discussion
What Worked Well

Unified training across countries improved robustness

Manual inspection revealed dataset-specific biases

Side-by-side visual comparison made results interpretable

Limitations

No quantitative metrics (precision/recall) on real-world videos

Night, rain, and extreme lighting not tested

Single-class focus (D40 only)

🔮 Future Scope

Add multi-class damage detection (D00, D10, D20)

Integrate GPS tagging for pothole localization

Deploy as:

Mobile app

Edge device (Jetson / Raspberry Pi)

Add temporal smoothing to stabilize video predictions

Evaluate under night and adverse weather conditions

# ## Full Video Results
Due to GitHub size limitations, full inference videos are not included.

Sample videos can be provided on request or shared via:
- Google Drive
- YouTube (unlisted)
- LinkedIn post
