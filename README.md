# Export Yolov7-weights to .onnx .tflite

## How to Convert yolov7 tiny to .onnx to .tflite

Download Yolov7 Official Repository
https://github.com/WongKinYiu/yolov7.git

Navigate to Yolov7 main folder

Install all the requirements from requirements.txt.
pip install -r requirements.txt
## Download the Yolov7 or Yolov7-Tiny weights
https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7.pt
https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7-tiny.pt

## Install other dependencies

pip install onnx onnxruntime onnxsim onnx-tf
pip install tensorflow tensorflow_probability

## PyTorch model to ONXX
python export.py --weights yolov7-tiny.pt --grid --end2end --simplify --topk-all 100 --iou-thres 0.65 --conf-thres 0.35 --img-size 640 640 --max-wh 640

## Convert onxx model to tensorflow
mkdir tfmodel
onnx-tf convert -i yolov7.onnx -o tfmodel/

## Convert model from Tensorflow to Tensorflow Lite
### Download the file tflite from link below
https://github.com/SyedSybtain/Yolov7-Tiny-.onnx-and-.tflite/blob/main/tf_model_to_tf_lite.py

Run the tf_model_to_tf_lite.py Script

### The output of the script should be Tensorflow Lite model named tfmodel/yolov7_model.tflite

Go to the tfmodel directory in Yolov7 main folder to see the .tflite model

# Run the inference on tflite
Run the tflite_main.py

