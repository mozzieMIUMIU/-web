
##高德地图的一些笔记

#### 1.城市之间切换并获取citycode
高德在使用行政区划插件已经封装好开发者可能会需要用到一些城市数据信息。
![](https://raw.githubusercontent.com/mozzieMIUMIU/amap-web/master/img/msg.png)
百度在使用过程中，citycode似乎是地图上的某一个点，不是一个地区。
比如我输入的地址是四川省成都市高新区，返回是青羊区的城市编码。

#### 2.地图拖拽和平移
百度对于城市列表在pc端已经有封装好的组件。
组件的说明不多，但目前满足我的需求。
拖拽地图，城市name也会跟随变化。我可以拿着nama做一些别的事情。
高德对于pc端没有像 https://ditu.amap.com/  上面的城市列表组件。
所以写了一个十分简单的城市名列表。

#### 3.坐标点
点击当前坐标点添加状态，并展示当前点击对象的数据信息
在代码里可以自定义key值
![](https://raw.githubusercontent.com/mozzieMIUMIU/amap-web/master/img/marker.gif)
```
var icon = new AMap.Icon({
   image: '../ico-gray.png',
   size: new AMap.Size(48, 48)
});
marker = new AMap.Marker({
   icon: icon,
   position: provinces[i].center.split(','),
   testKB: provinces[i].kb,  //自定义
   map: map
});
//添加事件
 marker.on('click', function(e) {
   console.log(e.target.vh.contentDom)
   //当前信息
   console.log(e.target)
});
```
#### 4.地图缩放获取的行政区域（国，省，区）配合地图的缩放等级来定。

#### 5.其它
```
 //清除地图上所有覆盖物(polygons)
for (var i = 0, l = polygons.length; i < l; i++) {
    polygons[i].setMap(null);
}
 //清除地图上所有覆盖物(markers)
for (var i = 0, l = markers.length; i < l; i++) {
    markers[i].setMap(null);
}
 //清除地图上所有覆盖物
 map.clearMap();
 ```