# GridCol属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。

**继承/实现关系：** GridColAttribute extends [CommonMethod<GridColAttribute>](CommonMethod<GridColAttribute>)

**起始版本：** 9

<!--Device-unnamed-declare class GridColAttribute extends CommonMethod<GridColAttribute>--><!--Device-unnamed-declare class GridColAttribute extends CommonMethod<GridColAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="gridcoloffset"></a>
## gridColOffset

```TypeScript
gridColOffset(value: number | GridColColumnOption)
```

设置相对于前一个栅格子组件偏移的列数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridColAttribute-gridColOffset(value: number | GridColColumnOption): GridColAttribute--><!--Device-GridColAttribute-gridColOffset(value: number | GridColColumnOption): GridColAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| GridColColumnOption | 是 | 相对于前一个栅格子组件偏移的列数。<br/>取值为非负整数，默认值：0 <br />非法值：按默认值处理。 |

<a id="order"></a>
## order

```TypeScript
order(value: number | GridColColumnOption)
```

设置栅格子组件的序号，根据序号从小到大对栅格子组件进行排序。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridColAttribute-order(value: number | GridColColumnOption): GridColAttribute--><!--Device-GridColAttribute-order(value: number | GridColColumnOption): GridColAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| GridColColumnOption | 是 | 元素的序号，根据栅格子组件的序号，从小到大对栅格子组件做排序。<br/>取值为非负整数，默认值：0 <br />非法值：按默认值处理。 |

<a id="span"></a>
## span

```TypeScript
span(value: number | GridColColumnOption)
```

设置占用列数。span为0，意味着该元素不参与布局计算，即不会被渲染。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridColAttribute-span(value: number | GridColColumnOption): GridColAttribute--><!--Device-GridColAttribute-span(value: number | GridColColumnOption): GridColAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| GridColColumnOption | 是 | 占用列数。<br/>取值为非负整数，默认值为1。<br />非法值：按默认值处理。 |

