# FetchResponse

**表2** responseType与success中data关系  
| responseType | data | 说明 | | -------- | -------- | -------- | | 无 | string | 服务器返回的header中的type如果是text/\*或application/json、application/javascript、application/xml，值为文本内容。 | | text | string | 返回文本内容。 | | json | Object | 返回json格式的对象。 |

**起始版本：** 3

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
```

## code

```TypeScript
code: number
```

表示服务器的状态code。

**类型：** number

**起始版本：** 3

**系统能力：** SystemCapability.Communication.NetStack

## data

```TypeScript
data: string | object
```

返回数据类型由responseType确定，详见表 responseType与success中data关系。

**类型：** string \| object

**起始版本：** 3

**系统能力：** SystemCapability.Communication.NetStack

## headers

```TypeScript
headers: Object
```

表示服务器response的所有header。

**类型：** Object

**起始版本：** 3

**系统能力：** SystemCapability.Communication.NetStack

**示例**

ArkTS示例：

```TypeScript
fetch.fetch({
  url: 'test_url',
  success: (response) => {
    console.info('fetch success');
    console.info(JSON.stringify(response));
  },
  fail: () => {
    console.error('fetch failed');
  }
});
```

JS示例：

```TypeScript
<!-- index.hml -->
<div class="container">
    <text class="title">测试网络连接</text>
    <input type="button" value="点击测试" style="width: 240px; height: 50px;margin: 5px;" onclick="usingFetch"></input>
    <text class="title" style="color: {{fontColor}};">{{result}}</text>
</div>
```

```TypeScript
/* index.css */
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}
.title {
  font-size: 30px;
  text-align: center;
  width: 200px;
  height: 100px;
}
.button {
  font-size: 30px;
  text-align: center;
  width: 200px;
  height: 100px;
}
```

```TypeScript
// index.js
import fetch from '@system.fetch';

export default {
    data: {
        fontColor: '#FFF',
        result: '',
    },
    usingFetch: function() {
        const that = this;
        fetch.fetch({
            url: 'test_url',
            success: function(response) {
                that.fontColor = '#00FF00';
                that.result = 'SUCCESS';
                console.info('fetch success');
                console.info(JSON.stringify(response));
            },
            fail: function() {
                that.fontColor = '#FF0000';
                that.result = 'FAILED';
                console.error('fetch failed');
            }
        });
    }
};
```

说明：默认支持https，如果要支持http，需要在config.json里增加network标签，属性标识 "cleartextTraffic":  true。

```TypeScript
{
  "deviceConfig": {
    "default": {
      "network": {
        "cleartextTraffic": true
      }
      // 用户的其它配置信息
      // ...
    }
  }
  // 用户的其它配置信息
  // ...
}
```
