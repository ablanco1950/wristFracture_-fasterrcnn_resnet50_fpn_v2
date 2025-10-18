# wristFracture_-fasterrcnn_resnet50_fpn_v2
This is an experiment adapting the project https://github.com/hubert10/fasterrcnn_resnet50_fpn_v2_new_dataset to detect wrist fractures using a selection of wrist fracture images obtained from https://universe.roboflow.com/landy-aw2jb/fracture-ov5p1/dataset/1 as a custom dataset. Given the positive results, it is uploaded to GitHub.

![Fig1](https://github.com/ablanco1950/wristFracture_-fasterrcnn_resnet50_fpn_v2/blob/main/LT_wrist_jumbo_jpeg_jpg.jpg)

![Fig2](https://github.com/ablanco1950/wristFracture_-fasterrcnn_resnet50_fpn_v2/blob/main/ray-of-a-wrist-with-a-distal-radius-fracture-that-has-healed-in-malalignment-with-a_png_jpg.jpg)

![Fig3](https://github.com/ablanco1950/wristFracture_-fasterrcnn_resnet50_fpn_v2/blob/main/Wrist1.jpg)

1 Download this project wristFracture_fasterrcnn_resnet50_fpn_v2 as a zip file and unzip it into a folder on your hard drive.

2 Download the master project from [hubert10/fasterrcnn_resnet50_fpn_v2_new_dataset: How to Train Faster RCNN ResNet50 FPN V2 on Custom Dataset?](https://github.com/hubert10/fasterrcnn_resnet50_fpn_v2_new_dataset)

as a zip file and unzip it.


You will get the pattern file folder fasterrcnn_resnet50_fpn_v2_new_dataset-main, along with another subfolder of the same name where this pattern project will go.

From the folder created in step 1:

Copy the modules:

MODtrain.py

MODinference.py

From the folder created in step 1, copy the data.zip folder and unzip it. This folder contains the images and annotations for the custom wrist fracture dataset, divided into three directories: train, valid, and test.

Copy the wristFracture.yaml file to the data_configs directory (you can see that there was already a ppe.yaml file from the master project).

3. Train the project:

>python MODtrain.py --model fasterrcnn_resnet50_fpn_v2 --config data_configs/wristFracture.yaml --epochs 25

With each epoch, folders named res_epoch number are created in the outputs/training folder. Initially, they do not contain any models, until they create a res_ folder with a model.pth and the graphs with the loss curves.

4. Check the results.
Assuming the folder where the models were created is res_16 (epoch 16),

python MODinference.py --weights outputs/training/res_16/last_model.pth --input data/wristFracture/dataset/test --threshold 0.8

In the outputs/inference folder, subfolders appear.
Each time the program is run, a subfolder is created with the fracture detection results (the annotation is shown in green, and the predicted one in blue).

Conclusions:

The results are good, but the model is resource-intensive.
To run it on a personal computer, as intended, the training file had to be reduced to just 104 images and the number of epochs to 25 (50 would have been required).

Note:
In the roboflow custom dataset the file names are very long and are truncated in Windows.

References:
https://github.com/hubert10/fasterrcnn_resnet50_fpn_v2_new_dataset
https://universe.roboflow.com/landy-aw2jb/fracture-ov5p1/dataset/1

