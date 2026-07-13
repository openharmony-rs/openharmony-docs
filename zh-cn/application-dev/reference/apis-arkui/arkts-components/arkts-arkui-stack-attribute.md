# Stack属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。

**继承/实现关系：** StackAttribute extends [CommonMethod<StackAttribute>](CommonMethod<StackAttribute>)

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignContent

```TypeScript
alignContent(value: Alignment)
```

设置子组件在容器内的对齐方式。该属性与[align](arkts-arkui-commonmethod-c.md#align-1)同时设置时，后设置的属性生效。该属性与接口的构造入参同时设置时，生效属性上的设置效果。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Alignment | 是 | 所有子组件在容器内的对齐方式。<br/>默认值：Alignment.Center <br />非法值：按默认值处理。 |

## syncLoad

```TypeScript
syncLoad(enable: boolean)
```

设置是否同步加载Stack区域内所有子组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否同步加载Stack区域内所有子组件。<br/>true表示同步加载；false表示异步加载。<br/>默认值：true<br/>**说明：** <br/>设置为false时，在首次显示场景，若当前帧布局耗时超过50ms，会将Stack区域内尚未布局的子组件延后到下一帧进行布局。 |

