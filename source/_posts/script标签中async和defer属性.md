---
title: script标签中async和defer属性
date: 2024-7-8 09:51:40
categories:	
  - 记录
tags:
  - javascript
---

`script`标签中的`script`和`defer`属性用于控制`JavaScript`脚本的加载和执行时机：

```javascript
<script src='script.js'></script>
<script src='async.js' async></script>
<script src='defer.js' defer></script>
```

开发过程中经常遇到这三类`script`，那么它们有什么区别？

<!--more-->

### script

------

浏览器解析`HTML`的过程中，如果遇到没有任何属性的`script`标签，此时会暂停解析，去获取该JS脚本，然后执行完该JS代码后，然后继续解析。

```html
<!doctype html>
<html lang="en">
<head>
    <title>Document</title>
   <script src="https://cdn.bootcdn.net/ajax/libs/jquery/3.7.1/jquery.js"></script>
</head>
<body>
<script>
    console.log(jQuery, 'jquery');
    document.addEventListener('DOMContentLoaded',function(){
        console.log('DOMContentLoaded');
    })
</script>
</body>
</html>
```

当`jquery`从远程加载完成后，才会继续执行后续代码，如果脚本加载时间过长，会导致白屏，用户看不到页面内容。

![截屏2024-07-08 11.13.17](https://cdn.jsdelivr.net/gh/hkp4570/ImagePicGo@main/img/%E6%88%AA%E5%B1%8F2024-07-08%2011.13.17.png)

### async

------

浏览器解析过程中如果遇到`<script src='async.js' async>`标签时，此时脚本是异步加载，与`HTML`解析并行执行。脚本加载完成之后立即执行，脚本的执行不会等待其他脚本的加载或`HTML`的解析。脚本的执行顺序无法保证，那个脚本先加载完成，就先执行哪个。

### defer

------

浏览器解析过程中如果遇到`<script src='defer' defer>`标签时，此时脚本是异步加载，与`HTML`解析并行执行。脚本会在`HTML`解析完成后，`DOMContentLoaded`事件执行之前执行。脚本会在它们在`HTML`中出现的顺序执行。

### async 和 defer 对比

------

| 特性     | async                                  | defer                             |
| -------- | -------------------------------------- | --------------------------------- |
| 加载方式 | 异步加载                               | 异步加载                          |
| 执行时机 | 加载完立即执行                         | HTML解析完后执行                  |
| 执行顺序 | 加载完的先后顺序（谁先加载完谁先执行） | 标签在文档中出现的顺序            |
| 使用场景 | 独立的第三方脚本，不依赖其他脚本       | 依赖DOM结构或需要按顺序执行的脚本 |

