# GridColOptions

设置栅格列布局组件布局选项。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface GridColOptions--><!--Device-unnamed-export declare interface GridColOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: int | GridColColumnOption
```

栅格子组件相对于原本位置偏移的列数。

**类型：** int \| [GridColColumnOption](arkts-arkui-gridcol-gridcolcolumnoption-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GridColOptions-offset?: int | GridColColumnOption--><!--Device-GridColOptions-offset?: int | GridColColumnOption-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## order

```TypeScript
order?: int | GridColColumnOption
```

元素的序号，根据栅格子组件的序号，从小到大对栅格子组件做排序。

**类型：** int \| [GridColColumnOption](arkts-arkui-gridcol-gridcolcolumnoption-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GridColOptions-order?: int | GridColColumnOption--><!--Device-GridColOptions-order?: int | GridColColumnOption-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## span

```TypeScript
span?: int | GridColColumnOption
```

栅格子组件占用栅格容器组件的列数。 span为0表示该元素不参与布局计算，即不会被渲染。

**类型：** int \| [GridColColumnOption](arkts-arkui-gridcol-gridcolcolumnoption-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GridColOptions-span?: int | GridColColumnOption--><!--Device-GridColOptions-span?: int | GridColColumnOption-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

