# LevelOrder

弹窗层级，可以控制弹窗显示的顺序。

**起始版本：** 18

<!--Device-unnamed-export class LevelOrder--><!--Device-unnamed-export class LevelOrder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## clamp

```TypeScript
static clamp(order: number): LevelOrder
```

创建指定顺序的弹窗层级。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LevelOrder-static clamp(order: number): LevelOrder--><!--Device-LevelOrder-static clamp(order: number): LevelOrder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| order | number | 是 | 弹窗显示顺序。取值范围为[-100000.0, 100000.0]，如果值小于-100000.0则设置为-100000.0，如果值大于100000.0则设置为100000.0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LevelOrder](arkts-arkui-promptaction-levelorder-c.md) | 返回当前对象实例。 |

## getOrder

```TypeScript
getOrder(): number
```

获取弹窗显示顺序。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LevelOrder-getOrder(): number--><!--Device-LevelOrder-getOrder(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回显示顺序数值。 |

