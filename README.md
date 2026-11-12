# Damaged-Car-parts-prediction-using-YOLOv8

## Training

``` pip install ultralytics```

* Collect dataset of damaged cars
* Annotate them
* in this case there are 8 classes namely : damaged door, damaged window, damaged headlight, damaged mirror, dent, damaged hood, damaged bumper, damaged windshield
* convert the annotations into YOLO 1.1 format
* run ```main.py```
* in this particular case i ran for 5000 epochs



![Screenshot from 2023-03-18 19-50-29](https://user-images.githubusercontent.com/17148269/226126564-145ebe9f-e276-44f9-b4cd-023843aafd1a.png)


## Results





![F1_curve](https://user-images.githubusercontent.com/17148269/226126757-21ec1c85-32a6-4e6f-ab51-6d07bf37c2e7.png)
![P_curve](https://user-images.githubusercontent.com/17148269/226126770-2d03e247-53df-4e82-9b1c-612126319ac1.png)
![PR_curve](https://user-images.githubusercontent.com/17148269/226126832-83ee056e-8711-4f0c-9c80-b23810aa42e0.png)
![R_curve](https://user-images.githubusercontent.com/17148269/226126876-132571a1-45b1-4595-bf1e-b30425f4b73f.png)



## Prediction
![val_batch0_pred](https://user-images.githubusercontent.com/17148269/226127656-dce9f1ed-fc2d-41be-8400-678b6bbc0cb3.jpg)
![val_batch1_pred](https://user-images.githubusercontent.com/17148269/226127705-c9fddde3-b5cf-4266-91cf-08d5705aa452.jpg)
![val_batch2_pred](https://user-images.githubusercontent.com/17148269/226127766-4bb44851-a3af-4c06-a86c-c0fdbd3803f8.jpg)
## Deployment

![Screenshot from 2023-03-20 06-11-43](https://user-images.githubusercontent.com/17148269/226222000-41ed7812-b1d2-4d4f-a5ee-97230d0eba98.png)

## Usage

* Clone the repo
* cd to my_fastapi_app
* run ```python main.py```

Test with images
Done!
Contributor: Mouli
Contributor: Aishwarya

## Backend API Implementation

The backend is developed using FastAPI and OpenCV to perform vehicle damage detection using a trained YOLOv8 model exported in ONNX format.

### Model Initialization

The `Detection` class initializes the trained ONNX model using OpenCV's DNN module. It defines eight vehicle damage categories:

- Damaged Door
- Damaged Window
- Damaged Headlight
- Damaged Mirror
- Dent
- Damaged Hood
- Damaged Bumper
- Damaged Windshield

### Image Processing and Inference

The application follows these processing steps:

1. Receives an uploaded vehicle image.
2. Converts the uploaded image into RGB format.
3. Converts the image into a NumPy array.
4. Creates an input blob with a size of 640 × 640.
5. Passes the image to the trained ONNX model.
6. Processes model predictions to identify damage categories and bounding boxes.
7. Applies Non-Maximum Suppression (NMS) to filter overlapping detections.

### API Endpoint

**Endpoint:** `/detection`

**Method:** POST

**Input:** Vehicle image uploaded as a file.

**Response:** JSON containing detected classes, confidence scores and bounding boxes.

### Example JSON Response

```json
{
  "boxes": [
    [120, 80, 200, 150]
  ],
  "confidences": [
    95.6
  ],
  "classes": [
    "damaged bumper"
  ]
}
```

*The above response is illustrative; actual values depend on the uploaded image and model predictions.*

### Backend Technologies

- Python
- FastAPI
- OpenCV DNN
- ONNX
- NumPy
- Pillow
- Uvicorn

API Testing and Integration

The project provides a REST API built using FastAPI to detect damaged vehicle parts from uploaded images.

API Endpoint

- Endpoint: "/detection"
- Method: POST
- Input: Vehicle image file
- Output: JSON response containing detected damage classes, confidence scores, and bounding box coordinates.

Running the Application

1. Navigate to the "my_fastapi_app" directory.
2. Install the required dependencies using the project's requirements file, if available.
3. Start the application:

python main.py

4. The FastAPI server runs on port "8080".

Testing Through Swagger UI

Open the following URL in your browser after starting the server:

http://localhost:8080/docs

1. Locate the "/detection" endpoint.
2. Select POST.
3. Click Try it out.
4. Upload a vehicle damage image.
5. Click Execute.
6. View the JSON prediction response.

Prediction Output

The API returns three main fields:

- "boxes": Coordinates of detected damaged regions.
- "confidences": Confidence scores of the predictions.
- "classes": Predicted vehicle damage categories.

Supported Damage Categories

1. Damaged Door
2. Damaged Window
3. Damaged Headlight
4. Damaged Mirror
5. Dent
6. Damaged Hood
7. Damaged Bumper
8. Damaged Windshield

Contributor

Mouli – API testing and project usage documentation.
