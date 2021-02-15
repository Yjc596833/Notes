<!--
 * @Author: your name
 * @Date: 2021-01-14 15:12:50
 * @LastEditTime: 2021-01-14 15:13:28
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \Notes\JQ\base.md
-->
$jObject 永远不会为空,$ 方法查找对象，始终都会返回一个jQuery 对象的

解决办法：我们就要把jQuery对象转换成js对象
var dom = $jObect[0]; alert(dom);
if($jObect.length<=0) {alert("该对象为空");}