# MediaQuery

提供根据不同媒体类型定义不同的样式。 定义MediaQuery接口。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-declare class MediaQuery--><!--Device-unnamed-declare class MediaQuery-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SystemMediaQuery, MediaQueryEvent, MediaQueryList } from '@kit.ArkUI';
```

## matchMedia

```TypeScript
static matchMedia(condition: string): MediaQueryList
```

根据媒体查询条件，创建MediaQueryList对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MediaQuery-static matchMedia(condition: string): MediaQueryList--><!--Device-MediaQuery-static matchMedia(condition: string): MediaQueryList-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | string | 是 | 用于查询的条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaQueryList](arkts-arkui-system-mediaquery-mediaquerylist-i.md) | 创建MediaQueryList对象，详情见下表说明。 |

