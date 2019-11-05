# timetable
时间表

![](https://cdn.nlark.com/yuque/0/2019/jpeg/378417/1572934532105-assets/web-upload/be920b91-8a3c-479c-89ed-d2901b3f21b5.jpeg)

## 由来
dhj同学抛来的一个需求，当时比较着急，接着他的代码写了一个版本。后面按照自己的思路进行重写。

## 难点
当时写的时候被dhj的逻辑给绕进去了，写了好一会。
后来按照自己的思路写，其实没什么难点，只是想吐槽这个接口返回的数据格式，还挺恶心的--!

```javascript
[
  {
    MONDAY: "",
    SUNDAY: "",
    WEDNESDAY: "",
    SDMC: "14:00-15:00",
    THURSDAY: "",
    SATURDAY: "",
    TUESDAY: "仙林校区",
    FRIDAY: ""
  },
  {
    MONDAY: "",
    SUNDAY: "",
    WEDNESDAY: "",
    SDMC: "15:30-16:30",
    THURSDAY: "江宁校区",
    SATURDAY: "",
    TUESDAY: "",
    FRIDAY: ""
  },
  {
    MONDAY: "",
    SUNDAY: "",
    WEDNESDAY: "嘉定校区",
    SDMC: "10:00-11:00",
    THURSDAY: "",
    SATURDAY: "",
    TUESDAY: "",
    FRIDAY: "四平校区"
  },
  {
    MONDAY: "",
    SUNDAY: "",
    WEDNESDAY: "",
    SDMC: "08:30-09:30",
    THURSDAY: "浦口校区",
    SATURDAY: "",
    TUESDAY: "",
    FRIDAY: ""
  }
]
```
## 吐槽
1、其实数据拿到前端处理无所谓，但是至少把`礼拜`顺序给排好吧，这应该是后端同学举手之劳的事情，像这样：
```javascript
[{
  MONDAY: "",
  TUESDAY: "",
  WEDNESDAY: "",
  THURSDAY: "浦口校区",
  FRIDAY: "",
  SATURDAY: "",
  SUNDAY: "",
  SDMC: "08:30-09:30"
}]
```
2、如果是这样的话（横向），那渲染就更方便了：
```javascript
[{
  week:"周一",
  campus:["","", "",""] // 按时间排序
},{
  week:"周二",
  campus:["","", "仙林校区",""]
},{
  week:"周三",
  campus:["","嘉定校区", "",""]
},{
  week:"周四",
  campus:["浦口校区","", "","江宁校区"]
},{
  week:"周五",
  campus:["","四平校区", "",""]
},{
  week:"周六",
  campus:["","", "",""]
},{
  week:"周日",
  campus:["","", "",""]
}]
```
3、或者是这样（纵向）：
```javascript
[{
  time:"08:30-09:30",
  campus:["","", "","浦口校区","","",""] // 按礼拜排序
},{
  time:"10:00-11:00",
  campus:["","", "嘉定校区","","四平校区","",""]
},{
  time:"14:00-15:00",
  campus:["","仙林校区", "","","","",""]
},{
  time:"15:30-16:30",
  campus:["","", "","江宁校区","","",""]
}]
```
## 总结
如果是我们公司的话，我肯定会去找后端同学，至少按照第一种方法整理下数据，举手之劳，前端就免得再处理了。
如果后端同学愿意第2、3种方法处理的话，那就更舒服了。
