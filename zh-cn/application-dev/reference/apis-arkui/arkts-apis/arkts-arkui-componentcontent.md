# ComponentContent

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ComponentContent](arkts-arkui-componentcontent-c.md) | 有两种创建实体封装组件的方式。ComponentContent需要通过update接口手动更新内容，主要适用于弹窗等解耦封装场景；ReactiveComponentContent支持响应式数据自动更新、完整生命周期管理和组件复用，适用于长列表等高性能渲染场景。开发者可根据实际需求从以下方式中选择。 |
| [ReactiveComponentContent](arkts-arkui-componentcontent-reactivecomponentcontent-c.md) | ReactiveComponentContent继承自[Content](../../../reference/apis-arkui/js-apis-arkui-Content.md#content-1)，是一个用于动态承载和复用UI内容的容器组件。它通过@Builder函数构建UI，并利用[ReactiveBuilderNode](arkts-arkui-buildernode-reactivebuildernode-c.md)生成和管理组件树。该组件的核心价值在于为动态内容提供完整的生命周期管理，使其能够融入ArkUI的组件复用体系，特别适用于长列表等需要高性能渲染的场景。 |
