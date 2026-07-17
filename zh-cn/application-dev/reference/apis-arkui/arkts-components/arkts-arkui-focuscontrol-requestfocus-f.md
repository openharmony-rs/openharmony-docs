# requestFocus

## requestFocus

```TypeScript
function requestFocus(value: string): boolean
```

方法语句中可使用的全局接口，调用此接口可以主动让焦点在下一帧渲染时转移至参数指定的组件上。

如果需要指定组件立刻获焦，推荐使用FocusController中的焦点同步转移接口[requestFocus](../arkts-apis/arkts-arkui-arkui-uicontext-focuscontroller-c.md#requestfocus-1)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-focusControl-function requestFocus(value: string): boolean--><!--Device-focusControl-function requestFocus(value: string): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 目标组件使用接口key(value: string)或id(value: string)绑定的字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回值表示是否成功给目标组件申请到焦点。若参数指向的目标组件存在且已挂载组件树，并具备获焦能力，则返回true，否则返回false。 |

