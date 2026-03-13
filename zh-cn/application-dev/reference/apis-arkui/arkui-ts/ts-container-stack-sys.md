# Stack (系统接口)

堆叠容器，子组件按照顺序依次入栈，后一个子组件覆盖前一个子组件。

> **说明：**
>
> 该组件从API version 11开始支持。后续版本如有新增内容将采用上角标单独标记该内容的起始版本。
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[Stack](ts-container-stack.md)。

## 属性

### pointLight

ArkTS-Dyn: pointLight(value: PointLightStyle): StackAttribute

ArkTS-Sta: pointLight(value: PointLightStyle | undefined): StackAttribute

设置点光源样式。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明         |
| ------ | ------------------------------------------------------------ | ---- | ------------ |
| value  | ArkTS-Dyn: [PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle)<br/>ArkTS-Sta: [PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle) \| undefined | 是   | 点光源样式。 |

