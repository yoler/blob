---
title: 文件下载
date: 2017-05-22 09:52:34
tags: 前端
---
```html
<button onclick="download('11.txt', 'fsdfdsfsdfsdfsdfsdfsf')">下载</button>
```
```javascript
function download(filename, content) {
	var aLink = document.createElement('a')
	var blob = new Blob([content])
	var event = new MouseEvent('click', {
	  'view': window,
	  'bubbles': true, //是否冒泡
	  'cancelable': true //事件是否可以取消
	});
	aLink.download = filename
	aLink.href = URL.createObjectURL(blob)
	aLink.dispatchEvent(event)
}
```
