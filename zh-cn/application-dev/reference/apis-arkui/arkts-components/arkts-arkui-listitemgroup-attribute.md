# ListItemGroup属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** ListItemGroupAttribute extends [CommonMethod<ListItemGroupAttribute>](CommonMethod<ListItemGroupAttribute>)

**起始版本：** 9

<!--Device-unnamed-declare class ListItemGroupAttribute extends CommonMethod<ListItemGroupAttribute>--><!--Device-unnamed-declare class ListItemGroupAttribute extends CommonMethod<ListItemGroupAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## childrenMainSize

```TypeScript
childrenMainSize(value: ChildrenMainSize)
```

设置ListItemGroup组件的子组件在主轴方向的大小信息。
> **说明：**  
>  
> - 必须同时给所在的List组件设置childrenMainSize属性才可以正常生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ListItemGroupAttribute-childrenMainSize(value: ChildrenMainSize): ListItemGroupAttribute--><!--Device-ListItemGroupAttribute-childrenMainSize(value: ChildrenMainSize): ListItemGroupAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ChildrenMainSize](arkts-arkui-childrenmainsize-c.md) | 是 | 该对象用来维护子组件在主轴方向的大小信息。 |

## divider

```TypeScript
divider(
    value: ListDividerOptions | null,
  )
```

设置ListItem分割线样式，默认无分割线。

strokeWidth，startMargin和endMargin不支持设置百分比。

ListItem设置[多态样式](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)时，被按压的子组件上下的分割线不绘制。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ListItemGroupAttribute-divider(    value: ListDividerOptions | null,  ): ListItemGroupAttribute--><!--Device-ListItemGroupAttribute-divider(    value: ListDividerOptions | null,  ): ListItemGroupAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ListDividerOptions](arkts-arkui-listdivideroptions-i.md) \| null | 是 | ListItem分割线样式。<br/> 默认值：null [since 18] |

