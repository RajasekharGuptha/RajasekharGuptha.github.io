---
layout: single
title: "Beyond console.log()"
date: 2020-10-02
excerpt: Lot more methods beyond console.log() like console.table(),console.count() etc..
categories: Javascript
Author: Rajasekhar Guptha
header:
  teaser: /assets/console_log.png
  og_image: /assets/console_log.png
toc: false
---

We all have been using console.log(), but many more options are available out there.Let us see them now

The most useful type beyond **log** is **console.table()**

- console.table()

  - Takes in JSON or an array and prints in table format
  - Very handy while visualising json objects and arrays
  - Syntax:

                  console.table({
                         id: "1",
                         key: "value",
                             count: 2,
                     });

    ![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/xdurz2y6jgi98l2u4z3g.PNG)

                   console.table([
                       {
                           id: "1",
                           key: "value",
                           count: 2,
                           },
                        {
                            id: "2",
                            key: "value2",
                                count: 22,
                          },
                          {
                               id: "3",
                               key: "value3",
                                   count: 5,
                                  },
                        ]);

    ![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/14iyr8ynuy0bdfbjvmnr.PNG)

The next useful method is **error**

- console.error() - useful to differentiate errors from output logs while debugging

  ![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/04y2gf22co4486vyt4jc.PNG)

  - red color

Next one, useful while calculating **runnning times** is **time** method

- Time(time,timeLog,timeEnd)

  - To understand this, let us assume scenario of a **stopwatch**
    ![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/vsepbkvmpf05e322t25s.png)

    - console.**time**()

      - equivalent to stopwatch **start**

    - console.**timeLog**()

      - like stopwatch **lap/split**

    - console.**timeEnd**()
      - stopwatch **end**

  - It works on basis of **label**. Label should be the same to get expected output

        console.time("ForLoop");  // "ForLoop" is label here
        for (let i = 0; i < 5; i++) {
        console.timeLog('ForLoop');
          }

    console.timeEnd("ForLoop");

  ![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/3vasc1sm4ihofnhczief.PNG)

Next one is **warning**

- console.warn();
  ![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/8dqzqpd7adgou203vr5k.PNG)

  - yellow color
  - For warnings

- console.**assert**()

  - console.assert(assert_statement,message)
  - evaluate assertion statement and if it is **false** displays the message

        	    if(3!=2){
        	console.error({ msg1: "msg1", msg2: "msg2" });
        	}
        	-----------same as---------
        	console.assert(3 === 2, { msg1: "msg1", msg2: "msg2" });

    ![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/7th14kqk1cymnj2k8qxp.PNG)

  - console.assert(assert_statement,message,args)`

    ```
        console.assert(false, "%d nd type for %s ",2,"console.assert() method");
    ```

    ![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/cr8laxb6jbmxwrdveico.PNG)

Useful method for **counting**

- console.**count**()  
  works on basis of **label** - console.count(label)

```
for (let i = 0; i < 3; i++) {
  console.count("label");
  console.count();
  console.count(i);
  }
  // output for
  console.count() console.count("label") console.count(i)
  default: 1         label: 1        0: 1
  default: 2         label: 2        1: 1
  default: 3         label: 3        2: 1
```

- console.count()

  - if no label is mentioned it will consider **default** as label
  - The problem with **default** is it will continue the count like this
    ![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/a2icg0tlhjtxgtq5g2ja.PNG)

  - console.countReset(label)

  * resets count of specified label to **0**

I mentioned only few methods which I think are more helpful.To check all the available methods refer [here](https://developer.mozilla.org/en-US/docs/Web/API/console)

[Twitter](https://twitter.com/rajasekhar_24)
