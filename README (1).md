# Automatic Number Plate Recognition using YOLOv8

This project implements an Automatic Number Plate Recognition (ANPR) system using YOLOv8 for vehicle and license plate detection, along with EasyOCR for text recognition.

## Project Overview

The system performs the following tasks:
1. Vehicle Detection using YOLOv8
2. License Plate Detection using YOLOv8
3. License Plate Text Recognition using EasyOCR
4. Vehicle Tracking using SORT (Simple Online and Realtime Tracking)

## Requirements

- Python 3.11
- PyTorch
- YOLOv8
- OpenCV
- EasyOCR
- NumPy
- Pandas
- filterpy (for SORT tracking)

## Installation

1. Create and activate a Python 3.11 environment:
```bash
pyenv install 3.11.9
pyenv virtualenv 3.11.9 yolov8-env
pyenv activate yolov8-env
```

2. Install the required packages:
```bash
pip install torch==2.4.0 torchvision==0.19.0 torchaudio==2.4.0
pip install ultralytics==8.0.114 pandas==2.0.2 opencv-python==4.7.0.72 
pip install numpy==1.24.3 scipy==1.10.1 easyocr==1.7.0 filterpy==1.4.5
```

## Project Structure

```
yolov8_project/
├── main.py               # Main script for ANPR
├── util.py              # Utility functions
├── add_missing_data.py  # Script to handle missing data
├── visualize.py         # Visualization utilities
├── models/              # Directory for model weights
│   └── yolov8n.pt      # YOLOv8 model weights
├── sort/               # SORT tracking implementation
│   └── sort.py        # SORT algorithm
└── sample.mp4         # Sample video for testing
```

## Usage

1. Place your input video as `sample.mp4` in the project directory.
2. Run the main script:
```bash
python main.py
```

The script will:
- Detect vehicles in the video
- Identify license plates
- Read the text from license plates
- Track vehicles across frames
- Generate results with vehicle IDs and license plate numbers

## How It Works

1. **Vehicle Detection**: Uses YOLOv8 to detect vehicles in each frame.
2. **License Plate Detection**: Applies YOLOv8 to detect license plates within vehicle regions.
3. **Text Recognition**: Uses EasyOCR to read text from detected license plates.
4. **Vehicle Tracking**: Implements SORT algorithm to maintain vehicle identity across frames.

## Output

The system generates:
- Processed video frames with vehicle and license plate detections
- CSV file with tracking results
- Vehicle IDs matched with their license plate numbers

## Notes

- CPU Usage: The system runs on CPU by default but supports GPU acceleration if available.
- Model Weights: Using YOLOv8n (nano) model for both vehicle and license plate detection.
- Performance: Processing speed depends on hardware capabilities and input video resolution.

## Future Improvements

- Add support for custom license plate detection model
- Implement real-time processing capabilities
- Add multi-GPU support
- Enhance OCR accuracy for different plate types
- Add support for multiple video formats

## License

This project is licensed under the MIT License - see the LICENSE file for details.

The video I used in this tutorial can be downloaded [here](https://www.pexels.com/video/traffic-flow-in-the-highway-2103099/).

## models

A Yolov8 pretrained model was used to detect vehicles.

A licensed plate detector was used to detect license plates. The model was trained with Yolov8 using [this dataset](https://universe.roboflow.com/roboflow-universe-projects/license-plate-recognition-rxg4e/dataset/4) and following this [step by step tutorial on how to train an object detector with Yolov8 on your custom data](https://github.com/computervisioneng/train-yolov8-custom-dataset-step-by-step-guide). 

The trained model is available in my [Patreon](https://www.patreon.com/ComputerVisionEngineer).

## dependencies

The sort module needs to be downloaded from [this repository](https://github.com/abewley/sort) as mentioned in the [video](https://youtu.be/fyJB1t0o0ms?t=1120).
