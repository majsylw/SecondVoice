---
title: Detection of human body landmarks - MediaPipe and OpenPose comparison
subtitle: OpenPose vs MediaPipe
summary: Read about the difference between OpenPose and MediaPipe. See why we have chosen the latter.



date: "2022-04-01T00:00:00Z"
lastmod: "2022-04-01T00:00:00Z"

featured: false
draft: false

image:

  caption: ''

  focal_point: "Center"
  placement: 2
  preview_only: false

authors:
- Patryk Radzki

tags:
- MediaPipe
- OpenPose
- pose estimation
- landmarks
- face recognition


---





 ## Introduction

Pose estimation is a complex Computer Vision problem that aims to detect the position and orientation of a person or object. This is generally done by predicting the location of specific keypoints, such as hands, hands, facial features, etc., when talking about human position.

Acquiring human pose keypoints from an image and extracting their properties has the potential to enrich the information contained in the datasets at our disposal in the scope of our project. The ability to perceive the shape and movement of parts of a person&#39;s body can be an essential element in making sign language and its properties more comprehensible. You can find more information about the datasets we use [HERE](https://www.hearai.pl/post/11-dataset/)

In order to supplement our data with the human body landmarks detection functionality, the Team decided to conduct a comparison of the popular available dedicated systems and then implement in our project the one that better suits our needs. This article presents the results of the comparison of MediaPipe and OpenPose systems.

## Overview

MediaPipe is a an open-source system from Google for building cross-platform, customizable ML solutions for live and streaming media. MediaPipe is currently under active development and contains extensive documentation including demos and examples of using the built-in functionality. MediaPipe is available in alpha at v0.7 at the time of the test. You can find more information about the MediaPipe here [1].

OpenPose is an open-source real-time multiple-person detection system, to jointly detect human body, palm, facial, and foot keypoints . It is authored by [Ginés Hidalgo](https://www.gineshidalgo.com/), [Zhe Cao](https://people.eecs.berkeley.edu/~zhecao), [Tomas Simon](http://www.cs.cmu.edu/~tsimon), [Shih-En Wei](https://scholar.google.com/citations?user=sFQD3k4AAAAJ&amp;hl=en), [Yaadhav Raaj](https://www.raaj.tech/), [Hanbyul Joo](https://jhugestar.github.io/), and [Yaser Sheikh](http://www.cs.cmu.edu/~yaser). This project is highly dependent on the CMU Panoptic Studio dataset. OpenPose is maintained by [Ginés Hidalgo](https://www.gineshidalgo.com/) and [Yaadhav Raaj](https://www.raaj.tech/) and also includes demos and examples of using the built-in functionality. The last OpenPose release is available in v1.7.0 dated 17 Nov 2020 at the time of the test. You can find more information about the OpenPose here [2].

## Comparative criteria and the test results

#### Assumptions

The parameters used to perform the comparison are focused on the ability to recognize Sign Language, which means that the test results cover only a portion of the range of capabilities of the involved systems. The input data for the test consists of videos of one person with the profile turned towards the camera; the camera covers at least part of the body from waist to head and includes hands; the person in the video presents words/sentences in Polish Sign Language; the background is not affected by any external factors. The video parameters used for the test were selected based on the video properties of our datasets and have a resolution of 1920x1080px and a frame rate of 30 FPS.

#### Features
In order to detect the features of Sign Language, from among the available pipelines, we have applied the following solutions:

| MediaPipe | OpenPose |
| --- | --- |
| Holistic mode including: | Real-time 2D multi-person keypoint detections mode including: |
|33 body/foot landmarks|15, 18, 27 body/foot landmarks|
|21 hand landmarks – each hand | 21 hand landmarks – each hand |
|468 facial landmarks|70 facial landmarks|

| ![](img1.png) | ![](img2.png) |
| ![](img3.png) | ![](img4.png) |
| ![](img5.gif) | ![](img6.png) |

## Configuration and setup

The following hardware configuration was used during the test:

- **OS**  : Ubuntu 20.04 LTS

- **Processor**  : Intel(R) Xeon(R) Platinum 8270 CPU @ 2.70GHz – 26 cores
- **GPU**  : NVIDIA GeForce RTX 2080 Ti with 11 GB RAM x2
- **Programming Language**  : Python

To conduct the comparative test, the default parameters recommended for a given system were used, allowing for the detection of the pose, hands and face. The exception is the size of the input resolution in order to find a compromise between performance and accuracy of the applied solution.

### Accuracy

In order to check the accuracy of MediaPipe and OpenPose, we tested videos of Polish Sign Language, taking into account various conditions and parameters that could hypothetically interfere with landmarks detection under the described assumptions. The following conditions/parameters were tested:

- Default conditions,
- Profile angle view,
- Motion speed,
- Light intensity,
- Self-occlusions: Hand-hand overlap,
- Self-occlusions: Hand-face overlap.

#### Default conditions

Figure 1 shows the video frame of the default video. It is worth to note that there are only two kinds of perspective action views in Sign Language videos: front overview and profile angle view. Since the front overview is definitely more common in datasets available to us, we utilize the mentioned frame description approach as the default.

As can be seen, with the frames showing a relatively static image, despite the elbows going slightly beyond the edge of the camera view, both solutions perform equally well in landmark detection.

![](img7.jpg)

Fig.1 Default perspective – OpenPose (left) vs MediaPipe (right)

#### Light intensity

In order to experiment with the effect of lighting on the detection of landmarks, we decided to use very unfavorable lighting conditions due to the lack of noticeable differences in the case of a slight deterioration of the lighting of the recorded video. To minimize the potential influence of other factors on the obtained results, only relatively static images were analyzed. As can be seen from the example pictures (Fig. 2, Fig. 3) MediaPipe does slightly better in this aspect.

![](img8.jpg) 

Fig.2 Effect of light intensity on OpenPose performance

![](img9.jpg) 

Fig.3 Effect of light intensity on MediaPipe performance

#### Profile angle view

Figures 4 and 5 shows the perspective video frames from the profile angle. Similar to the previous examples (Fig.1-3), considering only relatively static images both solutions also have no problem with landmark detection if we do not take into account body parts overlapping, which becomes more apparent with this perspective.

![](img10.jpg) 

Fig.4 Profile angle perspective – OpenPose (left) vs MediaPipe (right)

![](img11.jpg) 

Fig.5 Profile angle perspective – OpenPose (left) vs MediaPipe (right)

#### Motion speed

As part of this experiment, the influence of motion speed on the detection of landmarks was checked. By performing the tests, it could be seen that while body pose estimation appeared to be reliable, the hand position estimation did not work well in 30 FPS videos due to motion blur around the hand. The effect can be offset by using a higher frame rate, but it is difficult to obtain such a dataset [link do postu o datasetach].

In this test MediaPipe shown significantly more robustness to blur than OpenPose. Figures 6-9 show the effect of motion blur on landmark detection.

![](img12.jpg) 

Fig.6 Motion blur in landmark detection – OpenPose (left) vs MediaPipe (right)

![](img13.jpg) 

Fig.7 Motion blur in landmark detection – OpenPose (left) vs MediaPipe (right)
![](img14.jpg) 

Fig.8 Motion blur in landmark detection – OpenPose (left) vs MediaPipe (right)

#### Self-covering: Hand-hand overlap

Figures 9 and 10 show the effect of hand-hand overlap on landmark detection. The test showed issues with accurate landmark determination for both MediaPipe and OpenPose, disregarding slight interference due to motion blur, MediaPipe performed better in determining hand position (Fig. 9, Fig.10) and OpenPose more accurately represented pose position (Fig. 4, Fig.10).

![](im15.jpg) 

Fig.9 Hand-hand overlap – OpenPose (left) vs MediaPipe (right)

![](img16.jpg) 

Fig.10 Hand-hand overlap – OpenPose (left) vs MediaPipe (right)

#### Self-covering: Hand-face overlap

The last test examined how OpenPose and MediaPipe deal with hand-face overlapping. As can be seen in Figure 11, excluding the motion blur interference, both perform very well at estimating landmark positions when the face is partially hidden.

![](img17.jpg) 

Fig.11 Hand-face overlap – OpenPose (left) vs MediaPipe (right)

#### Computation Speed

The purpose of the experiment was to test the differences between the computational performance of OpenPose and MediaPipe and to compare the hardware resources needed to do so. The study took into account the needed amount of available computing resources in the form of GPU/CPU usage, and the real-time video processing speed expressed in frame rate per second [FPS].

The experiment was conducted on 6 different input resolutions. The input resolutions used are:
 -1×64px, -1×128px, -1x368px, -1x480px, -1x608px for OpenPose and 256x256px for MediaPipe.

The -1 means that that the resolution will be adapted to maintain the aspect ratio of the input source. E.g., -1x368, 656x-1, and 656x368 will result in the same exact resolution for 720p and 1080p input images.

The default resolution of the pose estimation model is -1x368 for OpenPose and 256x256px for MediaPipe. However, in the case of hands and face, regions are extracted from the image for transfer to the appropriate models using the appropriate image resolution (depending on the solution) for the corresponding region.

The test results are shown in the diagrams below.

![](img18.jpg) 

Fig 12. Frame Rate by Resolution

![](img19.jpg) 

Fig 13. GPU Memory Usage by Resolution

As can be seen from Fig. 12, increasing the input image resolution slightly affected the processing speed with OpenPose. The image processing speed for the default settings was 16 FPS and fluctuated by 1-2 frames during video processing. In addition, increasing the resolution of the input image was associated with a significant increase in the demand for GPU Memory (Fig. 13), which made it impossible to use OpenPose with the parameters that declared the highest accuracy - 1312x736px resolution, with the hardware resources available to us.

The change of the input image resolution above the default (-1x368px) slightly improved the accuracy of detecting the human pose landmarks. The use of -1x608px resolution required the implementation of an additional NVIDIA GeForce RTX 2080 Ti GPU and was the maximum supported resolution – via 3xGPU.

The reduction of the input image resolution slightly deteriorated the obtained results. At the threshold (-1x64), there was a complete loss of the ability to determine the characteristic points of the human body.

Image processing with MediaPipe in the default settings did not cause a drop in the FPS of the processed video. Due to the lack of a decrease in FPS, the resolution parameter was not subjected to further testing.

Due to the use of different types of acceleration (CPU / GPU), we are not able to objectively compare both solutions. On the home page of MediaPipe, the _Performance Benchmarking_ section is not yet complete, however such tests have already been carried out. The discussed pipeline configuration shows FPS drops within the limits of Google Pixel 2 - 18 FPS, Samsung S9+ - 20 FPS, 15-inch MacBook Pro 2017 - 15 FPS [3]. Taking into account the above data, it can be concluded that the MediaPipe model is more efficient than the corresponding OpenPose model.

## Summary

The above test demonstrated the strong capabilities of both MediaPipe and OpenPose. Both solutions have good accuracy in determining the landmarks of the human body when rendering relatively static images; with poor lighting or no matter if the signer is facing the camera directly. In terms of dealing with covering, MediaPipe and OpenPose work satisfactorily, but the accuracy of operation in the case of hand-hand or hand-face overlap should be considered, especially above 50% of the coverage area. The biggest problem with both solutions was motion blur, which, along with the increase in the speed of the motion, resulted in greater errors in representing the position of landmarks, even to the point of complete loss of detection. In this area, MediaPipe proved to be much more effective in dealing with the disruptions.

The landmark detection using OpenPose results was generally good and promising, but not satisfying, due to the many challenges the approach faced: First, working with OpenPose required us to review older available versions of the library due to compatibility issues with CUDA and cuDNN, and errors in the instructions for installing OpenPose on a container. Second, working with OpenPose was very slow relative to MediaPipe. It takes a relatively long time to process videos and takes a lot of computing power even on decent machines. Therefore, we decided to use MediaPipe in our project.

Moreover, due to frame rate limitations in the available datasets, we were not able to reduce motion blur, so we implemented additional landmark estimation methods, which may be the subject of another material 😊.

#### Sources:

[1] [https://google.github.io/mediapipe/](https://google.github.io/mediapipe/) (Access 25.03.2022)

[2] [https://cmu-perceptual-computing-lab.github.io/openpose/web/html/doc/index.html](https://cmu-perceptual-computing-lab.github.io/openpose/web/html/doc/index.html) (Access 25.03.2022)

[3] [https://ai.googleblog.com/2020/12/mediapipe-holistic-simultaneous-face.html](https://ai.googleblog.com/2020/12/mediapipe-holistic-simultaneous-face.html) (Access 25.03.2022)






