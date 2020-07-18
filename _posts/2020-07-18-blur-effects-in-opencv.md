---
layout: single
title:  "Types of Blur in OpenCV"
date:   2020-07-18
excerpt: Different ways to achieve blur in opencv
categories: OpenCV
tagline: gaussianblur in opencv,gaussian blur in opencv,average blur in opencv,bilateral filters in opencv,blur types in opencv,different types of blur in opencv
Author: Rajasekhar Guptha
---

### Averaging
```python
cv2.blur(image=image,ksize=(3,3))
```
average blur with ksize 3 and 7

![average](/assets\images\avgkernel.PNG)

change kernel size for blur depth

#### Note:- 
No need to bother about kernel and kernelsize just remember them as a factor for blur depth

### Gaussian Blur
+ kernel size should be positive and odd
```python
 gaussian=cv2.GaussianBlur(src=image,ksize=(5,5),sigmaX=0)
 # we should give sigmaX & sigmaY, if only x is given then y will bw taken same as of x
```
again all these are factors for blur effect

![gaussian](/assets\images\gauss.PNG)


### Median Blur
+ Reduces noise in image
+ kernel size shouldbe positive and odd

```python
median = cv2.medianBlur(image,3)
median2 = cv2.medianBlur(image,7)
```
![median](/assets\images\median.PNG)

### Bilateral Filter
+ Bilateral Filter effective in noise removal while keeping **edges sharp**

bilateralFilter	(	InputArray 	src,
OutputArray dst,
int d,
double sigmaColor,
double	sigmaSpace,
#int borderType = BORDER_DEFAULT)
```python
bilateralfilter_blur = cv2.bilateralFilter(image, 9, 75, 75)
```

![types1](/assets\images\avggaussian.PNG)
![types2](/assets\images\medbilateal.PNG)
