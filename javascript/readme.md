### js核心概念

##### js常用方法集（跨浏览器兼容）

1. 类数组转换为数组
``` js
 function convertToArray(nodes) {
    var array = null;
    try {
          array = Array.prototype.slice.call(nodes, 0); // 针对非IE浏览器
    } catch (e) {
      array = new Array();
      for (var i = 0, len = nodes.length; i < len; i++) {
        array.push(nodes[i]);
      }
    }
  return array;
}

```

2. 检测是否为数组类型
``` js
if（typeof Array.isArray === 'undefined'）{
     Array.isArray = function(arg) { 
        return  Object.prototype.toString.call(arg) === "[object Array]" 
    }
}

```
3. 获取元素的矩形对象
```js

function getElementLeft(element) {
    var actualLeft = element.offsetLeft;
    var current = element.offsetParent;
    
    while (current != null) {
        actualLeft += current.offsetLeft;
        current =  element.offsetParent;
    }
}

function getElementTop(element) {
    var actualTop = element.offsetTop;
    var current = element.offsetParent;
    
    while (current != null) {
        actualTop += element.offsetTop;
        current = element.offsetParent;
    }
}

function getBoundingClientRect(element) {
    var scrollTop = document.documentElement.scrollTop;
    var scrollLeft = document.documentElement.scrollLeft;
    if (element.getBoundingClientRect) {
        if (typeof arguments.callee.offset != 'number') {
            var temp = document.createElement('div');
            temp.style.cssText = 'position:absolute;left:0;top:0';
            document.body.appendChild(temp);
            arguments.callee.offset = -temp.getBoundingClientRect().top - scrollTop;
            document.removeChild(temp);
            temp = null;
        }
        
        var rect = element.getBoundingClientRect();
        var offset = arguments.callee.offset;
        
        return {
            left: rect.left + offset,
            right: rect.right + offset,
            top: rect.top + offset,
            bottom: rect.bottom + offset
        }
    } else {
        var actualLeft = getElementLeft(element);
        var actualRight = getElementTop(element);
        
        return {
            left: actualLeft - scrollLeft,
            right: actualLeft + element.offsetWidth - scrollLeft,
            top: actualTop - scrollTop,
            bottom: actualTop + element.offsetHeight - scrollTop
        }
    }
}
```
