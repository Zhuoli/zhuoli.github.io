---
layout: post
title: '再学Markdown'
date: 2019-4-05
author: zhuoli
cover: 'http://on2171g4d.bkt.clouddn.com/jekyll-banner.png'
tags: markdown  #这里写标签
---

> 用Markdown来写日记.

部分内容来自于: [Markdown终极教程](https://blog.ghost.org/markdown/) 

推荐编辑器: [Visual Studio Code自带 Markdown 预览功能](https://code.visualstudio.com/Docs/languages/markdown)

![all text](https://github.com/Zhuoli/zhuoli.github.io/blob/master/assets/img/md-dynamic-preview.gif?raw=true)


---
## 文件标题 Headers:
---
一个井号\#
# H1
两个井号\##
## H2
三个井号\###
### H3

Alternatively, for H1 and H2, an underline-ish style:

多个等于号=====

Alt-H1
======

破折号------

Alt-H2
------
---
## 着重符合

1. 用单个星号或者下划线来变成斜体, \*asterisks\* or \_underscores\_      
    * *asterisks* or _underscores_.

2. 用双星号与双下划线来加粗, with \**asterisks\** or \__underscores\__
    * **asterisks** or __underscores__

3. 将1与2结合起来用获得加粗斜体 with \**asterisks and _underscores_\**
    * **asterisks and _underscores_**

4. 用波浪线来划掉内容. \~~Scratch this.\~~
    * ~~Scratch this.~~

---

## 列表 List
1. First oder list
2. ANother item
...* Unordered sub-list
1. Actual number doesnt matter just that its a number
..1. Ordered sub-list
4. And another item.

* Unordered list can use asterisks
- or minuses
+ or pluses

---

## 超链接 Links

1. \[inline stype](https://www.google.com)
    * [I'm an inline-style link](https://www.google.com)

2. \[inline-style link with title](https://www.google.com "Google's Homepage")
    * [I'm an inline-style link with title](https://www.google.com "Google's Homepage")
3. \[I'm a reference-style link][Arbitrary case-insensitive reference text]
    * [I'm a reference-style link][Arbitrary case-insensitive reference text]

4. \[I'm a relative reference to a repository file](../blob/master/LICENSE)
    * [I'm a relative reference to a repository file](../blob/master/LICENSE)

5. \[You can use numbers for reference-style link definitions][1]
    * [You can use numbers for reference-style link definitions][1]

6. Or leave it empty and use the \[link text itself].
    * Or leave it empty and use the [link text itself].

URLs and URLs in angle brackets will automatically get turned into links. 
http://www.example.com or <http://www.example.com> and sometimes 
example.com (but not on Github, for example).

Some text to show that the reference links can follow later.

\[arbitrary case-insensitive reference text]: https://www.mozilla.org
[arbitrary case-insensitive reference text]: https://www.mozilla.org

\[1]: http://slashdot.org
[1]: http://slashdot.org
\[link text itself]: http://www.reddit.com
[link text itself]: http://www.reddit.com


---

## 引用Quotes

\> 生存还是毁灭，这是个问题
> 生存还是毁灭，这是个问题

---

## 代码片段 Code Snippets

Some text with an inline `code` snippet

 .my-link {
        text-decoration: underline;
    }

---

## 图片 Images

Here's our logo (滑动鼠标见内容):

1. Inline-style:

\!\[alt text]\(https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

2. Reference-style: 
\![alt text]\[logo]
![alt text][logo]

[logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 2"
\[logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 2"

## 代码与高亮 Code and Syntax Highlighting
**用三个`加语言名称实现对应高亮**

\```javascript

var s = "JavaScript syntax highlighting";
alert(s);

\```

```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```
 \```python

s = "Python syntax highlighting"
print s

\```

```python
s = "Python syntax highlighting"
print s
```
\```csharp

//Hello World
using System;
class Solution
{
  static void Main(String[] args)
  {
    Console.WriteLine("Hello World!");
  }
}

\```

```csharp
//Hello World
using System;
class Solution
{
  static void Main(String[] args)
  {
    Console.WriteLine("Hello World!");
  }
}
```
\```java
public class HelloWorld {

    public static void main(String[] args) {
        // Prints "Hello, World" to the terminal window.
        System.out.println("Hello, World");
    }

}
\```

```java
public class HelloWorld {

    public static void main(String[] args) {
        // Prints "Hello, World" to the terminal window.
        System.out.println("Hello, World");
    }

}
```

```
No language indicated, so no syntax highlighting. 
But let's throw in a <b>tag</b>.
```
var s = "JavaScript syntax highlighting";
alert(s);
s = "Python syntax highlighting"
    
    print s

No language indicated, so no syntax highlighting in Markdown Here (varies on Github). 
But let's throw in a <b>tag</b>.