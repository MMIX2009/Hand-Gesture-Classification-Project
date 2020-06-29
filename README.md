# Hand-Gesture-Classification-Project

Classification of hand gestures using accelerometer readings from an intertial motion unit. The accelerometer values are captured in 2D spectrogram images. The use of spectrograms to represent the gestures captures the temporal nature of the data.

# The dataset
There are 64 samples x 3 axis (x, y, and z) for a total of 192 accelerometer values sampled at a rate of xx Hz from a wrist-mounted MPU6050 IMU.
There are eight gesture captured: ['Hook','Idle','Jab','Okay','Stop','Thumbs Up','Uppercut','Wave'] with 50 to 60 sets of datapoints for each class/gesture. 
The dataset has 437 rows in the entire datasets with  This should be enough to get reasonable accuracy from the image classification model. 

 enough information to classify eight distinct hand gestures. 

# Areas of improvement:
More data: Ideally, there should be much more data available from more than a single subject to account for variations in how people perform those gestures. 
More Subjects: Another possible improvement is to generate synthetic data from the existing dataset since a preliminary analysis indicates that the x-, y-, z- axis from a given gesture are correlated.
More sensors: the addition of gyroscope sensor data which is also available on the MPU6050 can help improve the accuracy of the model prediction although it would also add to the training time

