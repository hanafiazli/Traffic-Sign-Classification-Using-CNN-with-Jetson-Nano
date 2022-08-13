# Traffic-Sign-Classification-Using-CNN-with-Jetson-Nano
Hello, this is my deep learning project in Intelligent Video and Computer Vision in International Islamic University Malaysia (IIUM). 

The project is to classify the traffic sign using the image classification method and Jetson Nano is utilized in this project. PLease note that all the code below need to be run in terminal and to be safe run inside your docker or environment.

![road work](https://user-images.githubusercontent.com/109489079/184506546-1da10840-d790-473b-88b9-a886bc723ad0.jpg)

#### _1) Download project into the Jetson Nano:_

```
git clone https://github.com/hanafiazli/Traffic-Sign-Classification-Using-CNN-with-Jetson-Nano.git
```

#### _2) Run this command before start training with dataset:_
```
python train.py --model-dir=models/traffic --epochs=70 --batch-size=4 --workers=1  --arch=resnet34 data/traffic
```

#### _3) Convert the tar format using onnx_export.py after completing the training:_
