# CMS 接口文档
###  (目前没有测试数据 预计7月7号可以调用接口 查询到测试数据)
### 详细对象信息 可以查看 swagger 
# [swagger 点这里 (需要VPN才能访问)](https://pmall-dev.dominos.com.cn/dominos-cms-front/swagger-ui.html)

1. 通过code查询模板
>/template/getOneByCode/{code}

2. 通过group查询模板
>/template/getTemplateByGroup
```js
    //请求参数
    {
        "channel": 0, //渠道
        "cityCode": "string", //城市code
        "group": "string", //组的key (必传)
        "integral": 0, //积分
        "storeCode": "string", //门店code
        "userLv": 0, //用户等级
        "variables": [ //变量数组 (如果想通过变量来筛选数据 变量需要在后台管理页面创建)
            {
            "key": "string",
            "value": "string"
            }
        ]
    }
```

## 示例
```js
    //请求参数
    {
        "group": "slideshow", //组的key (必传)
    }
    //返回值
    {
        "code": "200", //成功
        "data": [ //通过组查询 返回的是数组
            {
                "code": "string",
                "html": "string", //html文件地址
                "ordBy": 0,
                "richText": { //富文本对象
                    "chText1": "string",
                    "chText2": "string",
                    "enText1": "string",
                    "enText2": "string",
                },
                "temAlert": { //弹窗对象
                    "but1Name": "string",
                    "but1Url": "string",
                    "but2Name": "string",
                    "but2Url": "string",
                    "butNum": 0,
                    "chHint": "string",
                    "enHint": "string",
                    "img": "string",
                    "type": 0,
                },
                "temButton": { //按钮对象
                    "button1BackgroundColor": "string",
                    "button1Color": "string",
                    "button1Icon": "string",
                    "button1Name": "string",
                    "button1Url": "string",
                    "button2BackgroundColor": "string",
                    "button2Color": "string",
                    "button2Icon": "string",
                    "button2Name": "string",
                    "button2Url": "string",
                },
                "temImg": { //图片对象
                    "cnImg": "string", //中文图片地址
                    "enImg": "string", //英文图片地址
                },
                "titleAndBackground": { //标题对象
                    "backgroundColor": "string",//背景色
                    "backgroundImg": "string",//背景图
                    "chTitle1": "string",//中文标题1
                    "chTitle2": "string",//中文标题2
                    "enTitle1": "string",//英文标题1
                    "enTitle2": "string",//英文标题2
                    "title1Color": "string",//标题1颜色
                    "title2Color": "string",//标题2颜色
                    "url": "string"//跳转链接
                }
            }
        ],
        "errMsg": "string"
    }
```




- 场景1 -->轮播图  
通过组查询 来得到轮播图组
```js
    //请求轮播图的时候  group 为 slideshow
    {
        "group": "slideshow", //组的key (必传)
    }
    //其他的参数 可以不传
```
> 一般来说 轮播图就是图片和一个跳转链接  
> 所以:  
>>对象中的temImg 属性中拿到图片URL 就行  
>>比如轮播图还需要跳转页面的 可以配置在TitleAndBackground 对象的url属性中    
___
返回值如下:
```js
    {
        "code": "200", //成功
        "data": [ //通过组查询 返回的是数组
            {
                "code": "string",
                "html": "string", //html文件地址
                "temImg": { //图片对象
                    "cnImg": "baidu.com", //中文图片地址
                    "enImg": "string", //英文图片地址
                },
                "titleAndBackground": { //标题对象
                    "backgroundColor": "string",//背景色
                    "backgroundImg": "string",//背景图
                    "chTitle1": "string",//中文标题1
                    "chTitle2": "string",//中文标题2
                    "enTitle1": "string",//英文标题1
                    "enTitle2": "string",//英文标题2
                    "title1Color": "string",//标题1颜色
                    "title2Color": "string",//标题2颜色
                    "url": "string"//跳转链接
                }
            }
        ],
        "errMsg": "string"
    }
```
- 场景2 -->Tab 列表  
```js
    //请求Tab列表的时候  group 为 tab
    {
        "group": "tab", //组的key (必传)
    }
    //其他的参数 可以不传
```
还是通过组查询 获得对象数组
> 一般来说 Tab列表 就是一个文字 加上跳转链接  
> 所以:
> >遍历数组 获取每个对象的titleAndBackground属性
> 拿到中文标题属性:chTitle1 一般情况下 1个标题就够了 怕有特殊情况 设计了2个  
> 跳转URL 还是从url属性中拿  如果还有颜色等其他需求的  可以自行搭配


## 总结:  前端开发人员 需要和配置人员商量好 把什么属性放在哪里