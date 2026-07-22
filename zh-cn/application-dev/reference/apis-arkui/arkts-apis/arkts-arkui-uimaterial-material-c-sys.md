# Material（系统接口）

系统材质对象基类。

**起始版本：** 26.0.0

<!--Device-uiMaterial-class Material--><!--Device-uiMaterial-class Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: MaterialOptions)
```

Material的构造函数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-Material-constructor(options?: MaterialOptions)--><!--Device-Material-constructor(options?: MaterialOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [MaterialOptions](arkts-arkui-uimaterial-materialoptions-i-sys.md) | 否 | 系统材质配置选项，包括材质类型。<br/>默认值：{type:MaterialType.NONE} |

