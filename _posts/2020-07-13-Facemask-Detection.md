---
categories: OpenCV
title: Facemask Detection using OpenCV python
author: Rajasekhar Guptha
tagline: Custom Haar Cascade files,Custom Cascades,Haar Cascades
excerpt: Face Mask Detection Haar Cascade
image: /assets/images/2.jpg
header:
  teaser: /assets/images/1.jpg
gallery:
    - image_path: /assets/images/2.jpg
    - image_path: /assets/images/3.jpg 
---

## Face Mask Detection Haar Cascade  
{% include gallery caption="This is how it detects" %}

You can get cascade file [here](https://github.com/RajasekharGuptha/facemask-detection-haar-cascade) 

To create your own haar cascade files see [this tutorial]({{site.baseurl}}/opencv/2020/07/13/Custom-Cascade-Creation.html)

### How to use this cascade file :

**Reduce size of image before applying cascade for better results** 

For Testing we used 300x300 size for all images 

Try with different sizes for accurate results

```python
import cv2 as cv

fmcascade=cv.CascadeClassifier("facemaskcascade.xml")
image = cv.imread("test_image.jpg")
image = cv.resize(image, (300, 300))
fm = fmcascade.detectMultiScale(image, 1.12,2,None,(120,120),(300,300)) # try with different values for better results

for (x, y, w, h) in fm:
    cv.rectangle(image, (x, y), (x + w, y + h), (0, 0, 0))

cv.imshow("Final Image",image)

```

If it did not work for any image , convert image to gray mode and then try again  
```python
gray_image = cv.cvtColor(image, cv.COLOR_BGR2GRAY)

```
**Not 100% accurate**  

For creating custom cascade files see this [post]({{site.baseurl}}/opencv/2020/07/13/Custom-Cascade-Creation.html)


