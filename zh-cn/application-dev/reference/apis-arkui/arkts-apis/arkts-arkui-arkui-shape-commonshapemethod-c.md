# CommonShapeMethod

常见的形状方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class CommonShapeMethod--><!--Device-unnamed-export declare class CommonShapeMethod-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fill

```TypeScript
fill(color: ResourceColor): this
```

设置形状的填充区域的透明度，黑色表示完全透明，白色表示完全不透明。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonShapeMethod-fill(color: ResourceColor): this--><!--Device-CommonShapeMethod-fill(color: ResourceColor): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [ResourceColor](../../apis-na/arkts-apis/arkts-na-resourcecolor-t.md) | 是 | 形状的填充区域的透明度，黑色表示完全透明，白色表示完全不透明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前对象。 |

## offset

```TypeScript
offset(offset: Position): this
```

设置相对于组件布局位置的坐标偏移。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonShapeMethod-offset(offset: Position): this--><!--Device-CommonShapeMethod-offset(offset: Position): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | [Position](../../apis-na/arkts-apis/arkts-na-units-position-i.md) | 是 | 相对于组件布局位置的坐标偏移。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前对象。 |

## position

```TypeScript
position(position: Position): this
```

设置形状的位置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonShapeMethod-position(position: Position): this--><!--Device-CommonShapeMethod-position(position: Position): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [Position](../../apis-na/arkts-apis/arkts-na-units-position-i.md) | 是 | 设置形状的位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前对象。 |

