---
layout: single
title:  "Geometric Transformation using OpenCV"
date:   2020-07-19
excerpt: Transformations like rotation,perspective transformation,affine transformation,translation etc. in OpenCV
categories: OpenCV
tagline: rotation in opencv python,perspective transformation in opencv python,perspective,affine transformation in opencv python,perspective,translation in opencv python,perspective etc. in  OpenCV python
Author: Rajasekhar Guptha
---

Many of the transforamtions use Matrices as input (Computer Graphics students may already know this). Here in OpenCV we have different functions available to create those matrices.

### Perspective Transformation

We need 4 points on the input image and corresponding 4 points on the output image
```
let these be points on input [(a,b),(a1,b1),(a2,b2),(a3,b3)] and these will be ouput points  
[(x,y),(x1,y1),(x2,y2),(x3,y3)]

the point (a,b) will be placed in position (x,y) in output image

```
**getPerspectiveTransform** will create a matrix for us using those points 
```python
Matrix = cv2.getPerspectiveTransform(pts1,pts2)
```
Now apply this Matrix to image using **warpPerspective**

**Document scanners use this perspective**
```python
output = cv2.warpPerspective(image,M,(500,500))
```

### Affine Transformation
All parallel lines in the original image will still be parallel in the output image.

> To find the transformation matrix, we need three points from input image and their corresponding locations in output image

![affine](/assets\images\affine.PNG)

**getAffineTransform** will create a matrix for us.
```python
Matrix = cv2.getAffineTransform(pts1,pts2)
output = cv2.warpAffine(img,Matrix,(width,height))
```
cv2.warpAffine(input_image,Transformation_Matrix,outputImageSize))

**Note:** output image size will be in the form of (width,height) 

### Rotation
**getRotationMatrix2D** will create Rotation Matrix
```python
rotationMatrix=cv2.getRotationMatrix2D(center=(height/2,width/2),angle=45,scale=1)
o1=cv2.warpAffine(image,rotationMatrix,(width,height))
```
![rotation](/assets\images\rotation.PNG)

### Scaling

We can scale images using resize function by adding interpolation

cv2.INTER_AREA for shrinking and cv2.INTER_CUBIC (slow) & cv2.INTER_LINEAR for zooming

```python
res = cv2.resize(img,(width,height), fx=None,fy=None,interpolation = cv2.INTER_CUBIC)
```

or you can mention scaling factor manually

+ fx- horizontal scaling factor
+ fy- vertical scaling factor