# getStateByUrl

## getStateByUrl

```TypeScript
function getStateByUrl(url: string): Array<RouterState>
```

通过url获取对应页面的状态信息。 > **说明：** > > - 从API version 12开始支持，从API version 18开始废弃，建议使用[getStateByUrl]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_替 > 代。getStateByUrl需先通过[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_获取 > [Router]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_实例，然后通过该实例进行调用。 > > - 从API version 12开始，可以通过使用[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_方法获取当前UI上下文关联的 > [Router]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_对象。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** 18

**替代接口：** [@ohos.arkui.UIContext:Router#getStateByUrl](arkts-arkui-arkui-uicontext-router-c.md#getstatebyurl)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-router-function getStateByUrl(url: string): Array<RouterState>--><!--Device-router-function getStateByUrl(url: string): Array<RouterState>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 表示要获取对应页面信息的url。url格式为页面绝对路径，由配置文件中pages列表提供，例如：pages/index/index。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;RouterState&gt; | 匹配指定url的页面状态信息数组，每个元素包含页面索引、名称、路径和参数。 |

**示例：**

```TypeScript
import { router } from '@kit.ArkUI';

let options: Array<router.RouterState> = router.getStateByUrl('pages/index');
for (let i: number = 0; i < options.length; i++) {
  console.info('index = ' + options[i].index);
  console.info('name = ' + options[i].name);
  console.info('path = ' + options[i].path);
  console.info('params = ' + options[i].params);
}
```

