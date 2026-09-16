# @Entry

```TypeScript
declare const Entry: ClassDecorator & ((options?: LocalStorage | EntryOptions) => ClassDecorator)
```

\@Entry装饰的自定义组件将作为UI页面的入口，被框架识别为页面的根组件，适用于构建独立UI页面的场景。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
