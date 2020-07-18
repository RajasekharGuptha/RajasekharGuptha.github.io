---
layout: single
title:  "Color Detection using OpenCV"
date:   2020-07-18
excerpt: Detecting colors in an image using OpenCV
categories: OpenCV
tagline: Color Detection using OpenCV,color detection,opencv,hsv,mask in opencv,trackbars,named window
Author: Rajasekhar Guptha
---


For detecting a particular color using opencv we have to **HSV** values range for that color  

For this tutorial we will be using this image to identify red color

![rose](/assets\images\rose.PNG)

if u know them its alright, otherwise we can find out them using opencv  
let's see how  
> HSV - Hue,Saturation,Value

we need to find out  
**min HSV**-(Hue min,Saturation min,Value min)  and  
**max HSV**-(Hue max,Saturation max,Value max)  
for a color we need to identify

* we will be  using **trackbars** to find out min and max HSV values
```python
#creating new  window for hsv trackbars
windowName="HSV"
cv2.namedWindow(windowName)
```
we need to add 6 trackbars to window
> cv2.createTrackbar(trackbarName=,windowName,value,count,onChange=onchangefunc)  

+ value - initial value when trackbar created
+ count - max value for trackbar
+ onChange - function that will execute when trackbar value is changed
> opencv has only 180 Hue values , 255 saturation and 255 values

```python
def  onchangefunc(dummyArgument):
    #initially let onchange be empty
    pass

cv2.createTrackbar("Hue min", windowName,0,179,onchangefunc) #windowName must be the name of window we created
cv2.createTrackbar("Hue max",windowName,0,179,onchangefunc)
cv2.createTrackbar("Saturation min",windowName,0,255,onchangefunc)
cv2.createTrackbar("Saturation max",windowName,0,255,onchangefunc)
cv2.createTrackbar("Value min",windowName,0,255,onchangefunc)
cv2.createTrackbar("Value max",windowName,0,255,onchangefunc)
```
we successfully created trackbars
![trackbars](/assets\images\hsvTrackbars.PNG)

we have to create a mask based on hsv range for that color  
+ for that we need hsv image 
```python
hsvImage=cv2.cvtColor(image,cv2.COLOR_BGR2HSV)
```
![hsvrose](/assets\images\hsvRose.PNG)

now let's override onchangefunc
+ it will be called whenever any trackbar value is changed. So, get all trackbar values  in it and create a mask

+ **mask** is an image in which our required color will be white color and remaining image in black like this
![mask](/assets\images\mask.PNG)

```python
def  onchangefunc(dummyArgument):
    # get all trackbar values
    hue_min=cv2.getTrackbarPos(trackbarname="Hue min",winname=windowName)
    hue_max=cv2.getTrackbarPos(trackbarname="Hue max",winname=windowName)
    sat_min=cv2.getTrackbarPos(trackbarname="Saturation min",winname=windowName)
    sat_max=cv2.getTrackbarPos(trackbarname="Saturation max",winname=windowName)
    val_min=cv2.getTrackbarPos(trackbarname="Value min",winname=windowName)
    val_max=cv2.getTrackbarPos(trackbarname="Value max",winname=windowName)
    print((hue_min,sat_min,val_min),(hue_max,sat_max,val_max))

    # let's create mask
```
+  adjust values of trackbars to get your required color in white and remaining in black 

![likethis](/assets\images\likethis.PNG)


```python
minHSV=numpy.array([hue_min,sat_min,val_min])
maxHSV=numpy.array([hue_max,sat_max,val_max])
mask=cv2.inRange(hsvImage,minHSV,maxHSV)  
cv2.imshow("mask",mask)
```
I got these values
```
minHSV=(141,175,0)
maxHSV=(179,255,255)
```
now we have to apply this mask to hsv image to get required output

```python
#using bitwise_and operator for applying mask
finalImage=cv2.bitwise_and(image,image,mask=mask)
cv2.imshow("final image",finalImage)
```
![final](/assets\images\finalimage.PNG)

Get complete source code [here](https://github.com/RajasekharGuptha/Blog/blob/master/color_detection.py)
