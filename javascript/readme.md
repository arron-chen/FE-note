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
        array.push(nodes{i]);
      }
    }
  return array;
}

```
