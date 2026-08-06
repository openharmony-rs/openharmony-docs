# matchMediaSync

## matchMediaSync

```TypeScript
function matchMediaSync(condition: string): MediaQueryListener
```

设置媒体查询的查询条件，并返回对应的监听句柄。 > **说明：** > > -matchMediaSync需先通过[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_方法获取 > [MediaQuery]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_对象，然后通过该对象进行调用。 > > - 从API version 10开始，可以通过使用[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_方法获取当前UI上下文关联的 > [MediaQuery]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_对象。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 18

**替代接口：** ohos.arkui.UIContext.MediaQuery#matchMediaSync

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-mediaquery-function matchMediaSync(condition: string): MediaQueryListener--><!--Device-mediaquery-function matchMediaSync(condition: string): MediaQueryListener-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | string | 是 | 媒体事件的匹配条件，具体可参考\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 媒体事件监听句柄，用于注册和注销监听回调。 |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { mediaquery } from '@kit.ArkUI';

let listener: mediaquery.MediaQueryListener = mediaquery.matchMediaSync('(orientation: landscape)'); // 监听横屏事件
```

ArkTS-Sta示例：

```TypeScript
import mediaquery from '@ohos.mediaquery';

let listener: mediaquery.MediaQueryListener = mediaquery.matchMediaSync('(orientation: landscape)'); // 监听横屏事件
```

