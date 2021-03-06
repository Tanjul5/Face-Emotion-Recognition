Face-Emotion-Recognition

Live Class Monitoring System(Face Emotion Recognition)

Emotion recognition is the process of identifying human emotion. People vary widely in their accuracy at recognizing the emotions of others. Use of technology to help people with emotion recognition is a relatively nascent research area. Generally, the technology works best if it uses multiple modalities in context. To date, the most work has been conducted on automating the recognition of facial expressions from video, spoken expressions from audio, written expressions from text, and physiology as measured by wearables.
Facial expressions are a form of nonverbal communication. Various studies have been done for the classification of these facial expressions. There is strong evidence for the universal facial expressions of seven emotions which include: neutral happy, sadness, anger, disgust, fear, and surprise. So it is very important to detect these emotions on the face as it has wide applications in the field of Computer Vision and Artificial Intelligence. These fields are researching on the facial emotions to get the sentiments of the humans automatically.

Problem Statement

The Indian education landscape has been undergoing rapid changes for the past 10 years owing to the advancement of web-based learning services, specifically, eLearning platforms.
Global E-learning is estimated to witness an 8X over the next 5 years to reach USD 2B in 2021. India is expected to grow with a CAGR of 44% crossing the 10M users mark in 2021. Although the market is growing on a rapid scale, there are major challenges associated with digital learning when compared with brick and mortar classrooms. One of many challenges is how to ensure quality learning for students. Digital platforms might overpower physical classrooms in terms of content quality but when it comes to understanding whether students are able to grasp the content in a live class scenario is yet an open-end challenge. In a physical classroom during a lecturing teacher can see the faces and assess the emotion of the class and tune their lecture accordingly, whether he is going fast or slow. He can identify students who need special attention.
Digital classrooms are conducted via video telephony software program (ex-Zoom) where it???s not possible for medium scale class (25-50) to see all students and access the mood. Because of this drawback, students are not focusing on content due to lack of surveillance.
While digital platforms have limitations in terms of physical surveillance but it comes with the power of data and machines which can work for you. It provides data in the form of video, audio, and texts which can be analyzed using deep learning algorithms.
Deep learning backed system not only solves the surveillance issue, but it also removes the human bias from the system, and all information is no longer in the teacher???s brain rather translated in numbers that can be analyzed and tracked.
I will solve the above-mentioned challenge by applying deep learning algorithms to live video data. The solution to this problem is by recognizing facial emotions.
I have built a deep learning model which detects the real time emotions of students through a webcam so that teachers can understand if students are able to grasp the topic according to students' expressions or emotions and then deploy the model. The model is trained on the FER-2013 dataset .This dataset consists of 35887 grayscale, 48x48 sized face images with seven emotions - angry, disgusted, fearful, happy, neutral, sad and surprised.

Dataset Information:

I have built a deep learning model which detects the real time emotions of students through a webcam so that teachers can understand if students are able to grasp the topic according to students' expressions or emotions and then deploy the model. The model is trained on the FER-2013 dataset .This dataset consists of 35887 grayscale, 48x48 sized face images with seven emotions - angry, disgusted, fearful, happy, neutral, sad and surprised. Here is the dataset link:- https://www.kaggle.com/msambare/fer2013

1) Using DeepFace

DeepFace is a deep learning facial recognition system created by a research group at Facebook. It identifies human faces in digital images. The program employs a nine-layer neural network with over 120 million connection weights and was trained on four million images uploaded by Facebook users.The Facebook Research team has stated that the DeepFace method reaches an accuracy of 97.35% ?? 0.25% on Labeled Faces in the Wild (LFW) data set where human beings have 97.53%. This means that DeepFace is sometimes more successful than the human beings.

![image](https://user-images.githubusercontent.com/88198641/166412960-6bcfe31d-d55e-44c3-a9fd-5eb2f9e0e749.png)

We imported the image above which looks angry and our model gives us ???36 years old white angry Man??? this result. 

2) Using Transfer Learning Resnet50

Since the FER2013 dataset is quite small and unbalanced, we found that utilizing transfer learning significantly boosted the accuracy of our model. ResNet50 is the first pre-trained model we explored. ResNet50 is a deep residual network with 50 layers. It is defined in Keras with 175 layers. We replaced the original output layer with one FC layer of size 1000 and a softmax output layer of 7 emotion classes. We used Adam as our optimizer after training for 50 epochs using Adam and a batch size of 785, we achieved 63.11% accuracy on the test set and 67% on the train set. There is much less over-fitting. We have taken epochs as 50. Once the threshold is achieved by the model and we further tried to train our model, then it provided unexpected results and its accuracy also decreased. After that, increasing the epoch would also not help. Hence, epochs play a very important role in deciding the accuracy of the model, and its value can be decided through trial and error.

 ![image](https://user-images.githubusercontent.com/88198641/166414067-5b5f1be0-df3c-4963-8f08-2dd083444607.png)


3) Xception

Xception architecture is a linear stack of depth wise separable convolution layers with residual connections. This makes the architecture very easy to define and modify; it takes only 30 to 40 lines of code using a high level library such as Keras or Tensorflow not unlike an architecture such as VGG-16, but rather un- like architectures such as Inception V2 or V3 which are far more complex to define. An open-source implementation of Xception using Keras and Tensorflow is provided as part of the Keras Applications module2, under the MIT license. We used Adam as our optimizer after training for 70 epochs using Adam and a batch size of 785, we achieved 64% accuracy on the test set.

![image](https://user-images.githubusercontent.com/88198641/166414130-14a6eb84-f636-4178-a018-e00aa874a287.png)


4) Custom Deep CNN

A Convolutional Neural Network (ConvNet/CNN) is a Deep Learning algorithm which can take in an input image, assign importance (learnable weights and biases) to various aspects/objects in the image and be able to differentiate one from the other.
We designed the CNN through which we passed our features to train the model and eventually test it using the test features. To construct CNN we have used a combination of several different functions such as sequential, Conv (2D), Batch Normalization, Maxpooling2D, Relu activation function, Dropout, Dense and finally softmax function.

We used Adam as our optimizer after training for 70 epochs using Adam with minimum learning rate 0.00001 and a batch size of 785, we achieved 69 % accuracy on the test set and 74% as train accuracy.
One drawback of the system is the some Disgust faces are showing Neutral .Because less no. of disgust faces are given to train .This may be the reason.
I thought it was a good score should improve the score.
Thus I decided that I will deploy the model.

![image](https://user-images.githubusercontent.com/88198641/166414173-c7cf4960-360a-40db-91bb-98a7dfea897f.png)


Realtime Local Video Face Detection
 
We created patterns for detecting and predicting single faces as well as multiple faces using OpenCV video capture in a local webcam. Some of the detected face emotion are as follows:

![Screenshot (81)](https://user-images.githubusercontent.com/88198641/166415086-f0562133-a820-47ae-959c-7fb0898ca043.png)

![Screenshot (82](https://user-images.githubusercontent.com/88198641/166415115-a65b4098-231e-4678-9e91-a524a9cb6587.png)


Deployment of Streamlit WebApp in Heroku and Streamlit

We deployed the app in Heroku if you saw in the starting section of GitHub repo you see the all the requirement files are there for creating an app on Heroku of name ???face-emotion-recognition4???. but due to high slug size the buffering takes time so we have run our app working on local and it ran properly and app is also fine also we???ve included video on GitHub repo

Heroku Link:-  https://face-emotion-recognition4.herokuapp.com/

Conclusion

We explored several models including shallow CNNs, DeepFace, ResNet50, and Xception. To alleviate FER2013???s inherent class imbalance, we employed class weights, data augmentation, and auxiliary datasets. By ensemble seven models we achieved 77% training accuracy and 69% accuracy for CNN model. Additionally, we demonstrated that FER models could be applied in the real world by developing a web application with real-time recognition speeds. It was interesting project and we learn lot from this project.

