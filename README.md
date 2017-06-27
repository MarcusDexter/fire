#fire API
##接口地址
http://[host]/api
##0. 登录  
###POST
```json
{
    "action"    :   0,
    "username"  :   "",
    "password"  :   ""
}
```
###返回
```json
{
    "token"           :   "0123456789abcdef",
    "departmentID"    :   0,
    "departmentName"  :   "机构名称",
    "name"            :   "张三",
    "rank"            :   0
}
```
注：rank的值 1.无权限 2.仅添加队站权限 3.仅添加队站权限 4.添加水源和队站权限
##1. 修改密码
###POST
```json
{
    "action"    :   1,
    "token"     :   "0123456789abcdef",
    "password"  :   "87654321"
}
```
###返回
```json
{
    "status"  :   "1",
    "token"   :   "0123456789abcdef"
}
```
##2. 更新位置信息
###GET
````json
{
    "action"  :   2,
    "token"   :   "0123456789abcdef",
    "time"    :   "上次更新的时间|long|1498406400"
}
````
###返回
```json
{
    "status": 1,
    "waterData": [
        {
            "waterID"     :     "水源ID|long",
            "createTime"  :     "创建时间|long|1498406400",
            "updateTime"  :     "更新时间|long|1498406400",
            "type"        :     "水源类型|int",
            "waterName"   :     "水源名称|string",
            "lat"         :     "经度|double",
            "lon"         :     "纬度|double",
            "alt"         :     "海拔|double",
            "isUse"       :     "是否可用"
        },
        {
            "...":"..."
        }
    ] ,
    "houseData": [
        {
            "houseID"     :   "队站ID|int",
            "createTime"  :   "创建时间|long|1498406400",
            "updateTime"  :   "更新时间|long|1498406400",
            "type"        :   "队站类型|int",
            "houseName"   :   "队站名称|string",
            "lat"         :   "经度|double",
            "lon"         :   "纬度|double",
            "alt"         :   "海拔|double"
        },
        {
            "..."   :   "..."
        }
    ]
}

```
##3. 查看水源
###GET
```json
{
    "action"  :   3,
    "token"   :   "0123456789abcdef",
    "waterID" :   0
}
```
###返回
```json
{
    "status":1,
    "data"    :   {
        "waterName"       :   "水源名称",
        "departmentID"    :   0,
        "departmentName"  :   "机构名称",
        "remark"          :   "备注",
        "damageLevel"     :   0,
        "damageType"      :   "损坏种类",
        "isUse"           :   1,
        "pressure"        :   "水压|double",
        "pipeDiameter"    :   "管网直径|double",
        "pipeForm"        :   "管网形状|int",
        "placeForm"       :   "放置形式|int",
        "takeWaterForm"   :   "取水形式|int",
        "supplyUnit"      :   "供水单位",
        "interfaceForm"   :   "接口形式",
        "volume"          :   "容量|double",
        "highDifference"  :   "取水口距水面高差|double",
        "packingCount"    :   "停车数量|int",
        "lowWater"        :   "有无枯水期",
        "seasonVary"      :   "四季变化"
    }
}
```
##4. 查看水源维护记录
###GET
```json
{
    "action"    :   4,
    "token"     :   "0123456789",
    "waterID"   :   0,
    "index"     :   0
}
```
###返回
```json
{
    "status"  :   1,
    "data"    :   [
        {
            "checkLogID"    :   0,
            "checkTime"     :   14900000000,
            "remark"        :   ""
        },
        {
            "..."   :   "..."
        }
    ]
}
```
##5. 查看队站
###GET
```json
{
    "action"    :   5,
    "token"     :   "0123456789abcdef",
    "houseID"   :   0
}
```
###返回
```json
{
    "status"          :   1,
    "houseType"       :   1,
    "houseName"       :   "",
    "departmentID"    :   0,
    "departmentName"  :   "",
    "remark"          :   "",
    "trunkCount"      :   1,
    "staffCount"      :   1,
    "address"         :   ""
}
```
##6. 添加水源
###POST
```json
{
    "action"    :   6,
    "token"     :   "0123456789abcdef",
    "waterName" :   "水源名称",
    "lat"       :   "经度|double",
    "lon"       :   "纬度|double",
    "alt"       :   "海拔|double",
    "isUse"     :   1,
    "remark"    :   ""
}
```
###返回
```json
{
    "status"    :   1,
    "massage"   :   "写入成功"
}
```
##7. 添加维护记录
###POST
```json
{
    "action"      :   7,
    "token"       :   "0123456789abcdef",
    "remark"      :   "",
    "waterID"     :   0
}
```
###返回
```json
{
    "status"    :   1,
    "massage"   :   "写入成功"
}
```
##8. 添加队站
###POST
```json
{
    "action"      :   8,
    "token"       :   "0123456789abcdef",
    "houseName"   :   "队站名称",
    "lat"         :   "经度|double",
    "lon"         :   "纬度|double",
    "alt"         :   "海拔|double",
    "remark"      :   "",
    "houseID"     :   0
}
```
###返回
```json
{
    "status"    :   1,
    "massage"   :   "写入成功"
}
```
##9. 获取图片
###GET
```json
{
    "action"    :   9,
    "token"     :   "0123456789abcdef",
    "type"      :   "数字0-4",
    "ID"        :   "水源或队站图片ID"
}
```
###返回
图片文件
