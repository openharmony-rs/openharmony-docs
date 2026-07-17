# replace

## 导入模块

```TypeScript
import { router } from '@kit.ArkUI';
```

## replace

```TypeScript
function replace(options: RouterOptions): void
```

用应用内的某个页面替换当前页面，并销毁被替换的页面。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [replaceUrl](arkts-arkui-arkui-uicontext-router-c.md#replaceurl-2)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** replaceUrl(options:

<!--Device-router-function replace(options: RouterOptions): void--><!--Device-router-function replace(options: RouterOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RouterOptions](arkts-arkui-router-routeroptions-i.md) | 是 | 替换页面描述信息。 |

**示例：**

```TypeScript
import { router } from '@kit.ArkUI';

class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replace({
  url: 'pages/detail',
  params: new RouterParams('message')
});

```

