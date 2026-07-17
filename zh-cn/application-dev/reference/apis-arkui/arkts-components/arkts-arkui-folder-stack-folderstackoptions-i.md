# FolderStackOptions

> **说明：**  
>  
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

<!--Device-unnamed-interface FolderStackOptions--><!--Device-unnamed-interface FolderStackOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## upperItems

```TypeScript
upperItems?: Array<string>
```

定义悬停态会被移到上半屏的子组件的id数组。

当悬停触发时，upperItems数组中的子组件自动避让折叠屏折痕区后移到上半屏，其它组件堆叠在下半屏区域。

**类型：** Array<string>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FolderStackOptions-upperItems?: Array<string>--><!--Device-FolderStackOptions-upperItems?: Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

