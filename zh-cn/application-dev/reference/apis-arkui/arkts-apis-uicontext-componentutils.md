# Class (ComponentUtils)

提供获取组件绘制区域坐标和大小的能力。

> **说明：**
>
> - 本模块首批接口从API version 10开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本Class首批接口从API version 10开始支持。
>
> - 以下API需先使用UIContext中的[getComponentUtils()](./arkts-apis-uicontext-uicontext.md#getcomponentutils)方法获取到ComponentUtils对象，再通过该对象调用对应方法。

## getRectangleById

getRectangleById(id: string): componentUtils.ComponentInfo

获取组件大小、位置、平移、缩放、旋转及仿射矩阵属性信息。

> **说明：**
>
> 该接口需要在目标组件布局、完成以后获取目标组件区域大小信息，建议在[onAppear](./arkui-ts/ts-universal-events-show-hide.md#onappear)中使用该接口。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型     | 必填   | 说明        |
| ---- | ------ | ---- | --------- |
| id   | string | 是    | 组件唯一标识id。 |

**返回值：**

| 类型                                                         | 说明                                             |
| ------------------------------------------------------------ | ------------------------------------------------ |
| [componentUtils.ComponentInfo](js-apis-arkui-componentUtils.md#componentinfo) | 组件大小、位置、平移缩放旋转及仿射矩阵属性信息。 |

**错误码：** 

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息                |
| ------ | ------------------- |
| 100001 | UI execution context not found. |

**示例：**

<!--code_no_check-->
```ts
import { ComponentUtils } from '@kit.ArkUI';

let componentUtils: ComponentUtils = uiContext.getComponentUtils();
let modePosition = componentUtils.getRectangleById("onClick");
let localOffsetWidth = modePosition.size.width;
let localOffsetHeight = modePosition.size.height;
let localOffsetX = modePosition.localOffset.x;// 获取组件相对于父组件的x轴偏移
let localOffsetY = modePosition.localOffset.y;// 获取组件相对于父组件的y轴偏移
```
