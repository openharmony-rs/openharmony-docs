# ExactTimerConfig

```TypeScript
class ExactTimerConfig
```

创建精准定时器的的初始化选项

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## callback

```TypeScript
callback(): void
```

定时器超时时执行的回调。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## interval

```TypeScript
interval: number
```

连续两次定时器触发器之间的时间间隔，单位为毫秒。对于重复定时器，**interval*的最小值为1000 ms，最大值为86400000 ms。对于单次定时器，该值为**0**。单位为：毫秒。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## name

```TypeScript
name: string
```

定时器名称。最大长度为64且不能为空。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## repeat

```TypeScript
repeat: boolean
```

定时器是否为重复定时器。**true**表示该定时器为重复定时器。**false**表示定时器为单次定时器。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager
