# MARS - Mine Rescue AI System

MARS is an AI system to help rescue teams inside mines. A YOLO11n object detection model looks at camera images and detects people, fire, smoke and vehicles. The model runs on a **Raspberry Pi**, and a web dashboard fetches the detection data from the Pi and shows it.

I built this project for **Smart India Hackathon (SIH) 2026**. I also presented it at the inauguration of the **Capgemini Centre of Excellence at NIET, Greater Noida**.

---

## What It Detects

| ID | Class |
|---|---|
| 0 | person |
| 1 | fire |
| 2 | smoke |
| 3 | small_vehicle |
| 4 | large_vehicle |
| 5 | two_wheeler |

## How It Works

1. A camera connected to the Raspberry Pi captures images.
2. The trained YOLO11n model runs on the Raspberry Pi and detects the 6 classes.
3. The dashboard (HTML, custom CSS and JavaScript) fetches the detection data from the Pi and displays it.

## Model Training

- **Base model:** pretrained YOLO11n (`yolo11n.pt`) from Ultralytics
- **Dataset:** 12,440 labelled images with 6 classes
- **Epochs:** 50
- **Image size:** 416
- **Batch size:** 16
- **Trained on:** Google Colab (Ultralytics 8.4.138)

## Results (Validation)

| Metric | Value |
|---|---|
| Precision | 81.3% |
| Recall | 79.6% |
| mAP50 | **82.2%** |
| mAP50-95 | 64.3% |

## Tech Stack

Python, Ultralytics YOLO11, Raspberry Pi, HTML, CSS, JavaScript

## Try the Model

Install Ultralytics:

```
pip install ultralytics
```

Run the trained model on an image:

```
yolo predict model=best.pt source=your_image.jpg imgsz=416
```

Or in Python:

```python
from ultralytics import YOLO

model = YOLO("best.pt")
results = model("your_image.jpg", imgsz=416)
results[0].show()
```

## Note

YOLO11 is made by Ultralytics and is released under the AGPL-3.0 license.

## Author

**Vishal Bariar**

B.Tech, Electronics and Communication Engineering, NIET Greater Noida

[LinkedIn](https://www.linkedin.com/in/vishal-bariar-431772349) | [GitHub](https://github.com/Vishalbariar)
