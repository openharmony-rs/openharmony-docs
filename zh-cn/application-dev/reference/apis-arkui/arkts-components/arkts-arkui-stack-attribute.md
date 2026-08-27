# Stack属性/事件

除支持通用属性外，还支持以下属性：支持通用事件。

**继承/实现关系：** StackAttribute extends CommonMethod<StackAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## alignContent

```TypeScript
alignContent(value: Alignment)
```

设置子组件在容器内的对齐方式。该属性与align同时设置时，后设置的属性值会覆盖先设置的属性值。该属性与接口构造入参同时设置时，以属性设置 的值为准，与设置顺序无关。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Alignment](../arkts-apis/arkts-arkui-alignment-e.md) | 是 | 所有子组件在容器内的对齐方式。 默认值：Alignment.Center 非法值：按默认值处理。 |

## syncLoad

```TypeScript
syncLoad(enable: boolean)
```

设置是否同步加载Stack区域内所有子组件。同步加载时，所有子组件会在当前帧内完成布局计算和渲染；异步加载时，系统会根据当前帧的布局耗时动态调整子组件的布局时机，避免阻塞主线程。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否同步加载Stack区域内所有子组件。 true表示同步加载；false表示异步加载。 默认值：true    **说明：** 设置为false时，在首次显示场景，若当前帧布局耗时超过50ms，会将Stack区域内尚未布局的子组件延后到下一帧进行布局。 |
