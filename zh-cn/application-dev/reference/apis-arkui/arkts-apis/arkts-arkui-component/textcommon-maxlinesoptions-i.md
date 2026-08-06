# MaxLinesOptions

配置TextArea组件，文本超长时的显示效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface MaxLinesOptions--><!--Device-unnamed-export declare interface MaxLinesOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## overflowMode

```TypeScript
overflowMode?: MaxLinesMode
```

\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_可配置\_\_\_MD\_LINK\_DESC\_USD\_6\_\_\_组件的非内联模式。当超出设置的 \_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_最大行数时，会启用滚动效果。需同时配置 \_\_\_MD\_LINK\_DESC\_USD\_7\_\_\_，且仅当 \_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_为None或Clip时，\_\_\_INLINE\_CODE\_DESC\_USD\_3\_\_\_才能生效。默认情况下，\_\_\_INLINE\_CODE\_DESC\_USD\_4\_\_\_的值为Clip，超出\_\_\_INLINE\_CODE\_DESC\_USD\_5\_\_\_后文本会被截断。

**类型：** MaxLinesMode

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MaxLinesOptions-overflowMode?: MaxLinesMode--><!--Device-MaxLinesOptions-overflowMode?: MaxLinesMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

