# MultithreadingDetectionOptions

多线程检测功能参数配置。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Utils.Lang

## abort

```TypeScript
abort?: boolean
```

若 abort 为 **true**，应用将崩溃；若 abort 为 **false**，应用将不崩溃。默认值为 **true**。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

## frequency

```TypeScript
frequency?: number
```

多线程检测的采样频率。
该值必须为整数，最小为 **100**，最大为 **2147483647**（默认 **100**）。
该值应为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

## interval

```TypeScript
interval?: number
```

多线程检测的时间间隔（分钟）。
只有距离上次检测的时间超过此间隔时才会再次上报错误。
该值必须为 [0,1440] 范围内的整数（默认 5min）。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

