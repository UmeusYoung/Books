# JS 常用函数

## 常用工具函数

### Array

#### js删除数组指定item

```javascript
Array.prototype.removeByValue = function (val) {
  for (var i = 0; i < this.length; i++) {
    if (this[i] == val) {
      this.splice(i, 1);
      break;
    }
  }
}
```

#### js删除指定index的item

```javascript
Array.prototype.remove = function (dx) {
  if (isNaN(dx) || dx > this.length) {
    return false;
  }
  for (var i = 0, n = 0; i < this.length; i++) {
    if (this[i] != this[dx]) {
      this[n++] = this[i]
    }
  }
  this.length -= 1
}
```

#### 递归遍历数组成员并输出

```javascript
//函数 printArray 使用了递归方式，逐一输出数组中的每个成员，中间以空格隔开。
//@arr ：应是数组类型
function printArray(arr) {
  for (var i in arr) {
    if (arr[i] instanceof Array) {
      printArray(arr[i]);
    } else {
      document.write(arr[i] + '');
    }
  }
}
```

#### JS插入排序

```javascript
//此方法排序从小到大
//@arr ：应是数组类型

function insertionSort(arr) {
  //从第二个元素开始
  for (var i = i; i < arr.length; i++) {
    //取出待比较的元素
    var k = arr[i];
    //像前找，找到比当前元素大的位置
    var j;
    for (j = i - 1; j >= 0 && k < arr[j]; j--) {
      //向后移动一位
      arr[j + 1] = arr[j];
    }
    //插入元素
    arr[j + 1] = k;
  }
}
```

#### BOM

#### 判断浏览器

```javascript
function getOs() {
  if (navigator.userAgent.indexOf("MSIE 8.0") > 0) {
    return "MSIE8";
  } else if (navigator.userAgent.indexOf("MSIE 6.0") > 0) {
    return "MSIE6";
  } else if (navigator.userAgent.indexOf("MSIE 7.0") > 0) {
    return "MSIE7";
  } else if (isFirefox = navigator.userAgent.indexOf("Firefox") > 0) {
    return "Firefox";
  }
  if (navigator.userAgent.indexOf("Chrome") > 0) {
    return "Chrome";
  } else {
    return "Other";
  }
}
```

#### 手机类型判断

```javascript
var BrowserInfo = {
  userAgent: navigator.userAgent.toLowerCase(),
  isAndroid: Boolean(navigator.userAgent.match(/android/ig)),
  isIphone: Boolean(navigator.userAgent.match(/iphone|ipod/ig)),
  isIpad: Boolean(navigator.userAgent.match(/ipad/ig)),
  isWeixin: Boolean(navigator.userAgent.match(/MicroMessenger/ig)),
}
```

#### 获取当前js的版本

```javascript
function getjsversion() {
  var n = navigator;
  var u = n.userAgent;
  var apn = n.appName;
  var v = n.appVersion;
  var ie = v.indexOf('MSIE ');
  if (ie > 0) {
    apv = parseInt(i = v.substring(ie + 5));
    if (apv > 3) {
      apv = parseFloat(i);
    }
  } else {
    apv = parseFloat(v);
  }
  var isie = (apn == 'Microsoft Internet Explorer');
  var ismac = (u.indexOf('Mac') >= 0);
  var javascriptVersion = "1.0";
  if (String && String.prototype) {
    javascriptVersion = '1.1';
    if (javascriptVersion.match) {
      javascriptVersion = '1.2';
      var tm = new Date;
      if (tm.setUTCDate) {
        javascriptVersion = '1.3';
        if (isie && ismac && apv >= 5) javascriptVersion = '1.4';
        var pn = 0;
        if (pn.toPrecision) {
          javascriptVersion = '1.5';
          a = new Array;
          if (a.forEach) {
            javascriptVersion = '1.6';
            i = 0;
            o = new Object;
            tcf = new Function('o', 'var e,i=0;try{i=new Iterator(o)}catch(e){}return i');
            i = tcf(o);
            if (i && i.next) {
              javascriptVersion = '1.7';
            }
          }
        }
      }
    }
  }
  return javascriptVersion;
}
```

#### 判断浏览器是否支持CSS3属性

```javascript
/**
 * 判断是否支持css3
 * 
 * @param {string} style CSS属性
 * @returns 
 */
function supportCss3(style) {
    var prefix = ['webkit', 'Moz', 'ms', 'o'],
        i,
        humpString = [],
        htmlStyle = document.documentElement.style,
        _toHumb = function (string) {
            return string.replace(/-(\w)/g, function ($0, $1) {
                return $1.toUpperCase();
            });
        };

    for (i in prefix)
        humpString.push(_toHumb(prefix[i] + '-' + style));

    humpString.push(_toHumb(style));

    for (i in humpString)
        if (humpString[i] in htmlStyle) return true;

    return false;
}
```

#### 阻止事件冒泡

```javascript
//@e ：事件对象
function stopPP(e) {
  var evt = e || window.event;
  //IE用cancelBubble=true来阻止而FF下需要用stopPropagation方法
  evt.stopPropagation ? evt.stopPropagation() : (evt.cancelBubble = true);
}
```

#### 加入收藏

```javascript
/**
 * 加入收藏
 * 
 * @param {String} sURL 
 * @param {any} sTitle 
 */
function AddFavorite(sURL, sTitle) {
  sURL = encodeURI(sURL);
  try {
    window.external.addFavorite(sURL, sTitle);
  } catch (e) {
    try {
      window.sidebar.addPanel(sTitle, sURL, "");
    } catch (e) {
      alert("加入收藏失败");
    }
  }
}
```

#### 实现设为首页

```javascript
/**
 * 实现设为首页
 * 
 * @param {String} url 
 */
function SetHome(url) {
  if (document.all) {
    document.body.style.behavior = 'url(#default#homepage)';
    document.body.setHomePage(url);
  } else {
    alert("设为首页失败");
  }
}
```

### String

#### JS 替换非法字符主要用在密码验证上出现的特殊字符

```javascript
function URLencode(sStr) {
  return escape(sStr).replace(/\+/g, '%2B').replace(/\"/g, '%22').replace(/\'/g, '%27').replace(/\//g, '%2F');
};
```

#### Js 去掉空格方法

```javascript
String.prototype.Trim = function () {
  return this.replace(/(^\s*)|(\s*$)/g, "");
}
String.prototype.LTrim = function () {
  return this.replace(/(^\s*)/g, "");
}
String.prototype.RTrim = function () {
  return this.replace(/(\s*$)/g, "");
}
```

#### 字符串截取方法

```javascript
function getCharactersLen(charStr, cutCount) {
  if (charStr == null || charStr == '') return '';
  var totalCount = 0;
  var newStr = '';
  for (var i = 0; i < charStr.length; i++) {
    var c = charStr.charCodeAt(i);
    if (c < 255 && c > 0) {
      totalCount++;
    } else {
      totalCount += 2;
    }
    if (totalCount >= cutCount) {
      newStr += charStr.charAt(i);
      break;
    } else {
      newStr += charStr.charAt(i);
    }
  }
  return newStr;
}
```

#### 求一个字符串长度

```javascript
//@  str：传入一个字符串返回该字符串的长度
//PS：假设一个中文占两个字节，一个英文占用一个字节
function getBytes(str) {
  var len = str.length,
    //假如全英文字符串则代表字节长度与字符串长度相同
    bytes = len,
    i = 0;
  //循环遍历字符串获取相对应的Unicode 编码，
  for (i = 0; i < len; i++) {
    if (str[i].charCodeAt() > 255) {
      bytes++;
    }
  }
  return bytes;
}
```

#### js实现解析URL参数， 返回一个对象

```javascript
/**
 * js实现解析URL参数， 返回一个对象
 * 
 * @param {String} url 传入一个地址串，例如"http://www.baidu.com/index.php?key=0&key=1&key=2”
 * @returns 
 */
function parseQuerystring(url) {
  var params = {}, //声明一个数组来存放返回的对象
    arr = url.split('?'); //将url地址与参数分割开来
  if (arr.length <= 1) { //如果没有参数则代表arr.length长度<=1
    return params;
  }
  arr = arr[1].split('&'); //解析后面的参数并返回数组
  //循环遍历arr数组
  for (var i = 0, l = arr.length; i < l; i++) {
    var a = arr[i].split('=');
    params[a[0]] = a[1]; //将分割后的参数以键值对形式存入params
  }
  return params;
}

function GetQueryStringRegExp(name, url) {
  var reg = new RegExp("(^|\\?|&)" + name + "=([^&]*)(\\s|&|$)", "i");
  if (reg.test(url)) return decodeURIComponent(RegExp.$2.replace(/\+/g, " "));
  return "";
}
```

### Date

#### JS判断两个日期大小 适合 2012 - 09 - 09 与2012 - 9 - 9 两种格式的对比

```javascript
//得到日期值并转化成日期格式，replace(/\-/g, "\/")是根据验证表达式把日期转化成长日期格式，这样再进行判断就好判断了
function ValidateDate() {
  var beginDate = $("#t_datestart").val();
  var endDate = $("#t_dateend").val();
  if (beginDate.length > 0 && endDate.length > 0) {
    var sDate = new Date(beginDate.replace(/\-/g, "\/"));
    var eDate = new Date(endDate.replace(/\-/g, "\/"));
    if (sDate > eDate) {
      alert('开始日期要小于结束日期');
      return false;
    }
  }
}
```

#### 获取当前时间

```javascript
function GetCurrentDate() {
  var d = new Date();
  var y = d.getYear() + 1900;
  month = add_zero(d.getMonth() + 1),
    days = add_zero(d.getDate()),
    hours = add_zero(d.getHours());
  minutes = add_zero(d.getMinutes()),
    seconds = add_zero(d.getSeconds());
  var str = y + '-' + month + '-' + days + ' ' + hours + ':' + minutes + ':' + seconds;

  function add_zero(temp) {
    if (temp < 10){
      return "0" + temp;
    }
    return temp;
  }
  return str;
};
```

#### 获取前num天的日期

```javascript
/**
 * 公有方法：获取前num天的日期
 * 
 * @param {Number} num 自动向上取整 
 * @param {boolean} order true是日期从大到小，false是从小到大 
 * @returns MM-dd
 */
function getTodayDate(num, order = false) {
  debugger
  num = Math.ceil(num)
  let arr_Date = []
  for (var i = 0; i < num; i++) {
    let date = new Date(new Date().getTime() - (i * 24 * 60 * 60 * 1000))
    let currMonth = new Date(date).getMonth() + 1
    let currDay = new Date(date).getDate()
    let result = `${currMonth.toString().length < 2 ? `0${currMonth}` : currMonth}-${currDay.toString().length < 2 ? `0${currDay}` : currDay}`;
    if (order) {
      arr_Date.push(result);
    } else {
      arr_Date.unshift(result);
    }
  }
  // console.log(arr_Date);
  return arr_Date;
}
console.log(getTodayDate(7));
```

### DOM

#### 增加/移除事件

```javascript
var EventUtil = {
    addHandler:function(element,type,handler){
        if(element.addEventListener){//检测是否存在DOM2
            element.addEventListener(type,handler,false)
        }else if(element.attachEvent){//存在ie
            element.attachEvent('on'+type,handler)
        }else{//DOM0
            element['on'+type]=handelr;
        }
    },
    removeHandler:function(element,type,handler){
        if(element.removeEventListener){
            element.removeEventListener(type,handler,false);
        }else if(element.detachEvent){
            element.detachEvent('on'+type,handler);
        }else{
            element['on'+type]=null;
        }
    }
}

//使用
var btn = document.getElementById('myBtn');
var handler = function(){
    console.log('hi')
}
EventUtil.addHandler(btn,'click',handler);
EventUtil.removeHandler(btn,'click',handler);
```

#### js实时计算rem,宽度大于1920px时1rem=100px

```javascript
(function (doc, win) {
  var docEl = doc.documentElement,
    resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',
    recalc = function () {
      var clientWidth = docEl.clientWidth;
      if (!clientWidth) return;
      if (clientWidth >= 1920) {
        docEl.style.fontSize = '100px';
      } else {
        docEl.style.fontSize = 100 * (clientWidth / 1920) + 'px';
      }
    };

  if (!doc.addEventListener) return;
  win.addEventListener(resizeEvt, recalc, false);
  doc.addEventListener('DOMContentLoaded', recalc, false);
})(document, window);
```

#### 绑定按钮回车触发单机事件

```javascript
$("id").onkeypress = function (event) {
  event = (event) ? event : ((window.event) ? window.event : "")
  keyCode = event.keyCode ? event.keyCode : (event.which ? event.which : event.charCode);
  if (keyCode == 13) {
    $("SubmitLogin").onclick();
  }
}
```

#### 按Ctrl + Entert 直接提交表单

```javascript
document.body.onkeydown = function (evt) {
  evt = evt ? evt : (window.event ? window.event : null);
  if (13 == evt.keyCode && evt.ctrlKey) {
    evt.returnValue = false;
    evt.cancel = true;
    PostData();
  }
};
```

#### 全选 / 全不选

```javascript
function selectAll(objSelect) {
  if (objSelect.checked == true) {
    $("input[name='chkId']").attr("checked", true);
    $("input[name='chkAll']").attr("checked", true);
  } else if (objSelect.checked == false) {
    $("input[name='chkId']").attr("checked", false);
    $("input[name='chkAll']").attr("checked", false);
  }
}
```

#### 原生JS获取鼠标XY轴的值

```javascript
/**
 * 原生JS获取鼠标XY轴的值
 * 
 * @param {Object} evt 
 * @returns 
 */
function mousePosition(evt) {
  evt = evt || window.event;
  //Mozilla
  if (evt.pageX || evt.pageY) {
    return {
      x: evt.pageX,
      y: evt.pageY
    }
  }
  //IE
  return {
    x: evt.clientX + document.body.scrollLeft - document.body.clientLeft,
    y: evt.clientY + document.body.scrollTop - document.body.clientTop
  }
}

//获取X轴坐标
function getX(evt) {
  evt = evt || window.event;
  return mousePosition(evt).x;
}

//获取Y轴坐标
function getY(evt) {
  evt = evt || window.event;
  return mousePosition(evt).y;
}

//外部函数调用1
document.getElementById("x").onclick = function (evt) {
  alert(getX(evt))
}

//外部函数调用2
function showXY(evt) {
  evt = evt || window.event;
  document.getElementById("n").innerHTML = "" + getX(evt);
}
window.onload = function () {
  document.body.onmousemove = showXY;
}
```

1.  在IE中，event对象是全局的，它被存储在window.event中，对于Firefox，及其他的浏览器来说，这个事件将被传递到任何指向这个页面动作的函数中。可以通过传递参数获取。
2.  document.body.scrollTop是网页被卷去的高，具有 DTD 时用 document.documentElement.scrollTop 代替 document.body.scrollTop ，否则取不到值。
3. Firefox和其他的浏览器使用event.pageX和event.pageY来表示鼠标相对于document文档的位置。如果你有一个500_500的窗口，并且鼠标位于窗口中间，那么pageX和pageY的值将都是250。如果你将窗口向下滚动500象素，pageY的值为750。 如此相反的是，微软的IE使用event.clientX和event.clientY来表示鼠标相对于window窗口的位置，而不是当前document文档。在相同的例子中，如果将鼠标放置于500_500窗口的中间，clientX和clientY值将均为250。如果向下滚动页面，clientY将仍为250，因为它是相对于window窗口来测量，而不是当前的document文档。因此，在鼠标位置中，我们应该引入document文档body区域的scrollLeft和scrollTop属性。最后，IE中document文档实际并不在\(0,0\)的位置，在它周围有一个小（通常有2px）边框，document.body.clientLeft和document.body.clientTop包含了这个边框的宽度。所有用 

```javascript
evt.clientX + document.body.scrollLeft - document.body.clientLeft //在IE中获得
```

#### JS实现添加事件兼容函数

```javascript
/**
 * 公有函数:"事件处理"兼容函数
 *
 * @param {Object} evnentObj      需要添加事件的对象
 * @param {String} eventType      添加触发事件的类型，如click，不需要加on
 * @param {function} fn           事件函数
 * @param {Boolean} useCapture
 */
function addEvent(evnentObj, eventType, fn, useCapture) {
  if (evnentObj.addEventListener) {
    evnentObj.addEventListener(eventType, fn, false, useCapture); //DOM 2.0
  } else if (evnentObj.attachEvent) {
    evnentObj.attachEvent('on' + eventType, fn); //IE5+
  } else {
    evnentObj['on' + eventType] = fn; //DOM 0.0
  }
}
```

#### JS获取某元素以浏览器左上角为原点的坐标\(有问题\)

```javascript
/**
 * 公有函数:获取某元素以浏览器左上角为原点的坐标
 *
 * @param {Object} obj
 * @returns
 */
function getPoint(obj) {
  var top = obj.offsetTop; //获取该元素对应父容器的上边距
  var left = obj.offsetLeft; //对应父容器的上边距
  var objPoint = {};
  //判断是否有父容器，如果存在则累加其边距
  while (obj = obj.offsetParent) {
    top += obj.offsetTop;
    left += obj.offsetLeft;
  }
  objPoint.top = top;
  objPoint.left = left;

  return objPoint;
}

```

#### JS获取鼠标X.Y轴坐标

```javascript
function mousePosition(evt) {
  evt = evt || window.event;
  //Mozilla
  if (evt.pageX || evt.pageY) {
    return {
      x: evt.pageX,
      y: evt.pageY
    }
  }
  //IE
  return {
    x: evt.clientX + document.body.scrollLeft - document.body.clientLeft,
    y: evt.clientY + document.body.scrollTop - document.body.clientTop
  }
}

```

### Object

#### js实现对象的深Clone

```javascript
//PS:深度克隆：所有元素或属性均完全复制，与原对象完全脱离，也就是说所有对于新对象的修改都不会反映到原对象中。
function cloneObject(o) {
  //首先对传入的对象进行类型判断，
  if (!o || "object" !== typeof o) {
    return o;
  }
  var c = "function" === typeof o.pop ? [] : {};
  var p, v;
  for (p in o) {
    if (o.hasOwnProperty(p)) {
      v = o[p];
      if (v && 'object' === typeof v) {
        c[p] = Ext.ux.clone(v);
      } else {
        c[p] = v;
      }
    }
  }
  return c;
};

```

### Math

#### JS 生成范围随机整数

```javascript
// JS 生成范围随机整数
/**
 * 生成从minNum到maxNum的随机整数
 * @param {number} minNum 
 * @param {number} maxNum 
 * @param {boolean} [status=true] 生成整数 false生成小数
 * @returns 
 */
function randomNum(minNum, maxNum, status = true) {
  let result;
  console.log(arguments.length);
  switch (arguments.length) {
    case 1:
      result = parseInt(Math.random() * minNum + 1, 10);
      break
    case 2:
      result = parseInt(Math.random() * (maxNum - minNum + 1) + minNum, 10);
      break
    case 3:
      if (status) {
        result = parseInt(Math.random() * (maxNum - minNum + 1) + minNum, 10);
        break
      } else {
        result = Math.random() * (maxNum - minNum + 1) + minNum;
        break
      }
    default:
      result = 0;
      break
  }
  return result;
}

```

### XML

#### 转成XML对象

```javascript
/**
  * 转成XML对象
  * 
  * @param {String} str 一个xml格式的串
  * @returns 
  */
function createXml(str) {
  if (document.all) {
    var xmlDom = new ActiveXObject("Microsoft.XMLDOM")
    xmlDom.loadXML(str)
    return xmlDom
  }
  else
    return new DOMParser().parseFromString(str, "text/xml")
}

```

## 常用例子

### 格式化数字串

```javascript
/**
 * 格式化数字串
 * @param {String} str 源字符串
 * @param {Number} size 每隔几个字符进行分割 默认3
 * @param {String} delimiter delimiter-分割符 默认','
 */
function formatText(str, size = 3, delimiter = ',') {
    let _str = str.toString(),
        regText = '\\d{1,' + size + '}(?=(\\d{' + size + '})+$)',
        reg = new RegExp(regText, 'g');

    return _str.replace(/^(-?)(\d+)((\.\d+)?)$/,
        function ($0, $1, $2, $3) {
            return $1 + $2.replace(reg, `$&${delimiter}`) + $3;
        })
}

```

### Js身份证验证函数

```javascript
//            二代身份证号码为 18 位，其最后一位(第 18 位)的计算方法为:
//           1、 将前面的身份证号码 17 位数分别乘以不同的系数。从第一位到第十七位的系数分别 为:7-9-10-5-8-4-2-1-6-3-7-9-10-5-8-4-2
//            2、 将这 17 位数字和系数相乘的结果相加
//           3、 用加出来和除以 11，看余数是多少?
//            4、 余数只可能有 0-1-2-3-4-5-6-7-8-9-10 这 11 个数字。
//               每个数字所对应的 最后一位身份证的号码为:1-0-X-9-8-7-6-5-4-3-2
//               即，如果余数是是 2，就会在身份证的第 18 位数字上出现罗马数字的X。如果余数是 10，身份证的最后一位号码就 是 2
//        身份验证函数
function Authentication() {
  const arrXishu = [7, 9, 10, 5, 8, 4, 2, 1, 6, 3, 7, 9, 10, 5, 8, 4, 2]; //声明系数数组
  var arrch = ['1', '0', 'X', '9', '8', '7', '6', '5', '4', '3', '2']; //声明最后一位身份证号码的数组
  var idcard = document.getElementById("IdCard").value;
  var arrIdcard = idcard.split(""); //字符串转化为数组
  var sum = 0;
  if (arrIdcard.length != 18) {
    return alert("输入的号码有误");
  } else {
    for (var index = 0; index < arrXishu.length; index++) {
      sum += parseInt(arrXishu[index]) * arrXishu[index];
    }
    let c = sum % 11;
    let code = arrch(c);
    if (code == arrIdcard.charAt(17)) {
      alert("身份证号码正确");
    } else {
      alert("身份证号码错误");
    }
  }
}

```

### JS 执行计时器

```javascript
timeStart = new Date().getTime();
timesEnd = new Date().getTime();
document.getElementById("time").innerHTML = timesEnd - timeStart;
```

### JS写入Cookie

```javascript
function setCookie(name, value, expires, path, domain) {
  if (!expires) expires = -1;
  if (!path) path = "/";
  var d = "" + name + "=" + value;
  var e;
  if (expires < 0) {
    e = "";
  } else if (expires == 0) {
    var f = new Date(1970, 1, 1);
    e = ";expires=" + f.toUTCString();
  } else {
    var now = new Date();
    var f = new Date(now.getTime() + expires * 1000);
    e = ";expires=" + f.toUTCString();
  }
  var dm;
  if (!domain) {
    dm = "";
  } else {
    dm = ";domain=" + domain;
  }
  document.cookie = name + "=" + value + ";path=" + path + e + dm;
};

```

### JS 读Cookie

```text
function readCookie(name) {
  var nameEQ = name + "=";
  var ca = document.cookie.split(';');
  for (var i = 0; i < ca.length; i++) {
    var c = ca[i];
    while (c.charAt(0) == ' ') c = c.substring(1, c.length);
    if (c.indexOf(nameEQ) == 0) {
      return decodeURIComponent(c.substring(nameEQ.length, c.length))
    }
  }
  return null
}

```

### 原生Ajax 请求

```javascript
function jsAjax(args) {
  var self = this;
  this.options = {
    type: 'GET',
    async: true,
    contentType: 'application/x-www-form-urlencoded',
    url: 'about:blank',
    data: null,
    success: {},
    error: {}
  };
  this.getXmlHttp = function () {
    var xmlHttp;
    try {
      xmlhttp = new XMLHttpRequest();
    } catch (e) {
      try {
        xmlhttp = new ActiveXObject("Msxml2.XMLHTTP");
      } catch (e) {
        xmlHttp = new ActiveXObject("Microsoft.XMLHTTP");
      }
    }
    if (!xmlhttp) {
      alert('您的浏览器不支持AJAX');
      return false;
    }
    return xmlhttp;
  };
  this.send = function () {
    C.each(self.options, function (key, val) {
      self.options[key] = (args[key] == null) ? val : args[key];
    });

    var xmlHttp = new self.getXmlHttp();
    if (self.options.type.toUpperCase() == 'GET') {
      xmlHttp.open(self.options.type, self.options.url + (self.options.data == null ? "" : ((/[?]$/.test(self.options.url) ? '&' : '?') + self.options.data)), self.options.async);
    } else {
      xmlHttp.open(self.options.type, self.options.url, self.options.async);
      xmlHttp.setRequestHeader('Content-Length', self.options.data.length);
    }
    xmlHttp.setRequestHeader('Content-Type', self.options.contentType);
    xmlHttp.onreadystatechange = function () {
      if (xmlHttp.readyState == 4) {
        if (xmlHttp.status == 200 || xmlHttp.status == 0) {
          if (typeof self.options.success == 'function') self.options.success(xmlHttp.responseText);
          xmlHttp = null;
        } else {
          if (typeof self.options.error == 'function') self.options.error('Server Status: ' + xmlHttp.status);
        }
      }
    };
    xmlHttp.send(self.options.type.toUpperCase() == 'POST' ? self.options.data.toString() : null);
  };
  this.send();
};

```

### JS 加载到顶部LoadJS

```javascript
function loadJS(url, fn) {
  var ss = document.getElementsByName('script'),
    loaded = false;
  for (var i = 0, len = ss.length; i < len; i++) {
    if (ss[i].src && ss[i].getAttribute('src') == url) {
      loaded = true;
      break;
    }
  }
  if (loaded) {
    if (fn && typeof fn != 'undefined' && fn instanceof Function) fn();
    return false;
  }
  var s = document.createElement('script'),
    b = false;
  s.setAttribute('type', 'text/javascript');
  s.setAttribute('src', url);
  s.onload = s.onreadystatechange = function () {
    if (!b && (!this.readyState || this.readyState == 'loaded' || this.readyState == 'complete')) {
      b = true;
      if (fn && typeof fn != 'undefined' && fn instanceof Function) fn();
    }
  };
  document.getElementsByTagName('head')[0].appendChild(s);
};

function bind(objId, eventType, callBack) { //适用于任何浏览器的绑定
  var obj = document.getElementById(objId);
  if (obj.addEventListener) {
    obj.addEventListener(eventType, callBack, false);
  } else if (window.attachEvent) {
    obj.attachEvent('on' + eventType, callBack);
  } else {
    obj['on' + eventType] = callBack;
  }
}

function JSLoad(args) {
  s = document.createElement("script");
  s.setAttribute("type", "text/javascript");
  s.setAttribute("src", args.url);
  s.onload = s.onreadystatechange = function () {
    if (!s.readyState || s.readyState == "loaded" || s.readyState == "complete") {
      if (typeof args.callback == "function") args.callback(this, args);
      s.onload = s.onreadystatechange = null;
      try {
        s.parentNode && s.parentNode.removeChild(s);
      } catch (e) {}
    }
  };
  document.getElementsByTagName("head")[0].appendChild(s);
}

```

### 清空 LoadJS 加载到顶部的js引用

```javascript
function ClearHeadJs(src) {
  var js = document.getElementsByTagName('head')[0].children;
  var obj = null;
  for (var i = 0; i < js.length; i++) {
    if (js[i].tagName.toLowerCase() == "script" && js[i].attributes['src'].value.indexOf(src) > 0) {
      obj = js[i];
    }
  }
  document.getElementsByTagName('head')[0].removeChild(obj);
};

```

### js 动态移除 head 里的 js 引用

```javascript
function ClearHeadJs(src) {
  var js = document.getElementsByTagName('head')[0].children;
  var obj = null;
  for (var i = 0; i < js.length; i++) {
    if (js[i].tagName.toLowerCase() == "script" && js[i].attributes['src'].value.indexOf(src) > 0) {
      obj = js[i];
    }
  }
  document.getElementsByTagName('head')[0].removeChild(obj);
};

```

### 整个URL 点击事件 加在UL里的onclick里

```javascript
function CreateFrom(url, params) {
  var f = document.createElement("form");
  f.setAttribute("action", url);
  for (var i = 0; i < params.length; i++) {
    var input = document.createElement("input");
    input.setAttribute("type", "hidden");
    input.setAttribute("name", params[i].paramName);
    input.setAttribute("value", params[i].paramValue);
    f.appendChild(input);
  }
  f.target = "_blank";
  document.body.appendChild(f);
  f.submit();
};

```

### 获取地址栏某个参数的字段

```text
/**
 * 获取地址栏某个参数的字段
 *
 * @param {any} name
 * @returns
 */
function GetQueryString(name) {
    var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)");
    var r = window.location.search.substr(1).match(reg);
    if (r != null) return unescape(r[2]);
    return null;
}
```

## JS基础

```javascript
javascript函数一共可分为五类： 
•常规函数 
•数组函数 
•日期函数 
•数学函数 
•字符串函数 
1.常规函数 
javascript常规函数包括以下9个函数： 
(1)alert函数：显示一个警告对话框，包括一个OK按钮。 
(2)confirm函数：显示一个确认对话框，包括OK、Cancel按钮。 
(3)escape函数：将字符转换成Unicode码。 
(4)eval函数：计算表达式的结果。 
(5)isNaN函数：测试是(true)否(false)不是一个数字。 
(6)parseFloat函数：将字符串转换成符点数字形式。 
(7)parseInt函数：将符串转换成整数数字形式(可指定几进制)。 
(8)prompt函数：显示一个输入对话框，提示等待用户输入。例如： 
<script language="javascript"> 
<!-- 
alert("输入错误"); 
prompt("请输入您的姓名","姓名"); 
confirm("确定否！"); 
//--> 
script> 
(9)unescape函数：解码由escape函数编码的字符。 
2.数组函数 
javascript数组函数包括以下4个函数： 
(1)join函数：转换并连接数组中的所有元素为一个字符串。例: 
function JoinDemo() 
{ 
var a, b; 
a = new Array(0,1,2,3,4); 
b = a.join("-");//分隔符 
return(b);//返回的b=="0-1-2-3-4" 
} 
(2)length函数：返回数组的长度。例： 
function LengthDemo() 
{ 
var a, l; 
a = new Array(0,1,2,3,4); 
l = a.length; 
return(l);//l==5 
} 
(3)reverse函数：将数组元素顺序颠倒。例： 
function ReverseDemo() 
{ 
var a, l; 
a = new Array(0,1,2,3,4); 
l = a.reverse(); 
return(l); 
} 
(4)sort函数：将数组元素重新排序。例： 
function SortDemo() 
{ 
var a, l; 
a = new Array("X" ,"y" ,"d", "Z", "v","m","r"); 
l = a.sort(); 
return(l); 
} 
3.日期函数 
javascript日期函数包括以下20个函数： 
(1)getDate函数：返回日期的"日"部分，值为1～31。例： 
function DateDemo() 
{ 
var d, s = "Today's date is: "; 
d = new Date(); 
s += (d.getMonth() + 1) + "/"; 
s += d.getDate() + "/"; 
s += d.getYear(); 
return(s); 
} 
(2)getDay函数：返回星期几，值为0～6，其中0表示星期日，1表示星期一，...，6表示星期六。例： 
function DateDemo() 
{ 
var d, day, x, s = "Today is: "; 
var x = new Array("Sunday", "Monday", "Tuesday"); 
var x = x.concat("Wednesday","Thursday", "Friday"); 
var x = x.concat("Saturday"); 
d = new Date(); 
day = d.getDay(); 
return(s += x[day]); 
} 
(3)getHouse函数：返回日期的"小时"部分，值为0～23。例。 
function TimeDemo() 
{ 
var d, s = "The current local time is: "; 
var c = ":"; 
d = new Date(); 
s += d.getHours() + c; 
s += d.getMinutes() + c; 
s += d.getSeconds() + c; 
s += d.getMilliseconds(); 
return(s); 
} 
(4)getMinutes函数：返回日期的"分钟"部分，值为0～59。见上例。 
(5)getMonth函数：返回日期的"月"部分，值为0～11。其中0表示1月，2表示3月，...，11表示12月。见前面的例子。 
(6)getSeconds函数：返回日期的"秒"部分，值为0～59。见前面的例子。 
(7)getTime函数：返回系统时间。 
function GetTimeTest() 
{ 
var d, s, t; 
var MinMilli = 1000 * 60; 
var HrMilli = MinMilli * 60; 
var DyMilli = HrMilli * 24; 
d = new Date(); 
t = d.getTime(); 
s = "It's been " 
s += Math.round(t / DyMilli) + " days since 1/1/70"; 
return(s); 
} 
(8)getTimezoneOffset函数：返回此地区的时差(当地时间与GMT格林威治标准时间的地区时差)，单位为分钟。 
function TZDemo() 
{ 
var d, tz, s = "The current local time is "; 
d = new Date(); 
tz = d.getTimezoneOffset(); 
if (tz < 0) 
s += tz / 60 + " hours before GMT"; 
else if (tz == 0) 
s += "GMT"; 
else 
s += tz / 60 + " hours after GMT"; 
return(s); 
} 
(9)getYear函数：返回日期的"年"部分。返回值以1900年为基数，例如1999年为99。前面有例子。 
(10)parse函数：返回从1970年1月1日零时整算起的毫秒数(当地时间)。 
function GetTimeTest(testdate) 
{ 
var d, s, t; 
var MinMilli = 1000 * 60; 
var HrMilli = MinMilli * 60; 
var DyMilli = HrMilli * 24; 
d = new Date(); 
t = Date.parse(testdate); 
s = "There are " 
s += Math.round(Math.abs(t / DyMilli)) + " days " 
s += "between " + testdate + " and 1/1/70"; 
return(s); 
} 
(11)setDate函数：设定日期的"日"部分，值为0～31。 
(12)setHours函数：设定日期的"小时"部分，值为0～23。 
(13)setMinutes函数：设定日期的"分钟"部分，值为0～59。 
(14)setMonth函数：设定日期的"月"部分，值为0～11。其中0表示1月，...，11表示12月。 
(15)setSeconds函数：设定日期的"秒"部分，值为0～59。 
(16)setTime函数：设定时间。时间数值为1970年1月1日零时整算起的毫秒数。 
(17)setYear函数：设定日期的"年"部分。 
(18)toGMTString函数：转换日期成为字符串，为GMT格林威治标准时间。 
(19)setLocaleString函数：转换日期成为字符串，为当地时间。 
(20)UTC函数：返回从1970年1月1日零时整算起的毫秒数，以GMT格林威治标准时间计算。 
4.数学函数 
javascript数学函数其实就是Math对象，它包括属性和函数(或称方法)两部分。其中，属性主要有下列内容。 
Math.e:e(自然对数)、Math.LN2（2的自然对数)、Math.LN10(10的自然对数)、Math.LOG2E(e的对数，底数为 2)、Math.LOG10E(e的对数，底数为10)、Math.PI(π)、Math.SQRT1_2(1/2的平方根值)、Math.SQRT2 (2的平方根值)。 
函数有以下18个： 
(1)abs函数：即Math.abs(以下同)，返回一个数字的绝对值。 
(2)acos函数：返回一个数字的反余弦值，结果为0～π弧度(radians)。 
(3)asin函数：返回一个数字的反正弦值，结果为-π/2～π/2弧度。 
(4)atan函数：返回一个数字的反正切值，结果为-π/2～π/2弧度。 
(5)atan2函数：返回一个坐标的极坐标角度值。 
(6)ceil函数：返回一个数字的最小整数值(大于或等于)。 
(7)cos函数：返回一个数字的余弦值，结果为-1～1。 
(8)exp函数：返回e(自然对数)的乘方值。 
(9)floor函数：返回一个数字的最大整数值(小于或等于)。 
(10)log函数：自然对数函数，返回一个数字的自然对数(e)值。 
(11)max函数：返回两个数的最大值。 
(12)min函数：返回两个数的最小值。 
(13)pow函数：返回一个数字的乘方值。 
(14)random函数：返回一个0～1的随机数值。 
(15)round函数：返回一个数字的四舍五入值，类型是整数。 
(16)sin函数：返回一个数字的正弦值，结果为-1～1。 
(17)sqrt函数：返回一个数字的平方根值。 
(18)tan函数：返回一个数字的正切值。 
5.字符串函数 
javascript字符串函数完成对字符串的字体大小、颜色、长度和查找等操作，共包括以下20个函数： 
(1)anchor函数：产生一个链接点(anchor)以作超级链接用。anchor函数设定的链接点的名称，另一个函数link设定的URL地址。 
(2)big函数：将字体加到一号，与...标签结果相同。 
(3)blink函数：使字符串闪烁，与...标签结果相同。 
(4)bold函数：使字体加粗，与...标签结果相同。 
(5)charAt函数：返回字符串中指定的某个字符。 
(6)fixed函数：将字体设定为固定宽度字体，与...标签结果相同。 
(7)fontcolor函数：设定字体颜色，与标签结果相同。 
(8)fontsize函数：设定字体大小，与标签结果相同。 
(9)indexOf函数：返回字符串中第一个查找到的下标index，从左边开始查找。 
(10)italics函数：使字体成为斜体字，与...标签结果相同。 
(11)lastIndexOf函数：返回字符串中第一个查找到的下标index，从右边开始查找。 
(12)length函数：返回字符串的长度。(不用带括号) 
(13)link函数：产生一个超级链接，相当于设定的URL地址。 
(14)small函数：将字体减小一号，与...标签结果相同。 
(15)strike函数：在文本的中间加一条横线，与...标签结果相同。 
(16)sub函数：显示字符串为下标字(subscript)。 
(17)substring函数：返回字符串中指定的几个字符。 
(18)sup函数：显示字符串为上标字(superscript)。 
(19)toLowerCase函数：将字符串转换为小写。 
(20)toUpperCase函数：将字符串转换为大写。
标识可放入head>.. 或 ...之间。将JavaScript标识放置... 在头部之间，使之在主页和其余部分代码之前装载，从而可使代码的功能更强大；将JavaScript标识放置在... 主体之间以实现某些部分动态地创建文档。
通过标识说明：若不认识JavaScript代码的浏览器，则所有在其中的标识均被忽略；若认识，则执行其结果。使用注释这是一个好的编程习惯，它使其他人可以读懂你的语言。
1.	alert()是JavaScript的窗口对象方法，其功能是弹出一个具有OK对话框并显示（）中的字符串。
比如：
2.	Document. write()是文档对象的输出函数，其功能是将括号中的字符或变量值输出到窗口；document. close()是将输出关闭。
比如：
3.	window.external.AddFavorite(' ', '希望网络技术站') 提示把网站加入收藏夹
 
onload=favorate() 要加在标签处，如：
※ 如果你想在离开网页时提示加为收藏夹，只需要把 
onunload=favorate() 改成 onload=favorate() 即可
4.	close()//关闭窗口，如果窗口不是用脚本打开的，会弹出确认对话框。
如：退出系统或
退出系统
给我联系
5.	confirm() 
//弹出“确定/取消”对话框
6.	function document.oncontextmenu()// 禁止鼠标右键；
7.	function document.onselectstart()// 禁止选取
8.	window.prompt()就是一个窗口对象的方法，其基本作用是，当装入Web页面时在屏幕上显示一个具有“确定”和“取消”的对话框，让你输出数据。
 
alert()方法能创建一个具有OK按钮的对话框；
confirm()方法为编程人员提供一个具有两个按钮的对话框；
prompt()方法允许用户在对话框中输入信息，并可使用默认值，其基本格式如下：
prompt（“提示信息”，默认值）
9.	Window .open()是打开一个新窗口。
基本格式为：Window .open("URL","窗口名字","窗口属性")
window属性参数是由一个字符串列表项它由逗号分隔，它指明了有关新创建窗口的属性。
参 数	设定值	含 义
toolbar	yes/no	建立或不建立标准工具条
location	yes/no	建立或不建立位置输入字段
directions	yes/no	建立或不建立标准目录按钮
status	yes/no	建立或不建立状态条
menubar	yes/no	建立或不建立菜单条
scrollbar	yes/no	建立或不建立滚动条
revisable	yes/no	能否改变窗口大小
width	yes/no	确定窗口的宽度
Height	yes/no	确定窗口的高度。
10.	信息数据的输出显示。比较常用的有window.alert()、document.write和及document.writln()方法。
write()和writeln()方法都是用于向浏览器窗口输出文本字串；二者的唯一区别就是writeln()方法自动在文本之后加入回车符。
alert()方法是window对象的一个方法，因此在使用时，不需要写window窗口对象名，而是直接使用就行了。它主要用途用在输出时产生有关警告提示信息或提示用户，一旦用户按“确定”钮后，方可继续执行其他脚本程序。
11.	document.write(document.lastModified)可以产生最后修改日期。
 
JavaScript 本身是会区分大小写的， lastmodified 与 lastModified，在它看来是不同的结果。document.lastModified 参数在 Netscape 2.0 beta 2 版时是被写成documeut.lastmodified 的，然而，之後的版本就改为 document.lastModified。所以书写时要注意大小写。
12.	在传统的标签中加入onMouseOver的method，可以达到一定的效果。
如：
 
window.status是用来让你可以在WWW浏览器的状态列上显示一些讯息用的。在语法中， 你 可以看到讯息部分是用' 括起来的部分，而非以" 括起来，在讯息部分结束之后， 必须加 上 ; return true。
可以用onMouseOver的method配合事件发生时去呼叫函数。
 
 

```

```javascript
1.document.write(""); 输出语句
2.JS中的注释为//
3.传统的HTML文档顺序是:document->html->(head,body)
4.一个浏览器窗口中的DOM顺序是:window->(navigator,screen,history,location,document)
5.得到表单中元素的名称和值:document.getElementById("表单中元素的ID号").name(或value)
6.一个小写转大写的JS: document.getElementById("output").value = document.getElementById("input").value.toUpperCase();
7.JS中的值类型:String,Number,Boolean,Null,Object,Function
8.JS中的字符型转换成数值型:parseInt(),parseFloat()
9.JS中的数字转换成字符型:(""+变量)
10.JS中的取字符串长度是:(length)
11.JS中的字符与字符相连接使用+号.
12.JS中的比较操作符有:==等于,!=不等于,>,>=,<.<=
13.JS中声明变量使用:var来进行声明
14.JS中的判断语句结构:if(condition){}else{}
15.JS中的循环结构:for([initial expression];[condition];[upadte expression]) {inside loop}
16.循环中止的命令是:break
17.JS中的函数定义:function functionName([parameter],...){statement[s]}
18.当文件中出现多个form表单时.可以用document.forms[0],document.forms[1]来代替.
19.窗口:打开窗口window.open(), 关闭一个窗口:window.close(), 窗口本身:self
20.状态栏的设置:window.status="字符";
21.弹出提示信息:window.alert("字符");
22.弹出确认框:window.confirm();
23.弹出输入提示框:window.prompt();
24.指定当前显示链接的位置:window.location.href="URL"
25.取出窗体中的所有表单的数量:document.forms.length
26.关闭文档的输出流:document.close();
27.字符串追加连接符:+=
28.创建一个文档元素:document.createElement(),document.createTextNode()
29.得到元素的方法:document.getElementById()
30.设置表单中所有文本型的成员的值为空:
 var form = window.document.forms[0]
 for (var i = 0; i<form.elements.length;i++){
     if (form.elements[i].type == "text"){
         form.elements[i].value = "";
     }
 }
31.复选按钮在JS中判断是否选中:document.forms[0].checkThis.checked (checked属性代表为是否选中返回TRUE或FALSE)
32.单选按钮组(单选按钮的名称必须相同):取单选按钮组的长度document.forms[0].groupName.length
33.单选按钮组判断是否被选中也是用checked.
34.下拉列表框的值:document.forms[0].selectName.options[n].value (n有时用下拉列表框名称加上.selectedIndex来确定被选中的值)
35.字符串的定义:var myString = new String("This is lightsword");
36.字符串转成大写:string.toUpperCase(); 字符串转成小写:string.toLowerCase();
37.返回字符串2在字符串1中出现的位置:String1.indexOf("String2")!=-1则说明没找到.
38.取字符串中指定位置的一个字符:StringA.charAt(9);
39.取出字符串中指定起点和终点的子字符串:stringA.substring(2,6);
40.数学函数:Math.PI(返回圆周率),Math.SQRT2(返回开方),Math.max(value1,value2)返回两个数中的最在值,Math.pow(value1,10)返回value1的十次方,Math.round(value1)四舍五入函数,Math.floor(Math.random()*(n+1))返回随机数
41.定义日期型变量:var today = new Date();
42.日期函数列表:dateObj.getTime()得到时间,dateObj.getYear()得到年份,dateObj.getFullYear()得到四位的年份,dateObj
.getMonth()得到月份,dateObj.getDate()得到日,dateObj.getDay()得到日期几,dateObj.getHours()得到小时,dateObj.getMinutes()得到分,dateObj.getSeconds()得到秒,dateObj.setTime(value)设置时间,dateObj.setYear(val)设置年,dateObj.setMonth(val)设置月,dateObj.setDate(val)设置日,dateObj.setDay(val)设置星期几,dateObj.setHours设置小时,dateObj.setMinutes(val)设置分,dateObj.setSeconds(val)设置秒  [注意:此日期时间从0开始计]
43.FRAME的表示方式: [window.]frames[n].ObjFuncVarName,frames["frameName"].ObjFuncVarName,frameName.ObjFuncVarName
44.parent代表父亲对象,top代表最顶端对象
45.打开子窗口的父窗口为:opener
46.表示当前所属的位置:this
47.当在超链接中调用JS函数时用:(Javascript:)来开头后面加函数名
48.在老的浏览器中不执行此JS:<!--      //-->
49.引用一个文件式的JS:<script type="text/Javascript" src="aaa.js"></script>
50.指定在不支持脚本的浏览器显示的HTML:<noscript></noscript>
51.当超链和ONCLICK事件都有时,则老版本的浏览器转向a.html,否则转向b.html.例:<a href="a.html" onclick="location.href='b.html';return false">dfsadf</a>
52.JS的内建对象有:Array,Boolean,Date,Error,EvalError,Function,Math,Number,Object,RangeError,ReferenceError,RegExp,String,SyntaxError,TypeError,URIError
53.JS中的换行:\n
54.窗口全屏大小:<script>function fullScreen(){ this.moveTo(0,0);this.outerWidth=screen.availWidth;this.outerHeight=screen.availHeight;}window.maximize=fullScreen;</script>
55.JS中的all代表其下层的全部元素
56.JS中的焦点顺序:document.getElementByid("表单元素").tabIndex = 1
57.innerHTML的值是表单元素的值:如<p id="para">"how are <em>you</em>"</p>,则innerHTML的值就是:how are <em>you</em>
58.innerTEXT的值和上面的一样,只不过不会把<em>这种标记显示出来.
59.contentEditable可设置元素是否可被修改,isContentEditable返回是否可修改的状态.
60.isDisabled判断是否为禁止状态.disabled设置禁止状态
61.length取得长度,返回整型数值
62.addBehavior()是一种JS调用的外部函数文件其扩展名为.htc
63.window.focus()使当前的窗口在所有窗口之前.
64.blur()指失去焦点.与FOCUS()相反.
65.select()指元素为选中状态.
66.防止用户对文本框中输入文本:onfocus="this.blur()"
67.取出该元素在页面中出现的数量:document.all.tags("div(或其它HTML标记符)").length
68.JS中分为两种窗体输出:模态和非模态.window.showModaldialog(),window.showModeless()
69.状态栏文字的设置:window.status='文字',默认的状态栏文字设置:window.defaultStatus = '文字.';
70.添加到收藏夹:external.AddFavorite("http://www.xrss.cn","jaskdlf");
71.JS中遇到脚本错误时不做任何操作:window.onerror = doNothing; 指定错误句柄的语法为:window.onerror = handleError;
72.JS中指定当前打开窗口的父窗口:windo
w.opener,支持opener.opener...的多重继续.
73.JS中的self指的是当前的窗口
74.JS中状态栏显示内容:window.status="内容"
75.JS中的top指的是框架集中最顶层的框架
76.JS中关闭当前的窗口:window.close();
77.JS中提出是否确认的框:if(confirm("Are you sure?")){alert("ok");}else{alert("Not Ok");}
78.JS中的窗口重定向:window.navigate("http://www.sina.com.cn");
79.JS中的打印:window.print()
80.JS中的提示输入框:window.prompt("message","defaultReply");
81.JS中的窗口滚动条:window.scroll(x,y)
82.JS中的窗口滚动到位置:window.scrollby
83.JS中设置时间间隔:setInterval("expr",msecDelay)或setInterval(funcRef,msecDelay)或setTimeout
84.JS中的模态显示在IE4+行,在NN中不行:showModalDialog("URL"[,arguments][,features]);
85.JS中的退出之前使用的句柄:function verifyClose(){event.returnValue="we really like you and hope you will stay longer.";}}  window.onbeforeunload=verifyClose;
86.当窗体第一次调用时使用的文件句柄:onload()
87.当窗体关闭时调用的文件句柄:onunload()
88.window.location的属性: protocol(http:),hostname(www.example.com),port(80),host(www.example.com:80),pathname("/a/a.html"),hash("#giantGizmo",指跳转到相应的锚记),href(全部的信息)
89.window.location.reload()刷新当前页面.
89-1.parent.location.reload()刷新父亲对象（用于框架）
89-2.opener.location.reload()刷新父窗口对象（用于单开窗口）
89-3.top.location.reload()刷新最顶端对象（用于多开窗口）
90.window.history.back()返回上一页,window.history.forward()返回下一页,window.history.go(返回第几页,也可以使用访问过的URL)
91.document.write()不换行的输出,document.writeln()换行输出
92.document.body.noWrap=true;防止链接文字折行.
93.变量名.charAt(第几位),取该变量的第几位的字符.
94."abc".charCodeAt(第几个),返回第几个字符的ASCii码值.
95.字符串连接:string.concat(string2),或用+=进行连接
96.变量.indexOf("字符",起始位置),返回第一个出现的位置(从0开始计算)
97.string.lastIndexOf(searchString[,startIndex])最后一次出现的位置.
98.string.match(regExpression),判断字符是否匹配.
99.string.replace(regExpression,replaceString)替换现有字符串.
100.string.split(分隔符)返回一个数组存储值.
101.string.substr(start[,length])取从第几位到指定长度的字符串.
102.string.toLowerCase()使字符串全部变为小写.
103.string.toUpperCase()使全部字符变为大写.
104.parseInt(string[,radix(代表进制)])强制转换成整型.
105.parseFloat(string[,radix])强制转换成浮点型.
106.isNaN(变量):测试是否为数值型.
107.定义常量的关键字:const,定义变量的关键字:var

```

```javascript
4.格式化字符串变量  
<script>  
str1="peace,happiness and prosperity.<br>"  
document.write(str1)  
document.write(str1.big())  
document.write(str1.small())  
document.write(str1.bold())  
document.write(str1.italics())  
document.write(str1.strike())  
document.write(str1.fontsize(6))  
document.write(str1.fontcolor(green))  
</script>  
5.创建锚和链接  
<script>  
str1="this is the bigginning of the page.<br>"  
str2="….<br>"  
str3="this is the end of the page .<br>"  
str4="link to the start<br>"  
str5="link to the end<br>"  
document.write(str1.anchor("start"))  
for(i=0;i<10;i++)  
document.write(str2);  
document.write(str3.anchor("end"))  
document.write(str4.link("#start"))  
document.write(str5.link("#end"))  
</script>  
6.确定字符串长度  
<script>  
str1="this is the bigginning of the page."  
document.write(str1+"<br>")  
document.write( "字符串的长度是:"+str1.length)  
document.write("字符串全部大写是;"+str1.toUpperCase())  
document.write("字符串全部小写是;"+str1.toLowerCase())  
</script>  
7.在字符串内搜索 
<script>  
str1="this is the end of the line.<br>"  
document.write(str1)  
document.write("字符end在字符串的位置是"+str1.search("end"))  
document.write("字符dog在字符串的位置是"+str1.search("dog"))  
</script>  
8.定位字符串中的字符  
<script>  
str1="spring is a time for flowers and trees and baby bunnles<br>"  
document.write(str1)  
document.write("the index for the second word ‘and' is"+str1.indexOf("and",30))  
documednt.write("the last index of the word ‘and' is "+str1.lastIndexOf("and"))  
</script>  
9.替换字符串中的文本  
<script>  
str1="spring is a time for flowers and trees and baby bunnles<br>"  
document.write(str1)  
document .write(str1.replace("and",","))  
</script>  
10.字符串分离  
<script>  
str1="spring is a time for flowers and trees and baby bunnles<br>"  
document.write(str1)  
str1array=str1.split(" ")  
document.write(str1array[0]+"<br>")  
document.write(str1array[1]+"<br>")  
document.write(str1array[2]+"<br>")  
document.write(str1array[3]+"<br>")  
</script>  
第十章 使用日期和时间  
1.使用Date对象  
<script>  
cdate=new Date("august 2,1989 12:30:00")  
document.write(cdate)  
</script>  
2.显示当地时间和日期  
<script>  
cdate=new Date()  
document.write("当前时间是:"+cdate.toGMTString()+"<br>")  
document.write("日期和时间是:"+cdate.toLocaleString())  
</script>  
3.获得时间和日期值  
<script>  
cdate=new Date()  
document.write("显示当前的星期"+cdate.getDay()+"<br>")  
document.write("显示当前的月份"+cdate.getMonth()+"<br>")  
document.write("显示当前的日期"+cdate.getDay()+"<br>")  
document.write("显示当前的年份"+cdate.getYear()+"<br>")  
document.write("显示当前的小时"+cdate.getHours()+"<br>")  
document.write("显示当前的分钟"+cdate.getMinutes()+"<br>")  
document.write("显示当前的秒"+cdate.getSeconds()+"<br>")  
</script>  
4.设置时间和日期值  
<script language=javascript>  
cdate=new Date("December 25,1984")  
document.write("显示日期"+cdate+"<br>")  
document.write("设置月份"+cdate.setMonth(10)+"<br>")  
document.write("设置日期"+cdate.setDate(23)+"<br>")  
document.write("设置年份"+cdate.setYear(2000)+"<br>")  
document.write("设置小时"+cdate.setHours(13)+"<br>");  
document.write("设置分钟"+cdate.setMinutes(47)+"<br>");  
document.write("设置秒"+cdate.setSeconds(23)+"<br>");  
document.write("显示设置后的日期和时间"+cdate);  
</script>  
第十一章 使用Math对象  
1. 使用Math对象  
<script language=javascript>  
</script>  
<form name=form1>  
圆的半径:<input type=text name=rad><br>  
圆的面积:<input type=text name=area><br>  
<input type=button name=button1 value=计算圆的面积 onclick=document.form1.area.value=document.form1.rad.value*document.  
form1.rad.value*Math.PI>  
</form>  
2.生成随机数  
<script>  
array1=new Array(  
"这是第1句",  
"这是第2句",  
"这是第3句",  
"这是第4句",  
"这是第5句",  
"这是第6句")  
RandomNo=Math.floor(array1.length*Math.random())  
document.write("随机输出某一句"+"<br>"+array1[RandomNo])  
</script>  
3.使用平方根  
<form name=form1>  
value:<input type=text name=va1><br>  
平方根<input type=text name=sqrt><br>  
<input type=button name=button1 value=计算平方根  
onclick="document.form1.sqrt.value=Math.sqrt(document.form1.va1.value)">  
</form>  
4.数字的舍入  
<form name=form1>  
输入<input type=text name=val><br>  
舍入的结果<input type=text name=round><br>  
<input type=button name=button1 value=计算结果 onclick=document.form1.round.value=Math.round(document.form1.val.value)>  
</form>  
5.乘方运算  
<form name=form1>  
底数<input type=text name=val><br>  
指数<input type=text name=power><br>  
幂<input type=text name=result><br>  
<input type=button name=button1 value=计算结果 onclick="document.form1.result.value=Math.pow  
(document.form1.val.value,document.form1.power.value)">  
</form>  
6.发现最小值和最大值  
<form name=form1>  
数字1<input type=text name=val1><br>  
数字2<input type=text name=val2><br>  
最小值<input type=text name=min><br>  
最大值<input type=text name=max><br>  
数字1<input type=button value=计算 onclick="document.form1.min.value=Math.min (document.form1.val1.value,document.form1.val2.value);document.form1.  
max.value= Math.max(document.form1.val1.value,document.form1.val2.value)">  
</form>  
第十二章 使用表单  
1.使用文本框  
<form name=form1>  
<input type=text value="information ,please"name=text1>  
</form>  
<script>  
document.write("表单text1类型是: "+document.form1.text1.type+"<br>")  
document.write("表单text1名称是: "+document.form1.text1.name+"<br>")  
document.write("表单text1值是: "+document.form1.text1.value+"<br>")  
document.write("表单text1大小是: "+document.form1.text1.size+"<br>")  
</script>  
<form name=form1>  
<input type=text name=text1 value=click here  
onfocus=document.form1.text1.select()>  
</form>  
2.使用密码框  
<form name=form1>  
<input type=password name=pw1 value=daylight>  
</form>  
<script>  
document.write("表单pw1的类型:"+document.form1.pw1.type+"<br>")  
document.write("表单pw1的名称:"+document.form1.pw1.name+"<br>")  
document.write("表单pw1的值:"+document.form1.pw1.value+"<br>")  
document.write("表单pw1的大小:"+document.form1.pw1.size+"<br>")  
</script>  
3.使用隐藏字段  
<form name=form1>  
<input type=hidden name=hid1 value=piece of eight>  
</form>  
<script>  
document.write("表单hid1的类型:"+document.form1.hid1.type+"<br>")  
document.write("表单hid1的名称:"+document.form1.hid1.name+"<br>")  
document.write("表单hid1的值:"+document.form1.hid1.value+"<br>")  
</script>  
4.使用文本区域框  
<form name=form1>  
<textarea name=ta1>how many grains of sand are there in the sahara desert?</textarea>  
</form>  
<script>  
document.write("表单ta1的类型:"+document.form1.ta1.type+"<br>")  
document.write("表单ta1的名称:"+document.form1.ta1.name+"<br>")  
document.write("表单ta1的值:"+document.form1.ta1.value+"<br>")  
document.write("表单ta1的横向宽度:"+document.form1.ta1.cols+"<br>")  
document.write("表单ta1的纵向宽度:"+document.form1.rows.value+"<br>")  
</script>  
6.使用重置按钮  
<form name=form1>  
<input type=reset name=reset1 value="rest form">  
</form>  
<script>  
document.write("表单reset1的类型:"+document.form1.reset1.type+"<br>")  
document.write("表单reset1的名称:"+document.form1.reset1.name+"<br>")  
document.write("表单reset1的值:"+document.form1.reset1.value+"<br>")  
</script>  
7.使用提交按钮  
<form name=form1>  
<input type=submit name=submit1 value="submit form">  
</form>  
<script>  
document.write("表单submit1的类型:"+document.form1.submit1.type+"<br>")  
document.write("表单submit1的名称:"+document.form1.submit1.name+"<br>")  
document.write("表单submit1的值:"+document.form1.submit1.value+"<br>")  
</script>  
8.使用复选按钮  
<form name=form1>  
<input type=checkbox name=cb1 >computer savvy?  
</form>  
<script>  
document.write("表单cb1的类型:"+document.form1.cb1.type+"<br>")  
document.write("表单cb1是否被选择?:"+document.form1.cb1.checked+"<br>")  
document.write("表单cb1的名称:"+document.form1.cb1.name+"<br>")  
</script>  
9.使用单选按钮  
<form name=form1>  
<input type=radio name=radio1>male  
<input type=radio name=radio1>female  
</form>  
<script>  
document.write("第一个按钮被选择"+document.form1.radio1[0].checked+"<br>")  
document.write("第二个按钮被选择"+document.form1.radio1[1].checked+"<br>")  
document.write("按钮的名称"+ document.form1.radio1[0].name+"<br>")  
document.write("按钮的个数"+document.form1.radio1.length)  
</script>  
10.使用选择列表  
<form name=form1>  
<select name=select1 size=4>  
<option name=option1 value=lon>london,England</option>  
<option name=option2 value=dub>Dublin,Ireland</option>  
</select>  
</form>  
<script>  
document.write("这个选择列表的名称"+document.form1.select1.name+"<br>")  
document.write("这个选择列表的长度"+document.form1.select1.length+"<br>")  
document.write("这个选择列表当前被选择的索引号"+document.form1.select1.selectedIndex+"<br>")  
document.write("这个选择列表的尺寸"+document.form1.select1.size+"<br>")  
</script>  
11.验证表单的有效性  
<script>  
function validate(){  
if(document.form1.text1.value!='1'||'2'||'3'||'4'){  
alert("请输入1~4的整数")  
}  
}  
</script>  
<form name=form1>  
请输入1~4的整数:  
<input type=text name=text1 size=4 onchange=validate()>  
</form>  
12.控制表单焦点  
<form name=form1>  
<input type=text name=text1 value=where is you focus?><br>  
<input type=text name=text2 value=is there?><br>  
<input type=text name=text3 value=or maybe here?><br>  
<input type=button name=button1 value="text box #1" onclick=document.form1.text1.focus()><br>  
<input type=button name=button2 value="text box #2" onclick=document.form1.text2.focus()><br>  
<input type=button name=button3 value="text box #3" onclick=document.form1.text3.focus()><br>  
</form>  
第十三章 使用分栏  
第十四章 使用navigator  
1.使用navigator对象  
<script>  
document.write("navigator对象的属性"+"<br>")  
document.write("appcodename:"+navigator.appCodeName+"<br>")  
document.write("appname::"+navigator.appName+"<br>")  
document.write("appversion:"+navigator.appVersion+"<br>")  
document.write("platform:"+navigator.platform+"<br>")  
document.write("userAgent:"+navigator.userAgent+"<br>")  
</script>  
<script>  
document.write("navigator对象的方法"+"<br>")  
document.write("javaEnabled():"+navigator.javaEnabled())  
</script>  
2.检查用户的浏览器  
<script>  
if(navigator.appName.indexOf("Microsoft")!=-1){  
document.write("用户浏览器是微软的IE浏览器"+"<br>")}  
else if(navigator.appName.indexOf("Netscape")!=-1){  
document.write("用户浏览器是netscape的netscape浏览器"+"<br>")}  
if(navigator.appVersion.indexOf("4.0")!=-1){  
document.write("you are using a version 4.0compatible browser")  
}  
else{  
document.write("this browser is not 4.0 compliant")}  
</script>  
3.检测用户的操作系统  
<script>  
if (navigator.platform.indexOf("win32")!=-1){  
document.write("you are using a computer running windows 95 or highter")}  
else{  
document.write("this computer is not running windows 95 or higher")}  
</script>  
4.使用location对象  
<script>  
document.write("location对象的属性"+"<br>")  
document.write("hash"+location.hash+"<br>")  
document.write("hostname"+location.hostname+"<br>")  
document.write("host"+location.host+"<br>")  
document.write("href"+location.href+"<br>")  
document.write("port"+location.port+"<br>")  
document.write("search"+location.search+"<br>")  
</script>  
重新加载网页  
<form name=form1>  
<input type=button name=button1 value=重新加载本页 onclick=location.reload>  
</form>  
5.使用cookie  
<script>  
finction makecookie(){  
if(!document.cookie){  
name=prompt("请输入你的姓名");  
document.cookie="name="+name+";";}  
}  
</script>  
<body onload=makecookie()>  
<script>  
function makecookie(){  
if(!document.cookie){  
name=prompt("请输入你的姓名")  
document.cookie="name="+name+";";  
namestart=document.cookie.indexOf("=");  
nameend=document.cookieindexOf(";");  
document.writeln("your name is:" 
+document.cookie.substring(namestart+1,nameend)+",br>")  
}  
}  
</script>

```



