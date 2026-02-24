# geoNear

返回文档聚合阶段，按照距离指定点从最近到最远的顺序输出文档。
```
function geoNear(near: AggregateGeoNearParam): Aggregate;
```


## 请求参数 near

AggregateGeoNearParam 参数结构为：
| 属性 | 类型 | 默认值 | 必填 | 说明 |
| --- | --- | --- | --- | --- |
| near | GeoPoint | - | 是 | GeoJSON Point，用于判断距离的点。 |
| spherical | boolean | - | 否 | 确定 MongoDB 如何计算两点之间的距离：●当为 true，MongoDB 使用 $nearSphere 语义并使用球面几何来计算距离。●当为 false，MongoDB 使用 $near语义：2dsphere 索引使用球形几何形状，2d 索引使用平面几何形状。 |
| maxDistance | number | - | 否 | 距离中心点最大值。 |
| minDistance | number | - | 否 | 距离中心点最小值。 |
| query | Object | - | 否 | 将结果限制为与查询匹配的文档（语法同 where）。 |
| distanceMultiplier | number | - | 否 | 查询返回时在距离上乘以该数字。 |
| distanceField | string | - | 是 | 存放距离的输出字段名，可以用点表示法表示一个嵌套字段。 |
| includeLocs | string | - | 否 | 标识用于计算距离的位置的输出字段。当位置字段包含多个位置时，此选项有用。 |
| key | string | - | 否 | 指定计算距离时要使用的地理空间索引字段。 |


## 返回参数

Aggregate 聚合流水线构建对象。

## API 说明

●geoNear 必须为聚合管道的第一个阶段。●geoNear 必须有地理位置索引。如果集合上有多个地理空间索引，使用 keys参数指定在计算中使用哪个字段。如果只有一个地理空间索引，$geoNear隐式使用索引字段进行计算。

## 云函数示例

假设集合 places 有如下记录：
```JSON
{
name: "Central Park",
location: { type: "Point", coordinates: [ -73.97, 40.77 ] },
category: "Parks"
},
{
name: "Sara D. Roosevelt Park",
location: { type: "Point", coordinates: [ -73.9928, 40.7193 ] },
category: "Parks"
},
{
name: "Polo Grounds",
location: { type: "Point", coordinates: [ -73.9375, 40.8303 ] },
category: "Stadiums"
}
```
执行示例代码：
```JSON
const cloud = require('@alipay/faas-server-sdk');
exports.main = async (event, context) => {
// 初始化
cloud.init();
const db = cloud.database();
const $ = db.command.aggregate
db.collection('places').aggregate()
.geoNear({
distanceField: 'dist.calculated', // 输出的每个记录中 distance 即是与给定点的距离
spherical: true,
maxDistance: 2,
near: db.Geo.Point(-73.99279 , 40.719296),
query: {
category: 'Parks',
},
includeLocs: 'dist.location', // 若只有 location 一个是地理位置，则不需填
})
.end()
};
```
返回结果如下：
```
{
"_id" : 8,
"name" : "Sara D. Roosevelt Park",
"category" : "Parks",
"location" : {
"type" : "Point",
"coordinates" : [ -73.9928, 40.7193 ]
},
"dist" : {
"calculated" : 0.9539931676365992,
"location" : {
"type" : "Point",
"coordinates" : [ -73.9928, 40.7193 ]
}
}
}
```
​
