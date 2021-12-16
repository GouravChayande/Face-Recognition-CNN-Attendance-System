# Automated Attendance System using CNN Models
## _Presented by Sarthak Akre , Gourav Chayande , Nilesh Palandurkar_

#### a) Problem Statement
To design an Automated Attendance Marking System is using Face detection and Recognition technology.

* **Motivation**:
Taking attendance in a large class is cumbersome, repetitive, and it consumes valuable class time. To avoid these problems, an automatic attendance system using deep learning framework can be made. 
The automated attendance system scans the input image and classifies it to the correct face of registered students (or teachers).

* **Feasibility**:
This problem is common and is employed in various other ways such as biometric attendance. But the drawback of those solutions is that they are expensive and require special hardware, while using deep learning cuts cost as it can be performed using a normal camera to scan for images it comes at the cost of accuracy as networks can’t be as accurate compared to other solutions which come equipped with special hardware.

#### b) Data description

For our model we had initially used Yale faces database but due to its low number of images and as we found another dataset, we added Georgia tech face database as well.

Details for both are given below:
(Note: these are from their official pages and some parameters are specified)

* **Yale Faces**:
The Yale Face Database contains 165 grayscale images in GIF format of 15 individuals. There are 11 images per subject, one per different facial expression or configuration: centre-light, w/glasses, happy, left-light, w/no glasses, normal, right-light, sad, sleepy, surprised, and wink.

<div>
<h2></h2>
<img src="https://www.researchgate.net/profile/Adrian-Bors/publication/233545388/figure/fig4/AS:670337972858889@1536832435447/Images-from-the-Yale-face-database-a-Original-data-set-b-Reconstructed-faces-from.ppm"/>
</div>

- Details:
Colour Images: No
Image Size: 320 x 243
Number of unique people: 15
Number of pictures per person: 11 Different Conditions: centre-light, w/glasses, happy, left-light, w/no glasses, normal, right-light, sad, sleepy, surprised, wink
Citation reference: P. N. Bellhumer, J. Hespanha, and D. Kriegman. Eigenfaces vs. fisherfaces: Recognition using class specific linear projection. IEEE Transactions on Pattern Analysis and Machine Intelligence, Special Issue on Face Recognition, 17(7):711--720, 1997. 
For website link click [here.](http://vision.ucsd.edu/content/yale-face-database)

* **Georgia Tech Face Dataset**:
Georgia Tech face database contains images of 50 people taken in two or three sessions between 06/01/99 and 11/15/99 at the Centre for Signal and Image Processing at Georgia Institute of Technology.
All people in the database are represented by 15 colour JPEG images with cluttered background taken at resolution 640x480 pixels. The average size of the faces in these images is 150x150 pixels. The pictures show frontal and/or tilted faces with different facial expressions, lighting conditions and scale. Each image is manually labelled to determine the position of the face in the image. The images are stored in 50 directories s1, ..., s50. In each directory there are 15 images 01.jpg, ..., 15.jpg corresponding to one person in the database. 
Each image is manually labelled to determine the position of the face in the image. The label files contain four integers that describe the coordinates of the face rectangles and a string (s1, ..., s50) indicating the identity of the face.
<div>
<img src="https://www.researchgate.net/profile/Tarun-Gupta-23/publication/342872018/figure/fig2/AS:961257142239233@1606192970283/Sample-Images-from-Georgia-Tech-Face-Database-GTFD-16.ppm" width="600"/>
</div>

- Details of above:
Colour Images: Yes
Image Size: 150x150
Number of unique people: 50
Number of pictures per person: 15 Different Conditions: frontal and/or tilted faces with different facial expressions, lighting conditions and scale Citation reference: Ara V. Nefian and Monson H. Hayes, “Maximum likelihood training of the embedded HMM for face detection and recognition”, IEEE International Conference on Image Processing 2000.
To visit website click [here.](http://www.anefian.com/research/face_reco.htm)

#### C) Implementation

* **Preprocessing the DATASET: Face Detection using OpenCV and cropping**
Now that we have our images and labels assigned correctly we need to "clean up" or pre process the images so that model is trained correctly.

For this purpose we are using openCV. OpenCV has a lot of useful features related to object detection, face detection etc.

<div>
<img src="https://miro.medium.com/max/1156/1*XX8WqHo0lyrgZfTTRQ3ESQ.jpeg" width="400"/>
</div>

We will use a face detection classifier called as Haarcascade.
Haar cascades, first introduced by Viola and Jones in their seminal 2001 publication, Rapid Object Detection using a Boosted Cascade of Simple Features, are arguably OpenCV’s most popular object detection algorithm.

Some Haar cascade benefits are that they’re very fast at computing features, they can detect faces in images regardless of the location or scale of the face and are capable of running in real-time.

<div>
<img src="https://929687.smushcdn.com/2407837/wp-content/uploads/2014/10/sliding_window_example.gif?size=323x475&lossy=1&strip=1&webp=0" height="350"/>
</div>
