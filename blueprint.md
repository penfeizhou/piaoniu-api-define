FORMAT: 1A
HOST: http://api.ipiaoniu.com

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
          "totalNum": 1,
          "data": [{
            "createdAt": 1439853517000,
            "actorId": 0,
            "lowPrice": 1,
            "name": "abosdfe",
            "highPrice": 12,
            "rank": 10,
            "id": 1,
            "activityDetails": [{
              "id": 1,
              "createdAt": 1439855876000,
              "updatedAt": 1439855876000,
              "activityId": 1,
              "type": 2,
              "detailDesc": "todo"
            }],
            "poster": "http://www.gravatar.com/avatar/72ec343bf968d8fea338b9f57b4caab9?s=24&d=identicon",
            "class": "com.piaoniu.biz.entity.Activity",
            "categoryId": 1,
            "updatedAt": 1439853517000
          }]
        }

## 活动详情 [/v1/activities/{id}]

### 查询活动详情 [GET]

+ Parameters
    + id - 活动Id

+ Response 200 (appliation/json)

        {
          "createdAt": 1439853517000,
          "venue": {
            "id": 1,
            "createdAt": 1441590509000,
            "updatedAt": 1441590509000,
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
            "createdAt": 1439855876000,
            "updatedAt": 1439855876000,
            "activityId": 1,
            "type": 2,
            "detailDesc": {
              "title": "",
              "list": [
                "123",
                "456"
              ]
            }
          },{
            "id": 3,
            "createdAt": 1439855876000,
            "updatedAt": 1439855876000,
            "activityId": 1,
            "type": 1,
            "detailDesc": {
              "title": "演出详情",
              "content": [{
                text: "金曲创作..."
              },{
                image: "http://post.url"
              }]
            }
          }],
          "poster": "http://www.gravatar.com/avatar/72ec343bf968d8fea338b9f57b4caab9?s=24&d=identicon",
          "categoryId": 1,
          "events": [{
            "id": 1,
            "createdAt": 1439856046000,
            "updatedAt": 1439856046000,
            "activityGroupId": 1,
            "start": 1443628800000,
            "end": 1443632400000
          }],
          "updatedAt": 1439853517000
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
            "createdAt": 1441590509000,
            "regionId": 1,
            "name": "test",
            "activitiesNum": 1,
            "id": 1,
            "longitude": 11,
            "tags": ["hasTicket"],
            "updatedAt": 1441590509000
          }, {
            "address": "场馆地址:上海市黄浦区延安东路523号[查看地图]",
            "latitude": 0,
            "phones": "placeholder",
            "avatar": "placeholder",
            "cityId": 1,
            "createdAt": 1441590509000,
            "regionId": 0,
            "name": "上海音乐厅介绍",
            "activitiesNum": 0,
            "id": 2,
            "longitude": 0,
            "updatedAt": 1441590509000
          }]
        }

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
          "createdAt": 1441590509000,
          "regionId": 1,
          "activities": [{
            "id": 1,
            "createdAt": 1439853517000,
            "updatedAt": 1439853517000,
            "actorId": 0,
            "categoryId": 1,
            "name": "abosdfe",
            "poster": "http://www.gravatar.com/avatar/72ec343bf968d8fea338b9f57b4caab9?s=24&d=identicon"
          }],
          "name": "test",
          "id": 1,
          "class": "com.piaoniu.biz.entity.Venue",
          "longitude": 11,
          "updatedAt": 1441590509000
        }

## 手机验证码 [/v1/user/sendCode{?ua}]

### 发送手机验证码 [POST]

+ Parameters
    + ua - 账号（手机号）

+ Response 200 (application/json)

        {}

## 注册 [/v1/user/reg{?ua,pw,code}]

### 注册用户 [POST]
+ Parameters
    + ua - 账号（手机号）
    + pw - 密码
    + code - 验证码

+ Response 200 (application/json)

        {
          "user": {
              "userId": 6,
              "mobileNo": "13800138050",
              "userName": "pn9138050",
              "status": 0,
              "addTime": 1442074050000,
              "updateTime": 1442074050000
          },
          "token": "D937F781D33BBAB46887494EB95DAD5782AF4936842561DD1BE3EAAE7544FBA6"
        }


## 登录 [/v1/user/login{?ua,pw,lt}]

### 登录用户 [POST]

+ Parameters
    + ua - 账号（手机号）
    + pw - 密码
    + lt - 登录类型 （注册:00 web:10 手机:20）

+ Response 200 (application/json)

        {
            "user": {
                "userId": 1,
                "mobileNo": "13800138030",
                "userName": "南玻玩",
                "status": 0,
                "addTime": 1441965600000,
                "updateTime": 1441965600000
            },
            "token": "4A77AFB4A2EC1CD390F23A7C628269351F7645475E4D3BFA9B7E323401E4EA7A"
        }
