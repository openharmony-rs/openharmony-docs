# CollaborateEventType

协同事件类型的枚举。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## SEND_FAILURE

```TypeScript
SEND_FAILURE = 0
```

表示任务发送失败。在跨设备协同过程中，当发送协作任务（如协作事件）失败时产生此事件，常见原因包括网络异常、对端设备不可达等。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## COLOR_SPACE_CONVERSION_FAILURE

```TypeScript
COLOR_SPACE_CONVERSION_FAILURE = 1
```

表示色彩空间转换失败。在跨设备图像协同场景下，当需要将图像数据从源设备色彩空间转换为目标设备色彩空间格式失败时产生此事件，常见原因包括色彩格式不支持或转换参数

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration
