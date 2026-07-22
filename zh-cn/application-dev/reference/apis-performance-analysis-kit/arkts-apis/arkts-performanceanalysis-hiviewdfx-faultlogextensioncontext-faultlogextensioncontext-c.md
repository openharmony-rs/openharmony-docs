# FaultLogExtensionContext

FaultLogExtensionContext是[FaultLogExtensionAbility](arkts-performanceanalysis-hiviewdfx-faultlogextensionability-faultlogextensionability-c.md)的上下文环境，继承自[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。

FaultLogExtensionContext模块提供访问[FaultLogExtensionAbility](arkts-performanceanalysis-hiviewdfx-faultlogextensionability-faultlogextensionability-c.md)的资源的能力，对于扩展的ExtensionAbility，可直接将ExtensionContext作为上下文环境，或者定义一个继承自ExtensionContext的类型作为上下文环境。
> **说明：**  
>  
> - 本模块接口从API version 21开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**继承/实现关系：** FaultLogExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export default class FaultLogExtensionContext extends ExtensionContext--><!--Device-unnamed-export default class FaultLogExtensionContext extends ExtensionContext-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.FaultLogger

## 导入模块

```TypeScript
import { FaultLogExtensionContext } from '@kit.PerformanceAnalysisKit';
```

