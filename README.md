# Base
常用js汇总

1.获取当前时间戳
```
+ new Date()
```

2.去掉所有的空格
```
function trim(str) {
  return str.replace(/\s/g, "")
}
```

3.去掉左边的空格
```
funtion ltrim(str) {
  return str.replace(/(^\s*)/, "")
}
```

4.去掉右边的空格
```
function rtrim(str) {
  return str.replace(/\s+$/g, "")
}
```

5.去掉两边的空格
```
function lrtrim(str) {
  return strr.replace(/(^\s*)|(\s*$)/g, '')
}
or
str.trim()
```

6.浮点型相加
```
function addFloat(num1, num2) {
  var r1,r2,m;
  r1 = num1.toString().split(".")[1].length;
  r2 = num2.toString().split(".")[1].length;
  m = Math.pow(10, Math.max(r1,r2));
  return (num1 * m + num2 * m) / m;
}
```
7.浮点型相除
```
function divFloat(num1,num2){
  var r1,r2,m;
  r1 = num1.toString().split(".")[1].length;
  r2 = num2.toString().split(".")[1].length;
  m = Math.pow(10, Math.max(r1,r2));
  return (num1 * m) / (num2 * m); 
}
```

8.浮点型相乘
```
function accFloat(num1,num2){
  var r1,r2,m;
  r1 = num1.toString().split(".")[1].length;
  r2 = num2.toString().split(".")[1].length;
  m = Math.pow(10, Math.max(r1,r2));
  return (num1 * m) / (num2 * m)/m;
}

```
9.判断对象是否为空
```
function isEmptyObject(obj) {
  var name ;
  if ( name in obj ) {
    return false;
  };
  return true;
}
```

10.判断是否是对象
```
function isObject(obj){
  return Object.prototype.toString.call(obj) === "[object Object]" ? true : false;
  //return obj !== null && typeof obj === 'object';
}

```
11.数组去重
```
function unique(arr) {
  var result = []; 
  for (var i = 0; i < arr.length; i++){
    if (result.indexOf(arr[i]) == -1) result.push(arr[i]);
  }
  return result;
}
or 
[...new Set(arr)]
```

12.数组交集
```
function jj(a, b) { 
  var result = [];
  for(var i = 0; i < b.length; i ++) {
    var temp = b[i];
    for(var j = 0; j < a.length; j ++) {
      if(temp === a[j]) {
        result.push(temp);
        break;
      }
    }
  }
  return unique(result);
}
or 
[...new Set(arr.filter(v => arr1.indexOf(v) !== -1))]
```

13.数组并集
```
function bj(a, b) { 
  return unique(a.concat(b));
}
or
[...new Set([...arr, ...arr1])]
```

14.数组差集
```
function cj(a, b) {
  var clone = a.slice(0);
  for(var i = 0; i < b.length; i ++) {
    var temp = b[i];
    for(var j = 0; j < clone.length; j ++) {
      if(temp === clone[j]) {
        clone.splice(j,1);
      }
    }
  }
  return unique(clone);
}
or 
[...new Set(arr.concat(arr1).filter(v => !new Set(arr).has(v) || !new Set(arr1).has(v))) ]
```

15.统计数组中出现元素最多元素和次数
```
function count(str){
  var obj = {};
  var letter;
  var count = [];
  for(var i = 0,len = str.length;i<len;i++){
    letter = str[i];
    if(!obj[letter]){
      obj[letter] = 1;
    }else{
      obj[letter]++;
    }
  }
  var max_key,max_num=0;
  for(key in obj){
    if(max_num <obj[key]){
      max_num = obj[key];
      max_key = key;
    }
  }
  count.push(max_key);
  count.push(max_num);
  return count;
}
```

16.判断字符是否在数组中
```
/**
 * @ param ele 字符  arr 数组 i 从哪个位置开始
 **/
function inArray(ele,arr,i){
  var inArr = [];
  if (arr) {
    if (inArr.indexOf) {
      return inArr.indexOf.call(arr,ele,i);
    }
  }
}
```

17.英语首字母大写
```
function titleCase(words){
  if (typeof words === 'string') {
    var word = words.split(" ");
    for (var i = 0; i < word.length; i++) {
      word[i] = word[i].charAt(0).toUpperCase() + word[i].slice(1);
    };
    return word.join(" ");
  } else {
    return words;
  }
}
```
18.获取cookie
```
function getCookie(name) {
  var arr = document.cookie.match(new RegExp("(^| )" + name + "=([^;]*)(;|$)"));
  if (arr != null) return unescape(arr[2]);
  return null;
}
```

19.设置cookie
```
function setCookie(name, value, Hours) {
  var d = new Date();
  var offset = 8;
  var utc = d.getTime() + (d.getTimezoneOffset() * 60000);
  var nd = utc + (3600000 * offset);
  var exp = new Date(nd);
  exp.setTime(exp.getTime() + Hours * 60 * 60 * 1000);
  document.cookie = name + "=" + escape(value) + ";path=/;expires=" + exp.toGMTString() + ";"
}
```
20.获取URL参数
```
function getParam(name){
  var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)", "i"); 
  var r = window.location.search.substr(1).match(reg); 
  if (r != null) return unescape(r[2]); return null; 
}
```









