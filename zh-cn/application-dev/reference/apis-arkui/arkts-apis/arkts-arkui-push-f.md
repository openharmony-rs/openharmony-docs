# push

## push

```TypeScript
function push(options: RouterOptions): void
```

跳转到应用内的指定页面。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃，建议使用
> [pushUrl](arkts-arkui-router-c.md#pushurl-2)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** pushUrl(options:

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | RouterOptions | 是 | 跳转页面描述信息。 |

**示例：**

```TypeScript
class innerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class RouterParams {
  data1: string;
  data2: innerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new innerParams(tuple);
  }
}

router.push({
  url: 'pages/routerpage2',
  params: new RouterParams('message', [123, 456, 789])
});

```

