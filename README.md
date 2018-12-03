# 475project
**The final project of EECS 475 from Northwestern University**

**Content**: Real-Time Human Computer Interaction ASL Showing

**Author**: Yunan Wu, Jingyan Zhang, Yifan Le, Yaokao Yang

**Organization**: Northwestern University EECS 495

**Time**: 12/2/2018

**video_address**: 

## 1. American Sign Language<br>
 American Sign Language (ASL) is a complete, complex language that employs signs made by moving the hands combined with facial expressions and postures of the body. It is the primary language of many North Americans who are hearing impaired and is one of several communication options used by people who are deaf or hard-of-hearing. Normally, sign languages used in daily communication are hand gesture version of phases and even sentences. Yet, there are situations when letters themselves are needed to emphasize or just to spell words. For instance, knowing how to spell words is fundermental for children who are congenitally deaf, and knowing how to spell them in hand gestures is the best way to remember words. Thus out of necessity, comes American Sign Language Alphabets, seen below.<br>
 <img width="500" height="300" src="https://github.com/NancyWu2168/475project/blob/master/picture/gesture.png">
 
 Just like English, Each hand gesture in American Sigh Language Alphabets correspond with each one in English alphabets. twenty-six hand gestures differ in shape. As is shown in figure, there are gestures like fist and half fist, sure it is easy for people who master ASL to recognize immediately when seeing them. However, for people who are just starting to learn or have no idea what it is at all, it will be tremendously difficult to understand. In fact, this project is originated from a rising phenomenon that an increasing number of American parents have trouble in teaching their  hearing impaired children English. This project is meant to help these people, which is a large number of for sure, to understand, and even start to learn and practice ASL alphabets. It is believed that the initiation of this project is mutually beneficial for both sides.<br>
 So what we accutrally do in this project is a recognition of ASL alphabets (training images like below) and find the corrresponded English alphabet. By recognizing the gestures made by human, we can traslate them into English which is more familiar to us in **real time**. Thus, once applied in real life, people who use it can understand those geatures' meaning immediately and communicate without delay and misunderstading.<br>
 
 <div align=center>
 
 <img width="800" height="300" src="https://github.com/NancyWu2168/475project/blob/master/picture/ASL.png">
 
 </div>

## 2. Convolutional Neural Network<br>
Convolutional neural network (CNN) is a class of deep, feed-forward artificial neural network applied to analyzing visual  imagery using a variation of multilayer perceptrons designed to require minimal preprocessing. In our project, a CNN called  AlexNet was applied, which improves it performance by deepening its model. (see in [Alexnet_RGB](https://github.com/NancyWu2168/475project/blob/master/cnn_alexnet_version1.0_RGB.ipynb))The model architecture is shown below.

<div align=center>
 
<img width="500" height="500" src="https://github.com/NancyWu2168/475project/blob/master/picture/model_architecture.png">

</div>
We acquired 29,000 color pictures of American sign language (ASL) from the database, 1,000 for each of 29 characters  (including alphabet A to Z, space, delete and nothing). 800 pictures for each character are randomly selected to train the  models, while the rest are used for testing it. The results indicates that the models performed well.  
However, when applied to ASL photo taken by ourselves, the models did not achieve a high accuracy. As far as we are concerned, several factors including illumination intensity(img_1), color of the background(img_2), position and size of the hand may contribute to the uncertainties. Like the images below,, which cannot be classified correctly, while img_3 can be correctly detected.

<img width="250" height="300" src="https://github.com/NancyWu2168/475project/blob/master/picture/light_intensity.jpg"><img width="250" height="300" src="https://github.com/NancyWu2168/475project/blob/master/picture/complex_background.png"><img width="250" height="300" src="https://github.com/NancyWu2168/475project/blob/master/picture/good_class.jpg">


## 3. Gray Processing<br>
In order to improve the performance, we transformed all RGB images used for training and testing into grayscale images with weighted average. Training the pre-processed pictures in the same method as we did before. The results turned out to be significantly better than  those without preprocessing.
(see in [Alexnet_gray](https://github.com/NancyWu2168/475project/blob/master/cnn_alexnet_version2.0_GrayScale.ipynb))
## 4. Real-time Recognition<br>
Firstly, when we train the model in step 3 and 4, the optimal weights and models are reserved in [.json](https://github.com/NancyWu2168/475project/tree/master/model%20and%20weights%20in%20RGB) and .h5 files(too large to upload), which can be used in real-time detection without training them from scratch again.
By making use of open-CV, we realized real-time recognition of ASL, where the sign languages are photographed by  the camera of the computer and simultaneously recognised by the trained models. That function enables inputing a sequence of  characters into the computer by performing ASL. Tkinter is used as the platform to do this human computer interaction. Look at 
 [test_file](https://github.com/NancyWu2168/475project/blob/master/test.ipynb)
