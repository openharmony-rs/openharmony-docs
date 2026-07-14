# FolderStack

FolderStack继承于[Stack]{@link stack}(层叠布局)控件，新增了<!--RP1-->折叠屏悬停<!--RP1End-->能力，通过在FolderStack的配置项
[FolderStackOptions]{@link FolderStackOptions}的upperItems数组上设置子组件id，使相应子组件自动避让折叠屏折痕区后移到上半屏。

> **说明：**

> 该组件的悬停态能力针对<!--RP2-->双折叠<!--RP2End-->设计，只在双折叠设备生效。
>
> 当该组件的父组件为[if/else：条件渲染](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)节点时，折叠屏悬停能力将会失效。


## FolderStack

```TypeScript
FolderStack(options?: FolderStackOptions)
```

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | FolderStackOptions | 否 | FolderStack的配置项。 |

## 汇总

- [FolderStackOptions](arkts-arkui-folderstack-folderstackoptions-i.md)
- [HoverEventParam](arkts-arkui-folderstack-hovereventparam-i.md)
- [OnFoldStatusChangeInfo](arkts-arkui-folderstack-onfoldstatuschangeinfo-i.md)
- [OnFoldStatusChangeCallback](arkts-arkui-folderstack-onfoldstatuschangecallback-t.md)
- [OnHoverStatusChangeCallback](arkts-arkui-folderstack-onhoverstatuschangecallback-t.md)
- [WindowStatusType](arkts-arkui-folderstack-windowstatustype-t.md)
