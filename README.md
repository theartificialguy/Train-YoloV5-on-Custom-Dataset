# Train-YoloV5-on-Custom-Dataset
In this repo, I have included the steps involved in order to train your own YoloV5 object detector on Custom Dataset.

image dataset website link:- https://storage.googleapis.com/openimages/web/visualizer/index.html?set=train&type=detection&c=%2Fm%2F052sf

steps invovled:-

1.) git clone https://github.com/yash-007/Train-YoloV5-on-Custom-Dataset.git <br />
2.) pip3 install -r requirements.txt <br />
3.) python main.py downloader --classes Apple Orange --type_csv train --limit 5000 --multiclasses 1 <br />
4.) edit classes text file <br />
5.) python convert_annotations.py <br />

switch to google colab (if you don't have a good PC like me :D) <br />

6.) !git clone https://github.com/ultralytics/yolov5 <br />
7.) !pip install -U -r yolov5/requirements.txt <br />
8.) %cd /content/yolov5 <br />
9.) Create and add a yaml file (my_classes.yaml) inside data folder of yolov5 cloned repo, so that yolov5 wud be able to find the class images for training. <br />

'''<br />
train: /content/drive/MyDrive/datasets/OID/Dataset/train/Apple_Orange <br />
val: /content/drive/MyDrive/datasets/OID/Dataset/val/Apple_Orange <br />
test: /content/drive/MyDrive/datasets/OID/Dataset/val/Apple_Orange <br />
nc: 2 # num of classes <br />
names: ['Apple', 'Orange'] # classes <br />
'''<br />

10.) !python train.py --img 416 --batch 16 --epochs 30 --data ./data/my_classes.yaml --cfg ./models/yolov5s.yaml --weights  /content/drive/MyDrive/datasets/OID --name yolov5s_results  --cache --device 0 <br />
11.) !python detect.py --weights /content/drive/MyDrive/datasets/OID/ --img 416 --conf 0.4 --source /content/drive/MyDrive/datasets/OID/Dataset/test <br />
