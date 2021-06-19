# Train-YoloV5-on-Custom-Dataset
In this repo, I have included the steps involved in order to train your own YoloV5 object detector on Custom Dataset.

image dataset website link:- https://storage.googleapis.com/openimages/web/visualizer/index.html?set=train&type=detection&c=%2Fm%2F052sf

steps invovled:-

1.) git clone https://github.com/EscVM/OIDv4_ToolKit.git
2.) pip3 install -r requirements.txt
3.) python main.py downloader --classes Apple Orange --type_csv train --limit 5000 --multiclasses 1
4.) edit classes text file
5.) python convert_annotations.py

switch to google colab (if you don't have a good PC like me :D)

6.) !git clone https://github.com/ultralytics/yolov5
7.) !pip install -U -r yolov5/requirements.txt
8.) %cd /content/yolov5
9.) Create and add a yaml file inside data folder of yolov5 cloned repo, so that yolov5 wud be able to find the class images for training.

'''
# train and val data as 1) directory: path/images/, 2) file: path/images.txt, or 3) list: [path1/images/, path2/images/]
train: /content/drive/MyDrive/datasets/OID/Dataset/train/Apple_Orange
val: /content/drive/MyDrive/datasets/OID/Dataset/val/Apple_Orange
test: /content/drive/MyDrive/datasets/OID/Dataset/val/Apple_Orange
# number of classes
nc: 2

# class names
names: ['Apple', 'Orange']
'''

10.) !python train.py --img 416 --batch 16 --epochs 30 --data ./data/my_classes.yaml --cfg ./models/yolov5s.yaml --weights  /content/drive/MyDrive/datasets/OID --name yolov5s_results  --cache --device 0
11.) !python detect.py --weights /content/drive/MyDrive/datasets/OID/ --img 416 --conf 0.4 --source /content/drive/MyDrive/datasets/OID/Dataset/test
