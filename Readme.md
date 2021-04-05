# udacity project: Traffic_Sign_classifier 

Traffic_Sign_classifier is the third udacity task. We will learn deep learning models using german traffic sign dataset. I proceeded with the code using colab.



The goals / steps of this project are the following:

- Load the data set
- Explore, summarize and visualize the data set
- Design, train and test a model architecture
- Use the model to make predictions on new images
- Analyze the softmax probabilities of the new images
- Summarize the results with a written report

### step1: dataset summary & exploration

#### Dataset summary

The size of the traffic signs data set was calculated using the  numpy library. The labels are in the signnames.csv file. I used the csv  library to get the traffic sign label.

Number of training examples = 34799
Number of Validation examples = 4410
Number of testing examples = 12630
Image data shape = (32, 32, 3)
Number of classes = 43

#### An exploratory visualization of the dataset

In the training set, one picture was plotted for each label.  Visualization of the data set indicates how many pictures each label  contains.

### Step 2: Design and Test a Model Architecture

#### Pre-process the Data Set (normalization,grayscale)

I did nomalization to prevent differences in the scale of the feature. 

I tried to convert it to gray scale again.This is because it eliminates  noise and speeds up computational processing while improving accuracy.   But I didn't do it because there was an error.

LeNet from Lesson 8 was used, and the number of labels was modified from 10 to 43.

|      Layer      |                 Description                  |
| :-------------: | :------------------------------------------: |
|      Input      |              32x32x3 RGB image               |
|  Convolution 1  | 1x1 stride, VALID padding, output = 28x28x6  |
|      RELU       |                                              |
|   Max pooling   | 2x2 stride, VALID padding, output = 14x14x6  |
|  Convolution 2  | 1x1 stride, VALID padding, output = 10x10x16 |
|      RELU       |                                              |
|   Max pooling   |  2x2 stride, VALID padding, output = 5x5x16  |
|     Flatten     |                 output = 400                 |
| Fully connected |          input = 400, output = 120           |
|      RELU       |                                              |
| Fully connected |           input = 120, output = 84           |
|      RELU       |                                              |
| Fully connected |           input = 84, output = 10            |

To train the model I used 70 epochs, a batch size of 128 and a learning rate of 0.001.

I used softmax_cross_entropy_with_logits to optimize. Finally I applied minimize to the AdamOptimizer of the previous result.

Train Accuracy = 1.000
Valid Accuracy = 0.933
Test Accuracy = 0.920

### Step 3: Test a Model on New Images

I have received new pictures to test new images.

The test accuracy was 86 percent.

According to a new image, five out of seven were correct.

image1.png - Prediction: No entry
image2.png - Prediction: Yield
image3.png - Prediction: No entry
image4.jpg - Prediction: No entry
image5.png - Prediction: Stop
image6.png - Prediction: Yield
image7.png - Prediction: Keep right



If we increase the amount of images and convert to gray scale, we can get better results.