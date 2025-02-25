# 稿件投诉

---

- [附件上传](#附件上传)
- [获取投诉类型](#获取投诉类型)
- [投诉稿件](#投诉稿件)

---

## 附件上传

> 附件上传与视频封面上传共用一个api。

## 获取投诉类型

> https://api.bilibili.com/x/web-interface/archive/appeal/tags

*请求类型：GET*

**json回复：**

| 参数名  | 类型          | 内容 | 备注    |
| ------- | ------------- | ---- | ------- |
| code    | num           |      | 成功为0 |
| message | str           |      | 成功为0 |
| ttl     | num           | 1    |         |
| data    | List\<object> |      |         |

`data`数组：

| 项   | 类型 | 内容           | 备注               |
| ---- | ---- | -------------- | ------------------ |
| 0    | obj  | 评论条目 1     |                    |
| n    | obj  | 评论条目 (n+1) | 按照指定的顺序排列 |
| ……   | obj  | ……             | ……                 |

`data`数组中的对象

| 项       | 类型                           | 内容             | 备注     |
| -------- | ------------------------------ | ---------------- | -------- |
| tid      | num                            | 类型tid          |          |
| business | num                            |                  | 意义不明 |
| weight   | num                            | 权重             |          |
| round    | num                            |                  | 意义不明 |
| state    | num                            |                  | 意义不明 |
| name     | str                            | 类型名称         |          |
| remark   | str                            | 类型备注         |          |
| ctime    | str                            |                  | 意义不明 |
| mtime    | str                            |                  | 意义不明 |
| controls | 拥有时：object<br>没有时：null | 详细信息填写提示 |          |

`data`数组中的对象中的`controls`对象：

| 项          | 类型 | 内容           | 备注     |
| ----------- | ---- | -------------- | -------- |
| tid         | num  | 同上           |          |
| bid         | num  |                | 意义不明 |
| name        | str  | 提示名称       |          |
| title       | str  | 提示标题       |          |
| component   | str  | 需要填入的类型 |          |
| placeholder | str  | 文本框占位符   |          |
| required    | num  | 是否为必填     |          |

**示例：**

```bash
curl --location --request GET 'https://api.bilibili.com/x/web-interface/archive/appeal/tags'
```

<details>
  <summary>查看响应示例</summary>
```json
{
    "code": 0,
    "message": "0",
    "ttl": 1,
    "data": [
        {
            "tid": 1,
            "business": 1,
            "weight": 1,
            "round": 2,
            "state": 1,
            "name": "有其他问题",
            "remark": "为帮助审核人员更快处理，请补充问题类型和出现位置等详细信息",
            "ctime": "2018-08-13T15:41:20+08:00",
            "mtime": "2018-08-13T15:41:20+08:00",
            "controls": null
        },
        {
            "tid": 9,
            "business": 1,
            "weight": 30,
            "round": 2,
            "state": 1,
            "name": "引战",
            "remark": "为帮助审核人员更快处理, 请补充引战的话题和出现位置",
            "ctime": "2018-08-13T15:41:20+08:00",
            "mtime": "2018-08-13T15:41:20+08:00",
            "controls": null
        },
        {
            "tid": 10,
            "business": 1,
            "weight": 20,
            "round": 2,
            "state": 1,
            "name": "不能参加充电",
            "remark": "为帮助审核人员更快处理, 请补充问题类型和出现位置等详细信息",
            "ctime": "2018-08-13T15:41:20+08:00",
            "mtime": "2018-08-23T11:35:28+08:00",
            "controls": null
        },
        {
            "tid": 52,
            "business": 1,
            "weight": 35,
            "round": 2,
            "state": 1,
            "name": "转载/自制类型错误",
            "remark": "为帮助审核人员更快处理, 请补充原创作品出处",
            "ctime": "2018-08-13T15:41:20+08:00",
            "mtime": "2018-08-13T15:41:20+08:00",
            "controls": [
                {
                    "tid": 52,
                    "bid": 1,
                    "name": "出处",
                    "title": "原创视频出处",
                    "component": "link",
                    "placeholder": "请填写链接",
                    "required": 1
                }
            ]
        },
        {
            "tid": 2,
            "business": 1,
            "weight": 100,
            "round": 1,
            "state": 1,
            "name": "违法违禁",
            "remark": "为帮助审核人员更快处理，补充违规内容出现位置",
            "ctime": "2018-08-13T15:41:20+08:00",
            "mtime": "2018-08-13T15:41:20+08:00",
            "controls": null
        },
        {
            "tid": 3,
            "business": 1,
            "weight": 90,
            "round": 1,
            "state": 1,
            "name": "色情",
            "remark": "为帮助审核人员更快处理，补充违规内容出现位置",
            "ctime": "2018-08-13T15:41:20+08:00",
            "mtime": "2018-08-13T15:41:20+08:00",
            "controls": null
        },
        {
            "tid": 4,
            "business": 1,
            "weight": 80,
            "round": 1,
            "state": 1,
            "name": "低俗",
            "remark": "为帮助审核人员更快处理，补充违规内容出现位置",
            "ctime": "2018-08-13T15:41:20+08:00",
            "mtime": "2018-08-13T15:41:20+08:00",
            "controls": null
        },
        {
            "tid": 5,
            "business": 1,
            "weight": 70,
            "round": 1,
            "state": 1,
            "name": "赌博诈骗",
            "remark": "为帮助审核人员更快处理，补充违规内容出现位置",
            "ctime": "2018-08-13T15:41:20+08:00",
            "mtime": "2018-08-13T15:41:20+08:00",
            "controls": null
        },
        {
            "tid": 6,
            "business": 1,
            "weight": 60,
            "round": 1,
            "state": 1,
            "name": "血腥暴力",
            "remark": "为帮助审核人员更快处理，补充违规内容出现位置",
            "ctime": "2018-08-13T15:41:20+08:00",
            "mtime": "2018-08-13T15:41:20+08:00",
            "controls": null
        },
        {
            "tid": 7,
            "business": 1,
            "weight": 50,
            "round": 1,
            "state": 1,
            "name": "人身攻击",
            "remark": "为帮助审核人员更快处理，补充违规内容出现位置",
            "ctime": "2018-08-13T15:41:20+08:00",
            "mtime": "2018-08-13T15:41:20+08:00",
            "controls": null
        },
        {
            "tid": 8,
            "business": 1,
            "weight": 40,
            "round": 1,
            "state": 1,
            "name": "与站内其他视频撞车",
            "remark": "为帮助审核人员更快处理, 请描述撞车信息",
            "ctime": "2018-08-13T15:41:20+08:00",
            "mtime": "2018-08-23T00:30:04+08:00",
            "controls": [
                {
                    "tid": 8,
                    "bid": 1,
                    "name": "撞车对象",
                    "title": "撞车对象",
                    "component": "input",
                    "placeholder": "BVID",
                    "required": 1
                }
            ]
        },
        {
            "tid": 10000,
            "business": 1,
            "weight": 10,
            "round": 1,
            "state": 1,
            "name": "青少年不良信息",
            "remark": "为帮助审核人员更快处理, 请补充违规内容出现位置",
            "ctime": "2018-08-13T15:41:20+08:00",
            "mtime": "2018-08-13T15:41:20+08:00",
            "controls": null
        },
        {
            "tid": 10013,
            "business": 1,
            "weight": 37,
            "round": 1,
            "state": 1,
            "name": "不良封面/标题",
            "remark": "为帮助审核人员更快处理, 请描述详细信息",
            "ctime": "2019-04-17T19:18:09+08:00",
            "mtime": "2019-04-17T20:42:25+08:00",
            "controls": null
        }
    ]
}
```
</details>

## 投诉稿件

> https://api.bilibili.com/x/web-interface/archive/appeal

*请求方式：POST*

认证方式：Cookie（SESSDATA)

**正文参数：**

| 参数名 | 类型 | 内容                     | 必要性 | 备注                     |
| ------ | ---- | ------------------------ | ------ | ------------------------ |
| csrf   | str  | csrf token(位于cookie)   | 必要   | 在url params中           |
| jsonp  | str  | jsonp                    | 必要?  | 意义不明，位于url params |
| aid    | num  | 稿件aid                  | 必要   | 位于request body         |
| tid    | num  | 投诉理由tid              | 必要   | 位于request body         |
| desc   | str  | 投诉理由详细描述         | 必要   | 位于request body         |
| attach | str  | 附件（多个附件用逗号隔开 | 非必要 | 位于request body         |

**json回复：**

| 参数名  | 类型 | 内容   | 备注    |
| ------- | ---- | ------ | ------- |
| code    | num  | 返回码 | 成功为0 |
| message | str  |        | 成功为0 |
| ttl     |      | 1      |         |

**示例：举报av号为61080066的视频，理由为人身攻击，描述为“xxxxx”，并附带了一个图片附件

```bash
curl --location --request POST 'https://api.bilibili.com/x/web-interface/archive/appeal?jsonp=jsonp&csrf=xxxx' \
--form 'aid="61080066"' \
--form 'tid="7"' \
--form 'desc="xxxxx"' \
--form 'attach="https://archive.biliimg.com/bfs/archive/xxxxx.png"'
```

<details>
  <summary>查看响应示例</summary>
```json
{
	"code":0,
	"message":"0",
	"ttl":1
}
```
</details>
