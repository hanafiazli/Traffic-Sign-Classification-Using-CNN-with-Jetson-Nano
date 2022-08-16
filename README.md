# Traffic-Sign-Classification-Using-CNN-with-Jetson-Nano
Hello, this is my deep learning project in Intelligent Video and Computer Vision in International Islamic University Malaysia (IIUM). 

The project is to classify the traffic sign using the image classification method and Jetson Nano is utilized in this project. Please note that all the code below need to be run in the terminal and run inside your docker or environment.

![road work](https://user-images.githubusercontent.com/109489079/184506546-1da10840-d790-473b-88b9-a886bc723ad0.jpg)

### _First Step: Download project into the Jetson Nano:_

1. First, you need to git clone this repository. In your terminal, 
```
git clone https://github.com/dusty-nv/jetson-inference.git
```
A github repositary created by Dusty Franklin, NVIDIA jetson developer.

2. Then, a folder name 'jetson-inference' will be created and go to ./python/examples in the folder.
3. Copy the 'imagenet.py' file.
4. Go back to initial folder path, and go to ./python/training/classification and paste the file here.
5. Go to /jetson-inference/python/training/classification/models , create a folder. 

You also can download on your local machine (laptop) to execute the training beforehand. Input your data set inside `/data folder`. I have provided the dataset. Before starting to train a model with the dataset, make sure that you have all important library inside train.py are installed inside your docker (Jetson Nano) or environment (Local Machine).

### _Second Step: Run on Jetson Nano:_

1. Train your model by following the command below:
```
python train.py --model-dir=models/traffic --epochs=70 --batch-size=4 --workers=1  --arch=resnet34 data/traffic
```
Your model can be found in the folder `data/models/your_file_name` with the name `model_best.pth.tar`. You can adjust the epoch, batch size, learning rate and pre-trained model accordingly.

2. Convert the tar format using onnx_export.py after completing the training
```
python onnx_export.py --model-dir=models/traffic
```
You will find a file inside /models/traffic with name resnet34.onnx. The file will depends on the pretrained model name that you use during the training. Besides, you can download the file from my google drive, 
```
gdown https(kau punya link google drive)
```

### _Third Step: Testing on Jetson Nano:_

Before start to execute the model, you can try to check the availability of your webcam in your Jetson Nano, run `/dev/video` in the terminal before running inference code.

Lastly, to test the project. In Terminal, make sure run in a docker before test and cd on path /jetson-inference/python/training/classification , type:
```
python imagenet.py --model=models/file_name/resnet34.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/file_name/labels.txt /dev/video0
```




