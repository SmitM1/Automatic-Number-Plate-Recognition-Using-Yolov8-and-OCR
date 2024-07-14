# Automatic Number Plate Recognition Using YOLOv8 and Tesseract OCR

This project aims to recognize and extract number plates from vehicles using YOLOv8 for object detection and Tesseract OCR for optical character recognition.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

## Introduction

Automatic Number Plate Recognition (ANPR) systems are used to read vehicle registration plates for various applications, including toll collection, traffic law enforcement, and access control. This project utilizes the YOLOv8 model for detecting number plates in images and videos and Tesseract OCR for reading the text on the detected plates.

## Features

- **YOLOv8**: Advanced object detection model for accurate number plate detection.
- **Tesseract OCR**: Optical character recognition to read text from detected number plates.
- **LabelImg**: Tool for labeling images to create training datasets.
- **Image and Video Processing**: Convert video frames to images and process them for number plate detection and recognition.

## Installation

Follow these steps to set up the project on your local machine.

1. **Clone the repository**:
    ```bash
    git clone https://github.com/SmitM1/Automatic-Number-Plate-Recognition-Using-Yolov8-and-OCR.git
    cd Automatic-Number-Plate-Recognition-Using-Yolov8-and-OCR
    ```

2. **Create a virtual environment and activate it**:
    ```bash
    python -m venv venv
    source venv/bin/activate   # On Windows use `venv\Scripts\activate`
    ```

3. **Install the required packages**:
    ```bash
    pip install -r requirements.txt
    ```

4. **Install Tesseract OCR**:
    - Download and install Tesseract OCR from [here](https://github.com/tesseract-ocr/tesseract).
    - Update the Tesseract OCR path in your script (`main1.py`):
        ```python
        pytesseract.pytesseract.tesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'
        ```

## Usage

1. **Convert video to images**:
    - Run the `img.py` script to extract frames from your video:
        ```bash
        python img.py
        ```

2. **Create labels for images**:
    - Use LabelImg to label the extracted images. Save the label files in the appropriate format for YOLOv8.

3. **Train the YOLOv8 model**:
    - Ensure your dataset is properly structured and update the paths in `data.yaml`.
    - Train the model using the following command:
        ```bash
        yolo task=detect mode=train model=yolov8s.pt data=dataset/data.yaml epochs=100 imgsz=800 device=0 plots=True
        ```

4. **Run the ANPR system**:
    - Execute the `main1.py` script to start detecting and recognizing number plates:
        ```bash
        python main1.py
        ```

## Results

After running the `main1.py` script, detected number plates along with their timestamps will be saved in `car_plate_data.txt`. The bounding boxes for the detected number plates will be displayed on the video frames.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or new features.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
