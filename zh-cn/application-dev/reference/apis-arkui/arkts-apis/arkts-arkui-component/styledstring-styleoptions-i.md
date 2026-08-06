# StyleOptions

属性字符串初始化选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface StyleOptions--><!--Device-unnamed-export declare interface StyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## length

```TypeScript
length?: int
```

设置属性字符串样式的长度。 当length的值小于0或超出字符串长度与start的差值时，按字符串长度与start的差值处理。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyleOptions-length?: int--><!--Device-StyleOptions-length?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: int
```

设置属性字符串样式的开始位置。 当start的值小于0或超出字符串长度时，按0处理。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyleOptions-start?: int--><!--Device-StyleOptions-start?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## styledKey

```TypeScript
styledKey: StyledStringKey
```

样式类型的枚举值。

**类型：** StyledStringKey

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyleOptions-styledKey: StyledStringKey--><!--Device-StyleOptions-styledKey: StyledStringKey-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## styledValue

```TypeScript
styledValue: StyledStringValue
```

样式对象。

**类型：** StyledStringValue

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyleOptions-styledValue: StyledStringValue--><!--Device-StyleOptions-styledValue: StyledStringValue-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

