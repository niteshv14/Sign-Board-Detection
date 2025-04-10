#  Traffic Sign Detection and Tracking using YOLOv8 + DeepSORT

This repository provides a complete pipeline for training a YOLOv8 object detection model on custom annotated traffic signs, running inference on unseen video, and performing multi-object tracking with DeepSORT.

Sign Detection
├── Annotation/                         # CSV file with bounding boxes and class labels
├── Dataset/                            # Contains subfolders with images per class
├── Object_Tracking/Video/             # Contains test video (UnSeen_Dataset.mp4)
├── labels/                             # YOLO formatted annotations (auto-generated)
├── dataset/                            # Split YOLO dataset for training/validation
├── runs/                               # YOLO training and prediction outputs
├── tracked/                            # DeepSORT tracking output
├── dataset.yaml                        # YOLO config file
├── video_predictions.csv               # Inference predictions (frame-wise)



Step-by-Step Implementation
  1 Convert CSV Annotations to YOLO Format
      Reads a CSV file containing annotations (xmin, xmax, ymin, ymax, and class).
      Converts them to YOLO format (normalized bounding box coordinates).
      Saves one .txt file per image in labels/ folder.

  2 Split Dataset into Train/Validation
      Randomly splits images into training (80%) and validation (20%) sets.
      Copies corresponding .jpg and .txt files to respective folders:
        dataset/images/train, dataset/labels/train
        dataset/images/val, dataset/labels/val

  3 Generate dataset.yaml
      Required by YOLOv8 for training.
      Defines paths, number of classes, and class names.

  4 Train YOLOv8 Model
      Loads a pre-trained YOLOv8n model.
      Trains it for 50 epochs on the custom dataset.

  5  Run Inference on Unseen Video
      Runs object detection on the test video.
      Saves output video with bounding boxes.
      Extracts frame-wise predictions to a CSV file: video_predictions.csv

  6 Perform Multi-Object Tracking (YOLO + DeepSORT)
      Integrates YOLOv8 with DeepSORT for consistent object ID tracking.
      Annotates tracked IDs on output video tracked_output.avi.
      Supports frame-by-frame object persistence.

Most of these files might be missing due to upload limit contact : nikenitesh4@gmail.com
