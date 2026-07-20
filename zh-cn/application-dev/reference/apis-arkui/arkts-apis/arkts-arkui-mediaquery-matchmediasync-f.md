# matchMediaSync

## 导入模块

```TypeScript
import { mediaquery } from '@kit.ArkUI';
```

<a id="matchmediasync"></a>
## matchMediaSync

```TypeScript
function matchMediaSync(condition: string): MediaQueryListener
```

设置媒体查询的查询条件，并返回对应的监听句柄。

> **说明：**  
>  
> -matchMediaSync需先通过[UIContext](arkts-arkui-uicontext.md)中的  
> [getMediaQuery](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getmediaquery)方法获取  
> [MediaQuery](arkts-arkui-uicontext.md)对象，然后通过该对象进行调用。  
>  
> - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getMediaQuery](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getmediaquery)方法获取当前UI上下文关联的  
> [MediaQuery](arkts-arkui-uicontext.md)对象。

**起始版本：** 7

**废弃版本：** 18

**替代接口：** matchMediaSync

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-mediaquery-function matchMediaSync(condition: string): MediaQueryListener--><!--Device-mediaquery-function matchMediaSync(condition: string): MediaQueryListener-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | string | 是 | 媒体事件的匹配条件，具体可参考[媒体查询语法规则](docroot://ui/arkts-layout-development-media-query.md#语法规则)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaQueryListener](arkts-arkui-mediaquery-mediaquerylistener-i.md) | 媒体事件监听句柄，用于注册和注销监听回调。 |

**示例：**

```TypeScript
import { mediaquery } from '@kit.ArkUI';

let listener: mediaquery.MediaQueryListener = mediaquery.matchMediaSync('(orientation: landscape)'); // 监听横屏事件

```

