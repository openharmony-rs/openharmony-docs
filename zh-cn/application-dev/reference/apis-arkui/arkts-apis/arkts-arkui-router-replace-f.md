# replace

## replace

```TypeScript
function replace(options: RouterOptions): void
```

用应用内的某个页面替换当前页面，并销毁被替换的页面。不支持设置页面转场动效，如需设置，推荐使用\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用 > [replaceUrl]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [@ohos.arkui.UIContext:Router#replaceUrl](arkts-arkui-arkui-uicontext-router-c.md#replaceurl)(options:

<!--Device-router-function replace(options: RouterOptions): void--><!--Device-router-function replace(options: RouterOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 替换页面描述信息。 |

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

