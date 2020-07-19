---
layout: single
title:  "OpenCV Basics"
date:   2020-07-18
excerpt: Basic operations like resize,crop,drawing over images,blur effects etc in OpenCV
categories: OpenCV
tagline: OpenCV basics,opencv,opencv in a nutshell,resize,crop,blur,average blur ,gaussian blur in opencv
Author: Rajasekhar Guptha
---


### Reading Images
imread(filename)  
```python
image=cv2.imread("images/rose.jpeg")
```
cv2 library works on images as numpy matrices,
if you want to see it just print the image like  
```python
print(image)
```
To display image,  

cv2.imshow(windowname,image_matrix(cv2 image))
```python
cv2.imshow("image",image)
```
![imshow](/assets/images/rose1.PNG)  

the image will be blinked  to see the image we need to add delay  

cv2.waitKey(milliseconds)  
 if we give 0 then it is infinite delay
```python
cv2.waitKey(0) 
cv2.waiKey(1000) # delay of 1 sec
```

### Blur
blur_image=cv2.blur(source_image,kernel)  
we don't need to worry about kernel just change values to get desired depth of blur

```python
blur_image=cv2.blur(image,(3,3))  # average blur
```
![blur](/assets/images/blur.PNG)  
To know more about different types of blur available in cv2 [see this]({{site.baseurl}}/opencv/2020/07/18/blur-effects-in-opencv.html)


### color convertion

Usually we use RGB channels but in cv2 color channels convention is BGR  
we will oftenly use grayscale images  

```python
gray_scale=cv2.cvtColor(image,cv2.COLOR_BGR2GRAY)
```
![gray](/assets/images/gray.PNG)
To convert to RGB  
```python
rgb_image=cv2.cvtColor(image,cv2.COLOR_BGR2RGB)
```
To HSV
```python
hsvImage=cv2.cvtColor(image,cv2.COLOR_BGR2HSV)
```
![hsv](/assets\images\hsvRose.png)

and many more modes available  
### shape function
cv2 module has shape function that gives us  
height  
width  
and no.of color channels ex: 3 for RGB
```python
height=image.shape[0]
width=image.shape[1]
```
### Resize
cv2.resize(source,(width,height))
```python
resized_image=cv2.resize(image,(width/2,height/2))
```
![resize](/assets/images/resize.PNG)

### crop
as we know cv2 image objects are numpy arrays, we can crop images using array properties  
image[(height)from:to,(width)from:to]
```python
cropped_image=image[0:400,0:400]
```
![crop](/assets/images/crop.PNG)

## Drawing on Images
### Line
cv2.line(image,(x1,y1),(x2,y2),color,thickness)
```python
cv2.line(image,(0,0),(100,100),(0,0,0),2)
```
![line](/assets/images/line.PNG)

### rectangle
cv2.rectangle(image,(x1,y1),(x2,y2),color,thickness)
```python
cv2.rectangle(image,(10,10),(190,100),(255,255,255),2)
```
![rect](/assets/images/rect.PNG)


### circle
```python
cv2.circle(image,center=(100,100),radius=50,color=(255,255,255),thickness=1)
```
![circle](/assets/images/circle.PNG)

similarly we can draw ellipse,polygon

### Text
```python
cv2.putText(image,text="Text",org=(200,200),fontFace=cv2.FONT_ITALIC,fontScale=1,color=(255,0,0),thickness=2)
```
![text](/assets/images/text.PNG)

cv2 also has some other fonts

## Canny Edge Detection
```python
canny=cv2.Canny(image=image,threshold1=100,threshold2=102)
canny2=cv2.Canny(image=image,threshold1=150,threshold2=50)

#try different threshold values
```
![canny](/assets/images/canny.PNG)

## Listen to Mouse
```python
cv.setMouseCallback(windowName,functionToExecute)
```
def functionToExecute(event,x,y,flags,param):

+ (x,y)-pixel positions of mouse click
+ event - type of mouse action  
   + EVENT_LBUTTONDOWN - left mouse buttton down
   + EVENT_LBUTTONCLICK - left button click
   
    and there are lot more other events    