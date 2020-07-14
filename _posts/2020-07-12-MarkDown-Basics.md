---
layout: single
title:  "MarkDown"
date:   2020-07-12 
excerpt: Markdown Documentation
categories: MarkDown
tagline: MarkDown,GFM,complete markdown,Github MarkDown,MarkDown basics,MarkDown Docs,MarkDown glimpse
Author: Rajasekhar Guptha
header:
  teaser: /assets/images/md.png
---

<figure>
  <img src="/assets/images/md.png" alt="Markdown Header image">  
</figure>

# Markdown
Markdown is a lightweight markup language. With the help of markdown we can make up the look of plain text in a rich way in a text editor easily. Widely used for Github READMe files,websites,emails etc.

# Headings

If u know html, there we will have 6 levels of headings varying with size and boldness.  

Here in MarkDown we will use no.of '#' to represent size ,like  
"# heading 1"     similar to h1

```  
    # heading 1  
    
    ## heading 2  
    .
    .
    ###### heading 6
```  

  # heading 1
  ## heading 2  
  .
  . upto 6
  ###### heading 6


>Note:- Always use space between '#' and heading sentence

### Bold text
  #### < strong > in html

``
  For **bold** use two *'s before and after word  
``  

For **bold** use two *'s before and after word

### Italic
  #### < em > in html  
``
  For *italic* use one * before and after word  
``  

For *italic* use one * before and after word

Note:- We can use ' _ ' in place of  ' * ' for bold and italic

### Bold & Italic
  #### < strong >< em > < /em >< strong > or
  #### < em >< strong > < /strong >< /em >

``
    Use three *'s before and after word.  
    This is  ***bold and italic***
`` 

This is  ***bold and italic***

### Paragraphs
  ##### < p > in html

```
We simply don't need any syntax for paragraphs

But to separate lines use a blank line 
```
Note:- Don't indent paragraphs.    

### Line Breaks
  ##### < br > in html
```
    This is first line.
    This is second line
    (Here I am using "Enter" to separate lines but MarkDown don't actually break line there )
```
output:
``
    This is first line. 
    This is second line
``  

Use two or more spaces after a line and then use Enter
```
First Line  
Second Line
```
Output:  
First Line  
Second Line  

### Blockquotes

add > infront of paragraph

```  
> this line is blockquoted  
```
>this line is blockquoted

### Blockquotes (Multiple Paragrahs)

```
>This is first paragraph in blockquote

>This is second one
```
output:  
>This is first paragraph in blockquote

>This is second one

Whenever there are two or more paragraphs seoarated by blank line use > fot that blank line too
```
>This is first paragraph in blockquote
>
>This is second one
```
output:  
>This is first paragraph in blockquote
>
>This is second one

### Sub Blocks
```
>This is first paragraph in blockquote
>
>>This is second one and sub block
```
output:  
>This is first paragraph in blockquote
>
>>This is second one and sub block  

### Lists
  #### < ul > and < ol > in html

For ordered lists in markdown
```
use numbers before items 
order of numbers doesn't matter but we should start with 1.

1. item1
2. item2
4. item3
    1. sub item 1
    2. sub item 2
```  

output:-  
1. item1
2. item2
4. item3
    1. sub item 1
    2. sub item 2  

For unordered lists in markdown  

```
use '-' or '+' or '*'  before items 

+ item1
* item2
- item3
    - sub item 1
```
output:-  
+ item1
* item2
- item3
    - sub item 1

 Note:- Use Indentation for sub lists

### Code
  #### < code > in html
``  
`code`
`` 

`code`

### Code Blocks

Indent every line of block by a tab space 

    code 1
    code 2


### Horizontal rules
  #### < hr > in html

Use 3 or more *'s or _'s or -'s

```
    ---
    *****
    ______
```
Ouput:

---
***
___

 Note:-

```
  Line1
--- (for horizontal rule)
Line2
```
Output:  

  Line1
---
Line2

This is unexpected right!!

maintain space between them   
```
  Line1
--- (for horizontal rule)
Line2
```
Output:  

  Line1

---
Line2


### Links
```
[Title](link)
[My Website](https://rajasekharguptha.github.io)

For mails add "mailto:" to mail
[mail](mailto:rajasekharguptha.in@gmail.com)
```
Output:  

[My Website](https://rajasekharguptha.github.io)  
[mail](mailto:rajasekharguptha.in@gmail.com)


Without Title:
```
<link/mail>
<https://rajasekharguptha.github.io>
<rajasekharguptha.in@gmail.com>
```
output:  
<https://rajasekharguptha.github.io>
<rajasekharguptha.in@gmail.com>

### Images
```
![Image Name](Image link)
![Sample Image](/assets/sampleimage.jpg)
```
![Sample Image](/assets/sampleimage.jpg)

### Escaping Chars

Use backslash \ in front of character
like \*,\- etc.


