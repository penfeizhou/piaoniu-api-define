FORMAT: 1A
HOST: http://ipiaoniu.apiary.io

# 票牛Api

## 活动列表 [/v1/activities{?pageIndex,pageSize,keyword,regionId,categoryId,latitude,longitude,startTime,endTime}]

### 获取活动列表 [GET]

+ Parameters
    + pageIndex(number) - 第几页
    + pageSize(number) - 每页多少
    + keyword(string, optional) - 关键词
    + startTime(string, optional) - 开始时间 2015-01-01
    + endTime(string, optional) - 结束时间 2015-01-30
    + regionId(number, optional) - 地区Id
    + categoryId(number, optional) - 类型Id
    + latitude(string, optional) - 纬度
    + longitude(string, optional) - 经度

+ Response 200 (application/json)

            {
              "data": [
                {
                  "updateTime": 1439853517000,
                  "events": [
                    {
                      "end": 1443632400000,
                      "start": 1443628800000,
                      "activityEventGroupId": 1,
                      "updateTime": 1439856046000,
                      "addTime": 1439856046000,
                      "id": 1
                    }
                  ],
                  "ticketCategories": [{
                    "id": 1,
                    "originPrice": 200
                  },{
                    "id": 2,
                    "originPrice": 100
                  }],
                  "categoryId": 1,
                  "poster": "http://www.gravatar.com/avatar/72ec343bf968d8fea338b9f57b4caab9?s=24&d=identicon",
                  "id": 1,
                  "highPrice": 3000.0,
                  "name": "abosdfe",
                  "lowPrice": 10.0,
                  "actorId": 0,
                  "addTime": 1439853517000,
                  "venueName": "test",
                  "areaImage": "..."
                }
              ],
              "pageSize": 10,
              "pageIndex": 1,
              "totalNum": 1
            }


## 活动详情 [/v1/activities/{id}]

### 查询活动详情 [GET]

+ Parameters
    + id - 活动Id

+ Response 200 (appliation/json)

        {
          "addTime": 1439853517000,
          "venue": {
            "id": 1,
            "addTime": 1441590509000,
            "updateTime": 1441590509000,
            "name": "test",
            "address": "test",
            "avatar": "http://www.gravatar.com/avatar/72ec343bf968d8fea338b9f57b4caab9?s=24&d=identicon",
            "cityId": 1,
            "regionId": 1,
            "latitude": 11,
            "longitude": 11,
            "phones": "123,123"
          },
          "actorId": 0,
          "rank": 10,
          "name": "abosdfe",
          "id": 1,
          "activityDetails": [{
            "id": 1,
            "addTime": 1439855876000,
            "updateTime": 1439855876000,
            "activityId": 1,
            "type": 2,
            "detailDesc": {
              "title": "",
              "list": [
                "123",
                "456"
              ]
            }
          }],
          "poster": "http://www.gravatar.com/avatar/72ec343bf968d8fea338b9f57b4caab9?s=24&d=identicon",
          "areaImage": "<座位图>",
          "categoryId": 1,
          "events": [{
            "id": 1,
            "addTime": 1439856046000,
            "updateTime": 1439856046000,
            "activityEventGroupId": 1,
            "start": 1443628800000,
            "end": 1443632400000
          }],
          "updateTime": 1439853517000
        }

## 场馆列表 [/v1/venues{?pageIndex,pageSize,keyword,regionId,categoryId,latitude,longitude}]

### 获取场馆列表 [GET]

+ Parameters
    + pageIndex(number) - 第几页
    + pageSize(number) - 每页多少
    + keyword(string, optional) - 关键词
    + regionId(string, optional) - 地区Id
    + categoryId(string, optional) - 类型Id
    + latitude(string, optional) - 纬度
    + longitude(string, optional) - 经度

+ Response 200 (application/json)

        {
          "totalNum": 466,
          "pageIndex": 1,
          "pageSize": 10,
          "data": [{
            "address": "test",
            "latitude": 11,
            "phones": "123,123",
            "avatar": "http://www.gravatar.com/avatar/72ec343bf968d8fea338b9f57b4caab9?s=24&d=identicon",
            "cityId": 1,
            "addTime": 1441590509000,
            "regionId": 1,
            "name": "test",
            "activitiesNum": 1,
            "id": 1,
            "longitude": 11,
            "tags": ["hasTicket"],
            "updateTime": 1441590509000
          }, {
            "address": "场馆地址:上海市黄浦区延安东路523号[查看地图]",
            "latitude": 0,
            "phones": "placeholder",
            "avatar": "placeholder",
            "cityId": 1,
            "addTime": 1441590509000,
            "regionId": 0,
            "name": "上海音乐厅介绍",
            "activitiesNum": 0,
            "id": 2,
            "longitude": 0,
            "updateTime": 1441590509000
          }]
        }

## 收件地址管理 [/v1/myaddress]

### 获取我的收件地址 [GET]


+ Response 200 (application/json)

        {
            latestId: 1,
            receiverName: "", // 可空
            receiverPhone: "", // 可空
            addresses: [{
                "id": 1,
                "name": "xxx",
                "phone": "137192312",
                "district": "上海市宝山区",
                "address":"xxxx"
            },{
                "id": 2,
                "name": "yyyxxx",
                "phone": "137192312",
                "district": "上海市宝山区",
                "address":"xxxx"
            }]
        }

### 添加我的收件地址 [POST /v1/myaddress?name,phone,district,address]

+ Parameter

    + phone(string) - 手机号
    + name(string) - 收件人
    + district(string) - 省市区
    + address(string) - 地址

+ Response 200

        {
            "success": true,
            "data": 3
        }

### 删除我的收件地址 [DELETE /v1/myadress/{id}]


+ Response 200

        {
            "success": true
        }

## 订单 [/v1/order]

### 提交订单 [POST /v1/order?eventId,ticketGroupId,receiverName,receiverType,receiverMobile,receiverAddressId,count,paymentType,areaId,receiveType,totalAmount,paymentAmount]

+ Parameter

    + eventId
    + ticketGroupId
    + areaId
    + totalAmount(number) - 应付金额
    + paymentAmount(number) - 实付金额
    + receiveType(number) - 收件方式 1:快递寄送 2:现场取票
    + receiverName(string, optional) - 收件人
    + receiverMobile(string, optional) - 收件人手机号
    + receiverAddressId(number, optional) - 收件人地址
    + count - 张数
    + paymentType - 支付渠道 1:支付宝

+ Response 200 (application/json)

        {
            "orderId": 1,
            "paymentType": 1,
            "paymentParameters": "xxxxxx"
        }

### 查询支付结果 [GET /v1/order/status?orderId]


+ Parameter

    + orderId


+ Response 200 (application/json)

        {
            "status": "pending|success|fail"
        }

## 票源 [/v1/tickets]

### 获取票源信息 [GET /v1/tickets/?eventId,ticketCategoryId,pageIndex,pageSize]

用户端
说明：用于在选择票的界面根据票挡获取票源信息
由于该界面没有直接入口，其中的活动信息部分已从上一个界面获得（见“活动详情”接口）

同时根据活动Id（是否就是eventGroupId），由“演出场次信息列表”接口
获取所有场次以及相关票档。

选择一个票档，则根据该接口获取所有票源。

+ Parameters
    + eventId(number) - 场次
    + ticketCategoryId(number) - 票档Id
    + pageIndex(number) - 页码
    + pageSize(number) - 每页条数

+ Response 200 (application/json)

        {
            "pageSize": 10, // 以卖家为单位
            "pageIndex": 1,
            "totalNum": 20,
            "originPrice": 1800,
            "data": [{
                "ticketGroupId":1,
                "name": "卖家甲",
                "recommended": true,
                "salePrice": 2000,
                "desc": "买到赚到不加价",
                "tickets": [{
                // SalerTicketArea
                    "areaId": 1,
                    "areaName":"A区",
                    "saling": 10,
                }, {
                    "areaId": 2,
                    "areaName":"B区",
                    "saling": 10
                }]
            }, {
                "ticketGroupId":2,
                "name": "卖家乙"
                "recommended": true,
                "salePrice": 2000,
                "desc": "买到赚到不加价",
                "tickets": [{
                    "areaId": 1,
                    "areaName":"A区",
                    "saling": 10
                }, {
                    "areaId": 2,
                    "areaName":"B区",
                    "saling": 10
                }]
            }]
        }]

### 查询在售信息 [GET /v1/salerTickets/?ticketCategoryId,eventId]

+ Parameters
    + eventId
    + ticketCategoryId

+ Response 200 (application/json)

    + Body

            {
                "areas" : [{
                    "areaId": 1,
                    "areaName": "A区"
                },{
                    "areaId": 2,
                    "areaName": "B区"
                }],
                "salingInfo": {
                    "salePrice": 200,
                    "desc": "xxxx",
                    "tickets":[{
                        "areaId": 1,
                        "sold": 7,
                        "saling": 8
                    },{
                        "areaId": 2,
                        "sold": 7,
                        "saling": 8
                    }]
                }
            }


### 票源信息 [POST /v1/salerTickets]

+ Request (application/json)

    + Body

            {
                "eventId": 12,
                "ticketCategoryId": 12,
                "salePrice": 2000,
                "desc": "买到赚到",
                "tickets": [{
                    "areaId": 1, // 这里取id还是name确认下
                    "saling": 10
                }]
            }

+ Response 200 (application/json)

            {
                "success": true // 返回需要啥信息还没想好
            }

### 更改票源价格 [PUT /v1/salerTickets/price]

+ Request (application/json)

    + Body

            {
                "eventId": 12,
                "ticketCategoryId": 12,
                "price": 2000
            }

+ Response 200 (application/json)

            {
                "success": true
            }


### 更改票源价格 [PUT /v1/salerTickets/desc]

+ Request (application/json)

    + Body

            {
                "eventId": 12,
                "ticketCategoryId": 12,
                "desc": 2000
            }

+ Response 200 (application/json)

            {
                "success": true
            }


### 更改票档对应区域在售数量 [PUT /v1/salerTickets/storage]

delta为加减数量，前端填写的时候填的是票库存，发请求的时候根据现在的数量去计算得到delta

+ Request (application/json)

    + Body

            {
                "eventId": 12,
                "areaId": 12,
                "ticketCategoryId": 12,
                "delta": 5
            }

+ Response 200 (application/json)

            {
                "success": true
            }


## 演出热门搜索 [/v1/activities/hottest]

### 获取热门搜索 [GET]

+ Response 200 (application/json)

        [{
            "id": 1,
            "keyword": "第十一届爵士音乐节"
        },{
            "id": 2,
            "keyword": "第十一届爵士音乐节2"
        },{
            "id": 3,
            "keyword": "第十一届爵士音乐节3"
        }]


## 场馆详情 [/v1/venues/{id}]

### 获取场馆详情 [GET]

+ Parameters
    + id - 场馆id

+ Response 200 (application/json)

        {
          "address": "test",
          "latitude": 11,
          "phones": "123,123",
          "avatar": "http://www.gravatar.com/avatar/72ec343bf968d8fea338b9f57b4caab9?s=24&d=identicon",
          "cityId": 1,
          "addTime": 1441590509000,
          "regionId": 1,
          "activities": [{
            "id": 1,
            "addTime": 1439853517000,
            "updateTime": 1439853517000,
            "actorId": 0,
            "categoryId": 1,
            "name": "abosdfe",
            "poster": "http://www.gravatar.com/avatar/72ec343bf968d8fea338b9f57b4caab9?s=24&d=identicon"
          }],
          "name": "test",
          "id": 1,
          "class": "com.piaoniu.biz.entity.Venue",
          "longitude": 11,
          "updateTime": 1441590509000
        }

## 手机验证码 [/v1/user/sendCode{?ua}]

### 发送手机验证码 [POST]

+ Parameters
    + ua - 账号（手机号）

+ Response 200 (application/json)

        {}

## 注册 [/v1/user/reg]

### 注册用户 [POST]
+ Attributes
    + ua - 账号（手机号）
    + pw - 密码
    + code - 验证码
    + ct - 注册渠道 (ios:10, android: 11)

+ Response 200 (application/json)

        {
          "user": {
              "userId": 6,
              "mobileNo": "13800138050",
              "userName": "pn9138050",
              "status": 0,
              "addTime": 1442074050000,
              "updateTime": 1442074050000
          }
        }


## 登录 [/v1/user/login]

### 登录用户 [POST]

+ Attributes (object)
    + ua - 账号（手机号）
    + pw - 密码
    + ct - 登录渠道

+ Request

    + Body

            ua=123&password=qwe&ct=10

+ Response 200 (application/json)

    + Headers

            pn: D937F781D33BBAB46887494EB95DAD5782AF4936842561DD1BE3EAAE7544FBA6

    + Body

            {
                "user": {
                    "userId": 1,
                    "mobileNo": "13800138030",
                    "userName": "南玻玩",
                    "status": 0,
                    "addTime": 14419656000000,
                    "updateTime": 1441965600000
                }
            }