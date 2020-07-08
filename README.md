# Hand-Gesture-Classification-Project

Classification of hand gestures using accelerometer readings from an intertial motion unit. The accelerometer values are captured in 2D spectrogram images. The use of spectrograms to represent the gestures captures the temporal nature of the data. The classification will be performed by AWS Sagemaker ResNet image classifier.

# Applications
This particular dataset contains three boxing strikes (jab, hook, uppercut) and four common gestures (thumbs up, wave, stop, okay) and a generic "idle" gesture where none of the other seven gesture is performed.
The idea is to be build a prediction model that will allow an application (game, training tool, etc.) to determine what gesture is being perform and take the appropriate action such as measuring the conformance to certain key performance indicators such as speed, power, accuracy, style, etc.

# The dataset
There are 64 samples x 3 axis (x, y, and z) for a total of 192 accelerometer values sampled at a rate of xx Hz from a wrist-mounted MPU6050 IMU.
There are eight gesture captured: ['Hook','Idle','Jab','Okay','Stop','Thumbs Up','Uppercut','Wave'] with 50 to 60 sets of datapoints for each class/gesture. 
There are 437 rows in the entire dataset. I think that will be enough to get reasonable accuracy (better than 70%) from the image classification model. 

Using a custom Python script, I created the spectrograms for each gesture's x, y, z accelerometer samples. The three spectrogram images were then concatenated horizontally to reduce the number of images to be processed by the deep learning network classifier. These images are stored in the corresponding gesture subfolder inside the spectrograms folder.

# Preperation for AWS SageMaker
The spectrogram images for each of the 436 gestures were uploaded to an AWS S3 bucket. Also, the included .lst files which indicate to SageMaker the 80/20 split between training and test images were uploaded to the same S3 bucket.

# Areas of improvement
More data: Ideally, there should be much more data available from more than a single subject to account for variations in how people perform those gestures. 
More Subjects: Another possible improvement is to generate synthetic data from the existing dataset since a preliminary analysis indicates that the x-, y-, z- axis from a given gesture are correlated.
More sensors: the addition of gyroscope sensor data which is also available on the MPU6050 can help improve the accuracy of the model prediction although it would also add to the training time

# Prior work
In a previous project, I had successfully classified the eight gestures by using a deep learning classifier (Tensorflow/Keras). I did not use a convolutional neural network and the input data was flattened thus losing the temporal and spatial relationships between the corresponding x-, y-, z-axis samples. 
The hope is that this approah using SageMaker ResNet will be an improvement that will provide a good foundation for a more sophisticated classifier with more gestures/classes and sensor samples.

