# AI_Video_Model-
-----> Run the app using python app.py -----> Upload or capture a video for sentiment analysis. -----> Get a result using the piechart.

• Training the model for Facial Expression Detection

File name EmotionDetection.ipynb
DataSet used is Fer2013 data set which contains more than 35K images and 7 types of emotions. For this project we will be considering 5 emotions.
In this data set 4848 pixel grayscale images are flattened. So, we will reshape the data into 4848 pixels. #LINE 30
I have split the data for training and validation using sklerarn’s traintestsplit method and then have normalized the dataset. #Line 33/34
Using ImageDataGenerator it will augment the datasets with its flip images aswell.
Then for training the model I have used four convolution and two dense layers.
In model compilation Ihave used Adam optimizer.
I have also used callbacks that will save the model when high validation accuracy is achieved
I have the model in json format.
• Video analysis

Here the main file is predictemt.py

There are four function in this file that will be used in our project

Pred(): a. It takes image as an input and then it will convert it into grayscale b. Then using OpenCV’s cascade classifier it will detect the face of the person. c. Then we will only use the face for predicting and if the face is not found in the image than It will return 0. d. Then face image will be resized accourding to the size acceptable by our model.

Vidframe(): a. It takes an video as a input and then it will generate frames for that video. b. Each frame will be named and stored in output folder. c. Then after for every image it will run the pred function and will return the emotion and face of an person if found.

Ssimscore1() and removeout(): a. Ssimscore1 is used to compare the faces that are returned by the pred function b. Removeout is used for removing the output directory.

• App.py flask app

In this file first the CNN Emotion detection model is loaded that is stored in json file and also assigned the weights
Here the main function is upload that is used for uploading video
Then the vidframe function is run on the video that will return the emotion and faces
SmileIndex is calculated by dividing total happy images to total images
Ssimscore is calculated for every faces and if the score is less than 0.6 than we will say that the posture is not good.
Then after we will create a pie chart for the emotions and we will return that pie chart to our predict template.
