---
layout: single
title:  "Shape Detection using OpenCV"
date:   2020-07-19
excerpt: Detecting polygon type and finding area,perimeter also drawing bounding rectangle,minimum Enclosing Circle.
categories: OpenCV
tagline: OpenCV basics,polygon type detection,opencv,area of polygon,perimeter of polygon,bounding rectangle in opencv,minEnclosingCircle,boundingRect,approxPolyDP,arclength,contourArea,canny,Edge Detection
Author: Rajasekhar Guptha
---
### Procedure
+ Read an image 
```python
image = cv2.imread("/assetsimages/shapes.jpg")
```
![input](/assets\images\shapeinput.PNG)

+ Let's see edges using canny edge detection  
    + First convert image to gray scale for better detection and add blur to reduce noise 

```python
grayImage = (cv2.cvtColor(image, cv2.COLOR_BGR2GRAY))
blurredImage = cv2.GaussianBlur(grayImage, (3, 3), 0) 
 # check with different blur types for better output
```
 ![gray-blur](/assets\images\grayb.PNG)  
   + now apply canny 
```python
cannyImage = cv2.Canny(blurredImage, 95,90)
 # threshold1 and threshold2 values depends on images , try with different values
```
![edges](/assets\images\edges.png)

**findContours** method will give all the contours present in image 

provide cannyImage for finding contours
```python
contours, hierarchy = cv2.findContours(image=cannyImage,mode=cv2.RETR_EXTERNAL,method=cv2.CHAIN_APPROX_NONE)
```
[see this](#contours-and-hierarchy) for details about contours and hierarchy
> method = CHAIN_APPROX_NONE or CHAIN_APPROX_SIMPLE

**CHAIN_APPROX_NONE** : this will give all the points on the boundaries
**CHAIN_APPROX_SIMPLE** : It removes all redundant points and compresses the contour, thereby saving memory.

![nonevssimple](/assets\images\nonevssimple.png)

Here with CHAIN_APPROX_SIMPLE it gave only 4 corner points but with CHAIN_APPROX_NONE we got each and every point on the borders

**choose according to your requirement**  

I am willing to draw entire boundary here so, I am using CHAIN_APPROX_NONE

>Tip:- we can draw boundaries by getting corner points also using line function in OpenCV

```python
for contour in contours:
    area = cv2.contourArea(contour)
    # gives area of contour
    perimeter = cv2.arcLength(contour, closed=True)
    # gives perimeter of contour

    borders = cv2.approxPolyDP(curve=contour,epsilon=0.05*perimeter,closed=True)
    # approximate boundaries for given polygon contour
```
> **epsilon :**
    (x*perimeter) try with different values of x for better result
when I used x=0.1, it detected **circle as square**

![0.1](/assets\images\0.1_LI.jpg)
+ For 0.05 I got it perfect 

by using len(boundaries) determine polygon type  
Now the conflict is when, no. of boundaries is 4, it may be a square or rectangle
+ I used aspect ratio to differentiate square and rectangle
![aspectratio](/assets\images\aspectRatio.PNG)
![square aspectratio](/assets\images\squareAspectRatio.png)


```python
    if  len(borders) == 3:
        shape = 'Tri'
    elif len(borders) == 4:
        aspectratio=w/h
        print(aspectratio)
        if round(aspectratio,1)==1:
            shape = "Square"
        else:
            shape="Rectangle"
    elif len(borders) > 4:
        shape = "Circle"
    else:
        shape = "nothing"
```
Printing Polygon type on image using putText method
```python
    cv2.putText(image,shape,(round(x+w//2)-15,round(y+h//2)+10),fontFace=cv2.FONT_HERSHEY_COMPLEX,fontScale=0.3,color=(0,0,0))
```
![final](/assets\images\final.PNG)

### Additional
#### drawContours 
 we can also draw contours we get on images using **drawContours** 
 ```python
 for contour in contours:
    cv2.drawContours(grayImage,contour,-1,color=(0,0,0),thickness=3)
    cv2.imshow("edges drawn",grayImage)
   ```
+ for CHAIN_APPROX_NONE
>![none](/assets\images\edgesnone.PNG)
+ for CHAIN_APPROX_SIMPLE 
>![simple](/assets\images\edgessimple.PNG)

#### boundingRect
min rectangle over the image
```python
borders = cv2.approxPolyDP(curve=contour,epsilon=0.05*perimeter,closed=True)
x, y, w, h = cv2.boundingRect(borders)
cv2.rectangle(image,(x,y),(x+w,h+y),(255,0,0))
```
![boundingrect](/assets\images\boundingrect.PNG)
#### minEnclosingCircle
min circle that fits the shape
```python
(x1,y1),r=cv2.minEnclosingCircle(contour)
# now draw circle (x1,y1) as center and r as radius

```
![minCircle](/assets\images\minEnclosingCircle.PNG)

[see this](https://docs.opencv.org/3.4/dd/d49/tutorial_py_contour_features.html) for more..
### contours and hierarchy

+ **Contours** (boundaries) is a Python list of all the contours in the image. Each individual contour is a Numpy array of (x,y) coordinates of boundary points of the object.
+ **Hierarchy :** Incase of nested Figures,hierarchy will define the relation between contours. It can specify how one contour is connected to each other, like, is it child of some other contour, or is it a parent etc   
[more about contours and hierarchy](https://docs.opencv.org/3.4/d9/d8b/tutorial_py_contours_hierarchy.html)