# Operation

属性操作指示的枚举。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## READABLE

```TypeScript
READABLE = 0x01
```

当该比特置位后，属性值可被读取。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## WRITE_NO_RESPONSE

```TypeScript
WRITE_NO_RESPONSE = 0x02
```

当该比特置位后，属性值可被写入，写入后无反馈。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## WRITE_WITH_RESPONSE

```TypeScript
WRITE_WITH_RESPONSE = 0x04
```

当该比特置位后，属性值可被写入，写入后产生反
馈给客户端。
写操作完成后，会反馈给客户端。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## NOTIFY

```TypeScript
NOTIFY = 0x08
```

当该比特置位后，属性值通过通知方式传递给客户
端。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

