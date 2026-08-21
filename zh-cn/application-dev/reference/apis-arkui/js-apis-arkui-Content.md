# Content
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

定义ComponentContent和NodeContent的基类，为ArkUI内容承载结构提供统一的内容管理能力，适用于需要动态创建和挂载自定义内容节点的场景。

> **说明：**
>
> - 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { Content } from '@kit.ArkUI';
```

## Content

Content是ArkUI内容承载结构的基类，为[ComponentContent](./js-apis-arkui-ComponentContent.md)和[NodeContent](./js-apis-arkui-NodeContent.md)提供统一的内容管理能力，适用于需要动态创建和挂载自定义内容节点的场景。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23