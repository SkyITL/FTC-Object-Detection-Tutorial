# FTC-Object-Detection-Tutorial
Best Limelight 3A Object Detection Tutorial for First Tech Challenge teams who are new to machine learning and want to enhance their performance by Object Detection

Link to colab: https://colab.research.google.com/drive/1Va2sn476X0AMfYKHIClsrEXm5QalcM0_?usp=sharing

- Model used: SSD Mobilenet V2 FPNlite 320*320 from Tensorflow V2 Object Detection model zoo
- Pretrain Dataset: Coco 17
- Recommended training dataset format: TFRecords
- Recommended labeling platform: Roboflow
- Developed by Treeman 19600 <3

## **Steps to use:**

0: Collect data and label with any labeling tool. Export your data in *TFRecord* format. You do not need to augment the dataset with horizontal flips - the code does that already.

1: **Rename** your dataset folder to /tfrecords.
  - Your dataset structure should contain /tfrecords/train/objects.tfrecord, /tfrecords/valid/objects.tfrecord, /tfrecords/test/objects.tfrecord and etc.

2: **Zip and upload your tfrecords folder to /content/tfrecords.zip**

3: Modify Hyperparameters as you wish.

4: Hit run all. You can stop training process early and export the model.

5: If ran into bugs, hit restart runtime

6: Your model would be automatically downloaded. Upload the 8bit tflite model and labels.txt to your limelight. 

7: Free Google Colab do sometimes kill their connection and delete all files, if you want continuous training over a long time period, you should have a copy training_output on your local device once in a while to prevent progress loss. Set your browser settings to always keep colab active to minimize chances of disconnection.

## **FAQ**

Q1: Why my training code keeps aborting when I didn't make it stop?

- A1: Your code might have requested too much RAM thus colab disconnects. Reduce batchsize to 8.

Q2: Why the code took so long to train my model? 

- A2: Tensorflow models took time to load their whole computational graph into RAM. Normally, you could see progress reports after 100 steps and could see average time taken to train per step. The estimated time could also be calculated with roughly 5s / step on free Google Colab runtime for each 100 images in your dataset.

Q3: Could the training code start upon my checkpoints?

- A3: Yes, The training code do start upon any checkpoints inside the model-path.

Q4: Why my trained model didn't predict any boundingbox / Why is my model's confidence so low?

- A4: Your model is underfitted. Train with more steps if you stopped early.

Q5: Why my trained model isn't creating good bounding box?

- A5: Either your model is underfitted - refer to A4, or you should enhance your training data. Vary your train data to ensure they are representative of all instance your robot might face, increase number of trianing data, and make more precise labeling

Q6: Why my tflite model's performance is significantly worse than my original tfmodel?

- A6: Your model is not correctly aligned after converting. Although unlikely, manually pick your representative data so they are diverse and truely representative or change quantizing methods.

