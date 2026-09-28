# Street_Vehicle_Detection_YOLO11
Identifying and counting these vehicles and people from street footage
# Street Vehicle Detection using YOLO11

A custom object detection project that detects and classifies **motorbikes, rickshaws, cars and people** in City street images and video, using a YOLO11 model trained on a self-collected and self-annotated dataset.

---

## 1. Project Title
City Street Vehicle Detection using YOLO11

## 2. Problem Statement
City streets have mixed traffic made up of motorbikes, rickshaws, cars and pedestrians sharing the same road space. Manually identifying and counting these vehicles and people from street footage is slow, tiring and error-prone. Traffic in City also differs from the data in most standard datasets: rickshaws are rare there, and dense, overlapping traffic is common.

## 3. Objective
- Build a custom YOLO11 object detector for four classes: **Motorbike, Rickshaw, Car, Person**.
- Detect and classify these objects in street images and video.
- Count each class automatically, to support basic traffic monitoring.

## 4. Proposed Solution
Collect street images and video frames from City, annotate them with bounding boxes and class labels, and train a YOLO11 model using transfer learning from COCO-pretrained weights. The trained model outputs a bounding box, class name and confidence score for each object. Combined with object tracking on video, it gives per-class counts.

## 5. Dataset Collection Method
Images were captured with a mobile camera on City streets, covering different angles, distances, backgrounds, lighting conditions and traffic densities. Frames were extracted from video where needed. <!-- Add: locations, times of day, and any external image sources (the assignment requires these to be stated). -->

## 6. Dataset Size
**402 images** in total.

## 7. Number of Classes
**4:** Motorbike, Rickshaw, Car, Person

## 8. Annotation Method
Images were annotated manually with bounding boxes and class labels using **Roboflow**, then exported in **YOLOv11 format** (images, label `.txt` files and `data.yaml`).

## 9. Train / Validation / Test Split

| Split | Images | Share |
|---|---|---|
| Train | 352 | 88% |
| Validation | 33 | 8% |
| Test | 17 | 4% |
| **Total** | **402** | 100% |

## 10. YOLO Model Used
YOLO11n (nano), fine-tuned from COCO-pretrained weights via the Ultralytics library.

## 11. Training Parameters

| Parameter | Value |
|---|---|
| Model | YOLO11n |
| Image size | 640 |
| Epochs | 60 |
| Batch size | 16 |
| Early stopping patience | 20 |
| Dataset size | 402 images |
| Number of classes | 4 |
| Environment | Google Colab (T4 GPU) |



## Precision, Recall and mAP Results
### Matric     Value
- Precision : 0.621
- Recall    : 0.631
- mAP@50    : 0.594
- mAP@50-95 : 0.346

### Per-class results:
- Car        P=0.580  R=0.654  mAP50=0.615  mAP50-95=0.377
- Motorbike  P=0.594  R=0.576  mAP50=0.542  mAP50-95=0.311
- Person     P=0.635  R=0.581  mAP50=0.545  mAP50-95=0.268
- Rickshaw   P=0.675  R=0.714  mAP50=0.674  mAP50-95=0.430


## Challenges Faced
- **Small dataset:** with 402 images, the model may not generalise well to new streets, lighting or camera angles. The 33-image validation set and 17-image test set give only rough estimates of performance.
- **Class imbalance:** motorbikes appear far more often than rickshaws or cars.
- **Person class:** pedestrians vary widely in pose and are often hidden behind vehicles, which makes them harder to detect.
- **Small and distant objects:** vehicles far down the street appear very small in the frame.
- **Occlusion and dense traffic:** overlapping vehicles make bounding boxes harder to draw and to detect.

## 19. Conclusion
<!-- Fill in after training, e.g.: The YOLO11n model reached mAP@50 of X on the validation set, detecting motorbikes and cars reliably while Person and Rickshaw remained harder. Future work: collect more images (especially rickshaws and night scenes), try YOLO11s, and add tracking-based counting. -->


## Tools
Python, Ultralytics YOLO11, Roboflow, Google Colab, OpenCV, Matplotlib
