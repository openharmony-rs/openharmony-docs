# DynamicComponent

**DynamicComponent**用于支持在本页面内嵌入显示独立Abc（.abc文件）提供的UI，展示的内容在Worker线程中运行。 通常用于动态加载Abc页面的模块化开发场景。通过Worker线程隔离运行Abc UI，避免阻塞主线程，提升应用流畅度。

## 子组件 无

## DynamicComponent

```TypeScript
DynamicComponent(options: DynamicOptions)
```

创建DynamicComponent组件，用于显示Worker线程中运行的Abc UI。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DynamicComponentInterface-(options: DynamicOptions): DynamicComponentAttribute--><!--Device-DynamicComponentInterface-(options: DynamicOptions): DynamicComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DynamicOptions](arkts-arkui-dynamicoptions-i-sys.md) | 是 | DynamicComponent的构造配置参数，用于配置要加载的Abc页面入口、运行Worker及显示选项。 |

## 汇总

- [DynamicOptions](arkts-arkui-dynamicoptions-i-sys.md)
- [ErrorCallback](arkts-arkui-errorcallback-t-sys.md)
- [Worker](arkts-arkui-worker-t-sys.md)
