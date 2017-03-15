#### 题目
* 参考以下示例代码，页面加载后，将提供的空气质量数据数组，按照某种逻辑（比如空气质量大于60）进行过滤筛选，最后将符合条件的数据按照一定的格式要求显示
```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>IFE JavaScript Task 01</title>
  </head>
<body>

  <h3>污染城市列表</h3>
  <ul id="aqi-list">
<!--   
    <li>第一名：福州（样例），10</li>
      <li>第二名：福州（样例），10</li> -->
  </ul>

<script type="text/javascript">

var aqiData = [
  ["北京", 90],
  ["上海", 50],
  ["福州", 10],
  ["广州", 50],
  ["成都", 90],
  ["西安", 100]
];

(function () {

  /*
  在注释下方编写代码
  遍历读取aqiData中各个城市的数据
  将空气质量指数大于60的城市显示到aqi-list的列表中
  */

})();

</script>
</body>
</html>
```
* 第一步用for循环获取数据
* 将数字数据添加到一个新数组
* 筛选数据进行判断

* 对新数组用sort()方法进行排序
* 将结果添加到html中

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>IFE JavaScript Task 01</title>
  </head>
<body>

  <h3>污染城市列表</h3>
  <ul id="aqi-list">
<!--   
    <li>第一名：福州（样例），10</li>
      <li>第二名：福州（样例），10</li> -->
  </ul>

<script type="text/javascript">

var aqiData = [
  ["北京", 90],
  ["上海", 50],
  ["福州", 10],
  ["广州", 50],
  ["成都", 90],
  ["西安", 100]
];
function sortNumber(a,b)
{
return a - b
}

(function () {
  var arr = new Array()
  var ul = document.getElementById('aqi-list');
  var str = '';
  var n=0;
  //用for循环获取数据
  for (var i = 0; i < aqiData.length; i++) {
    //将数字数据添加到一个新数组
    arr[i] = aqiData[i][1];
    //筛选数据进行判断
    if(arr[i]>60){
      
      var sort = arr.sort(sortNumber);
      n++;
      //对新数组用sort()方法进行排序
      str += '<li>第'+n+'名：'+aqiData[i][0]+'，'+arr[i]+'</li>';    
      //将结果添加到html中
      ul.innerHTML= str;
    }    
  }

})();

</script>
</body>
</html>
```
#### JS中的sort方法
sort() 方法用于对数组的元素进行排序。
```
arrayObject.sort(sortby)
```
##### 返回值

对数组的引用。请注意，数组在原数组上进行排序，不生成副本。
##### 说明
如果调用该方法时没有使用参数，将按字母顺序对数组中的元素进行排序，说得更精确点，是按照字符编码的顺序进行排序。要实现这一点，首先应把数组的元素都转换成字符串（如有必要），以便进行比较。

如果想按照其他标准进行排序，就需要提供比较函数，该函数要比较两个值，然后返回一个用于说明这两个值的相对顺序的数字。比较函数应该具有两个参数 a 和 b，其返回值如下：

* 若 a 小于 b，在排序后的数组中 a 应该出现在 b 之前，则返回一个小于 0 的值。
* 若 a 等于 b，则返回 0。
* 若 a 大于 b，则返回一个大于 0 的值。

如果不使用函数，则按照字母表的顺序排序
```
<script type="text/javascript">

var arr = new Array(6)
arr[0] = "10"
arr[1] = "5"
arr[2] = "40"
arr[3] = "25"
arr[4] = "1000"
arr[5] = "1"

document.write(arr + "<br />")//10,5,40,25,1000,1

document.write(arr.sort())//1,10,1000,25,40,5

</script>
```
如果需要对数字的大小排序就要创建一个函数

```
<script type="text/javascript">

function sortNumber(a,b)
{
return a - b
}

var arr = new Array(6)
arr[0] = "10"
arr[1] = "5"
arr[2] = "40"
arr[3] = "25"
arr[4] = "1000"
arr[5] = "1"

document.write(arr + "<br />")
document.write(arr.sort(sortNumber))
//10,5,40,25,1000,1
//1,5,10,25,40,1000

</script>
```
