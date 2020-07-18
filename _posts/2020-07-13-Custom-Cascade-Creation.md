---
categories: OpenCV
author: Rajasekhar Guptha
title: Custom Haar Cascade File in just 4 steps
tagline: Custom Haar Cascade files,Custom Cascades,Haar Cascades
excerpt: Face Mask Detection Haar Cascade
header:
  teaser: /assets/images/3.jpg
---

## Prerequisites:
+ [GUI Trainer Tool](http://amin-ahmadi.com/cascade-trainer-gui/)
+ Positive Images set ( Images you want to detect )
+ Negative Images set ( Non positive images )  
    
__ProTip :__ For negative images use images relevant to positive.  
For example if you want to recognize human faces dont include forest images as negative ones  

### step1
Create 2 folders **p** (place positive image set here) and **n** (place positive image set here)

<figure>
<img src="/assets/images/np.PNG" />
</figure>

### step2
Open GUI Tool 
<figure>
<img src="/assets/images/step1.png" />
</figure>

### step3

choose no. of training sessions
<figure>
<img src="/assets/images/step2.png" />
</figure>

### step4
<figure>
<img src="/assets/images/step3.png" />
</figure>

That's it after traing completion of training process you can see these..
<figure>
<img src="/assets/images/files.PNG" />
</figure>

Inside **classifier** folder you can get cascade.xml
<figure>
<img src="/assets/images/cascadefile.png" />
</figure>


To know how to use this cascade file and detect objects see this [post]({{site.baseurl}}/opencv/2020/07/13/Facemask-Detection.html) 



