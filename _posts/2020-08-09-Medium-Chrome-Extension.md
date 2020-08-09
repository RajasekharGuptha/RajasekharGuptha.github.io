---
layout: single
title:  "( Chrome Extension) Read Unlimited Premium Posts In Medium by Rajasekhar Guptha"
date:   2020-08-09
excerpt: Headache of switching to Incognito is No more.. 
categories: WeekendProjects
tags: "Weekend Project #1"
Author: Rajasekhar Guptha
header:
  teaser: /assets\images\mediumCrackTeaser.png
image: 
  path: https://github.com/RajasekharGuptha/RajasekharGuptha.github.io/assets/images/mediumCrackTeaser.png
  height: 100
  width: 100
---
<figure>
  <img src="/assets\images\mediumCrackTeaser.png" alt="Medium Crack image">
  
</figure>

### Steps to add this extension to chrome

+ Clone this [Repo](https://github.com/RajasekharGuptha/Medium-Freeifier).

+ visit [this](chrome://extensions/) page.

![Developer Mode](/assets\images\developermodetoggle.png)

+ Switch On Developer Mode (On Top Right)

+ Click **Load Unpacked**

![load unpacked](/assets\images\loadUnpacked.png)

+ Select downloaded folder  

And that's it..

### Developers can go through remaining post..
**Note:-  Remaining post will be more of technical terms**

We can achieve this in 2 ways..

+ Spoofing the request as it is referred from Twitter
+ Change user_id in website cookies 

#### Twitter Referer Method

![Tweet](/assets\images\tweet.png)

So, when a premium post is referred from twitter it is free.

But we cannot always head to twitter to read posts.

So, we are spoofing premium post requests as they are referred from twitter.

main logic is embedded here..
```js
// removing already existing referer from request
headers.filter(({ name }) => name.toLowerCase() != "referer");

// adding twitter as referer
headers.push({ 'referer', twitter_link});

twitter_link='https://t.co/'+random string
// link may be something like this
// 'https://t.co/wTerQ3LRSYu1'
```

#### Changing user_id

We all know that we can read premium posts for free in **incognito mode**

Normally every user will be assigned with 12 digit user_id (uid) which will be stored in cookies.

+ For every user id we can read 3 articles 

But why are we able to read them for free in  incognito..?
 Bcoz, in incognito mode our user_id will be changed to a random number.

 After observing uid in incognito I found this..(lo_3Rf4TgYofTeh,lo_r0fgLdmOfT6q..),

 + In incognito mode user_id will be **lo_**+random 12 digit alpha numeric string

main logic is here..
 ```js
// function to generate random alphanumeric string for given length
 function getRandomString(length) {

  allowedChars = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
  var randomStr = ''
  for (var i = 0; i < length; i++) {

    randomStr += allowedChars[Math.floor(Math.random() * allowedChars.length)]

  }

  return randomStr

}

// we require string of length 12

// url - post url to get cookies associated
// name - userid will be stored in cookie with name of uid 
// value - generated random string of length 12
var details = { 'url': url, 'value':'lo_'+getRandomString(12), 'name': 'uid' }
  chrome.cookies.set(details, function (cookie) {
  })


```

To get full code check this [repo](https://github.com/RajasekharGuptha/Medium-Freeifier)
