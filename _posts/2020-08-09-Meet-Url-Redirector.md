---
layout: single
title:  "Redirects Google Meet and Classroom Url's to desired Mail..( Chrome Extension) "
date:   2020-09-02
excerpt: No need to switch mail for every class .. 
categories: WeekendProjects
tags: "Weekend Project #2"
Author: false
header:
  og_image: assets/images/meet_url_redirector.jpg
  teaser: /assets/images/meet_url_redirector.png
  
---

## Steps to add this extension to chrome

+ Clone/Download this [Repo](https://github.com/RajasekharGuptha/GoogleMeet-Mail-Switcher).

+ visit chrome://extensions/ page.

![Developer Mode](/assets\images\developermodetoggle.png)

+ Switch On Developer Mode (On Top Right)

+ Click **Load Unpacked**

![load unpacked](/assets\images\loadUnpacked.png)

+ Select the folder you downloaded just now 

+ And it will be added to chrome..  
![Added Extension](/assets\images\Capture.PNG)

  ![ext tool bar](/assets\images\ext_bar.PNG)
+ Now Click on **Extension Manager** in Chrome ToolBar

+ and click on this extension to get a popup like this..
![](/assets\images\popup_meet_redirect.PNG) 
+ select Meet and/or classroom as per your need
+ You have to enter Google Account Number.
Chrome Numbers your accounts like this 

  + Default Account - **0**   
  + Next Account - **1** and so on..   
![](/assets\images\gmail_numbering.png)

+ select desired account and enter respective number in popup
+ Click **Save**

That's it..


## Developer Terms..

Achieved this using  **webRequest.onBeforerequest**..

**Explanation :**  
When you enter link (similar to below one ) it will open with default google account.

``
1 https://meet.google.com/xxx-xxxx-xxx
``  

After switching account the link changes to some thing like this 

``
2 https://meet.google.com/xxx-xxxx-xxx?pli=1&authuser=y
``

here **y** is your google account/user number as per accounts in chrome.
Chrome numbers your accounts starting from 0.

So Whenever link corresponds to meet (similar to first link) redirect to changed link(second one) 

```js
chrome.webRequest.onBeforeRequest.addListener(function (tabDetails) {
            var tabUrl = tabDetails.url;
            var req_url_extra = "?pli=1&authuser=" + googleAccountNumber; // user input
                var redirect_url = tabUrl + req_url_extra;
                return { redirectUrl: redirect_url };
             }
            , {
                urls: ["https://meet.google.com/*"],

              // https://meet.google.com/* is
              // regex for google meet links

                types: ["main_frame", "sub_frame", "stylesheet", "script", "image", "object", "xmlhttprequest", "other"]
            },
            ['blocking']
        )
```
This handles most of the cases..
But in cases like this

``
3 https://meet.google.com/xxx-xxxx-xxx?pli=1&authuser=z
``
+ User desired mail is **y** but url is related to **z**
To handle these type of cases we need to do modification to our prev code..
```javascript
chrome.webRequest.onBeforeRequest.addListener(function (tabDetails) {
            var tabUrl = tabDetails.url;
            var req_url_extra = "?pli=1&authuser=" + googleAccountNumber;
            
            //?pli=1&authuser=y required addition to link

            // check if ?pli=1&authuser=y is there in input link
            // if it is there then no need of modifying link
            if (!tabUrl.includes(req_url_extra)) {
              // to handle case 3 https://meet.google.com/xxx-xxxx-xxx?pli=1&authuser=z
              // check if ? is there in link
              // presence of ? indicates link of type 3 
                if (tabUrl.includes('?')) {
                  // removing ?pli=1&authuser=z part
                    tabUrl = tabUrl.split('?')[0];
                }
                // adding ?pli=1&authuser=y 
                var redirect_url = tabUrl + req_url_extra;
                return { redirectUrl: redirect_url };
            }
            else {

                return { redirectUrl: tabUrl };
            }

        }
            , {
                urls: ["https://meet.google.com/*"],
                types: ["main_frame", "sub_frame", "stylesheet", "script", "image", "object", "xmlhttprequest", "other"]
            },
            ['blocking']
        )
```

+ Similar method for classroom links

```
  regex for classroom links:  
         https://classroom.google.com/*

  Link for Default account:
        https://classroom.google.com

  Link for accounts with user number:
        https://classroom.google.com/u/y/h

        y - desired account number
```

To get full source code check this [repo](https://github.com/RajasekharGuptha/GoogleMeet-Mail-Switcher)

+ Incase of issues,raise issue in [Github Repo](https://github.com/RajasekharGuptha/GoogleMeet-Mail-Switcher)

**For suggestions/improvements in Code [mail here](mailto:rajasekharguptha.in@gmail.com)**
