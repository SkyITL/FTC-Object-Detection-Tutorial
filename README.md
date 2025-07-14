# FTC-Object-Detection-Tutorial
Best Limelight 3A Object Detection Tutorial for First Tech Challenge teams who are new to machine learning and want to enhance their performance by Object Detection

- Model used: SSD Mobilenet V2 FPNlite 320*320 from Tensorflow V2 Object Detection model zoo
- Pretrain Dataset: Coco 17
- Recommended training dataset format: TFRecords
- Recommended labeling platform: Roboflow

## **Steps to use:**

1: **Rename** your dataset folder to /tfrecords.
  - Your dataset structure should contain /tfrecords/train/objects.tfrecord, /tfrecords/valid/objects.tfrecord, /tfrecords/test/objects.tfrecord and etc.

2: **Zip and upload your tfrecords folder to /content/tfrecords.zip**

3: Modify Hyperparameters as you wish.

4: Hit run all. You can stop training process early and export the model.

5: If ran into bugs, hit restart runtime

## **FAQ**

Q1: Why my training script keeps aborting when I didn't make it stop?

- A1: Your script might have requested too much RAM thus colab disconnects. Reduce batchsize to 8.

Q2: Why my trained model didn't predict any boundingbox / Why is my model's confidence so low?

- A2: Your model is underfitted. Train with more steps if you stopped early.

Q3: Why my trained model isn't creating good bounding box?

- A3: Either your model is underfitted - refer to A2, or you should enhance your training data. Vary your train data to ensure they are representative of all instance your robot might face, increase number of trianing data, and make more precise labeling

Q4: Why my tflite model's performance is significantly worse than my original tfmodel?

- A4: Your model is not correctly aligned after converting. Although unlikely, manually pick your representative data so they are diverse and truely representative or change quantizing methods.

Developed by Treeman 19600 <3
