---
layout: post
title: '字符串的编码与解码'
date: 2021-4-10
author: zhuoli
cover: 'http://on2171g4d.bkt.clouddn.com/jekyll-banner.png'
tags: tech 
---

Leetcode [271题](https://leetcode.com/problems/encode-and-decode-strings/)

## 如何讲一组字符串编码串联成一个字符串， 然后再解码成原来的一组字符串呢？
两个很实用的解法:
1) 思路一： 把字符与分隔符区别开来。 Base64, 把原字符串转化成base64， 这样就不会与分隔符冲突了
2) 思路二： 告诉解码器每一个字符串的起始位置与长度。 Chunked Transfer Encoding， 借助http1.1 chunked transfer encoding的设计思想， 我们在每个字符串之前加上字符串长度描述符；这样Decode过程就能按长度描述符准确的切割后面的字符串了.
```
例子:  
input:  'good', 'morning'
Encode: [0004good0007morning]
```

```python
# Base64
class Codec:
    def encode(self, strs: [str]) -> str:
        """Encodes a list of strings to a single string.
        """
        result=""
        for string in strs:
            bs = string.encode('ascii')
            b64 = base64.b64encode(bs)
            result = result + ',' + b64.decode('ascii')
        return result

    def decode(self, s: str) -> [str]:
        """Decodes a single string to a list of strings.
        """
        s = s[1:]
        strs = s.split(',')
        result = []
        for b64 in strs:
            decode_obj = base64.b64decode(b64)
            result.append(decode_obj.decode('ascii'))
        return result
```