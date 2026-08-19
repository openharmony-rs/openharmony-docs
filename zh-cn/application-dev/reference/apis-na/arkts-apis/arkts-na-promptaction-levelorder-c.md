# LevelOrder

弹窗层级，可以控制弹窗显示的顺序。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class LevelOrder--><!--Device-unnamed-export declare class LevelOrder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## clamp

```TypeScript
static clamp(order: double): LevelOrder
```

创建指定顺序的弹窗层级。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LevelOrder-static clamp(order: double): LevelOrder--><!--Device-LevelOrder-static clamp(order: double): LevelOrder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| order | double | 是 | 弹窗显示顺序。取值范围为[-100000.0, 100000.0]，如果值小于-100000.0则设置为-100000.0，如果值大于100000.0则设置为100000.0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LevelOrder](arkts-na-promptaction-levelorder-c.md) | 返回当前对象实例。 |

## getOrder

```TypeScript
getOrder(): double
```

获取弹窗显示顺序。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LevelOrder-getOrder(): double--><!--Device-LevelOrder-getOrder(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 返回显示顺序数值。 |

