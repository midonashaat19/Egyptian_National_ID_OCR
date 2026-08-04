# Egyptian National ID OCR

An OCR pipeline for extracting structured information from Egyptian National ID cards using **YOLO11**, **PaddleOCR**, and custom image preprocessing techniques.

---

# Acknowledgements

The **ID card detection model** (`detect_id_card.pt`) used to locate and crop the ID card from the background is based on the work from:

**Forked from:** NASO7Y/OCR_Egyptian_ID

## Project Overview

This project automatically extracts information from Egyptian National ID cards through the following pipeline:

1. Detect the ID card.
2. Detect each field separately using a trained YOLO11 model.
3. Crop every detected field.
4. Apply field-specific preprocessing.
5. Extract Arabic text using PaddleOCR.
6. Store the extracted information in a structured DataFrame.

---

## Features

- Egyptian National ID detection
- Individual field detection
- Custom preprocessing for every field
- Arabic OCR using PaddleOCR
- Automatic DataFrame generation
- Image quality enhancement before OCR

---

## Classes

The model detects the following fields:

- Face
- Name1
- Name2
- Num1
- Num2
- Add1
- Add2

---

# Pipeline

```
Input Image
      │
      ▼
Detect ID Card
      │
      ▼
YOLO11 Object Detection
      │
      ▼
Crop Each Field
      │
      ▼
Image Preprocessing
      │
      ▼
PaddleOCR
      │
      ▼
DataFrame
```

---

# Technologies

- Python
- Ultralytics YOLO11
- PaddleOCR
- OpenCV
- NumPy
- Pandas
- Matplotlib

---

# Dataset

Dataset used for training:

https://universe.roboflow.com/rdl/zeyad-merged-kwhdy

Version:

https://universe.roboflow.com/rdl/zeyad-merged-kwhdy/dataset/2

---

# Model Training

The YOLO11 model was trained using:

- Epochs: 150
- Image Size: 960
- Batch Size: 8
- Optimizer: AdamW
- Early Stopping Patience: 30

---

# Image Preprocessing

Different preprocessing parameters were applied depending on the detected field.

Examples include:

- Fast Non-Local Means Denoising
- Image Resizing
- Padding
- Border Expansion

This significantly improved OCR accuracy.

---

# Results

Evaluation on 34 Egyptian National ID cards:

| Field | Accuracy |
|--------|----------|
| Name1 | 100% |
| Name2 | 93% |
| Num1 | 91% |
| Num2 | 97% |
| Add1 | 92% |
| Add2 | 91% |

---

# Output

The final output is stored as a Pandas DataFrame.

Example:

| Image | Name1 | Name2 | Num1 | Num2 | Add1 | Add2 |
|------|------|------|------|------|------|------|

---

# Repository Structure

```
Egyptian_National_ID_OCR
│
├── YOLOsID_OCR.ipynb
├── best.pt
├── object_detect.png
├── sample_images/
├── README.md
└── requirements.txt
```

---

# Requirements

```
ultralytics
paddleocr
opencv-python
pd,np,plt
```

---

# Future Improvements
- better yolo model
- more ocr models and compare them
- Better preprocessing
- Real-time detection
- GUI application
- Export results to Excel
- Confidence visualization
- IDV
- deploying


---

## Author

Developed by ** Mohamed Nashaat **
