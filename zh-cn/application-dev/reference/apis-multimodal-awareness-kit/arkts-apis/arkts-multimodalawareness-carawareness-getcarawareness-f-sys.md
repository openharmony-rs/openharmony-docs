# getCarAwareness（系统接口）

## 导入模块

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## getCarAwareness

```TypeScript
function getCarAwareness(capability: Capability, options?: CarAwarenessOptions): Promise<CarAwarenessInfo[]>
```

/** 关闭汽车感知，订阅汽车感知结果。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-carAwareness-function getCarAwareness(capability: Capability, options?: CarAwarenessOptions): Promise<CarAwarenessInfo[]>--><!--Device-carAwareness-function getCarAwareness(capability: Capability, options?: CarAwarenessOptions): Promise<CarAwarenessInfo[]>-End-->

**系统能力：** SystemCapability.MultimodalAwareness.CarAwareness

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capability | Capability | 是 | 表示特定能力。 |
| options | [CarAwarenessOptions](arkts-multimodalawareness-carawareness-carawarenessoptions-i-sys.md) | 否 | 指示特定功能的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CarAwarenessInfo](arkts-multimodalawareness-carawareness-carawarenessinfo-i-sys.md)[]&gt; | Promise用于返回对应的能力数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Car awareness not supported. Function can not work correctly due to limited device capabilities. |
| [34000002](../../apis-multimodalawareness-kit/errorcode-carAwareness.md#34000002-指定能力不支持) | Specific capability not supported. |
| [34000001](../../apis-multimodalawareness-kit/errorcode-carAwareness.md#34000001-服务异常) | Service exception. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission check failed. A non-system application uses the system capability. |

