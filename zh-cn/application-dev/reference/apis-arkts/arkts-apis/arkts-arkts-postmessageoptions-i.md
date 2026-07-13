# PostMessageOptions

明确数据传递过程中需要转移所有权的对象，这些对象必须是ArrayBuffer，在发送方的上下文中将变为不可用，仅在接收方可用。

**起始版本：** 7

**系统能力：** SystemCapability.Utils.Lang

## transfer

```TypeScript
transfer?: Object[]
```

ArrayBuffer数组，用于传递所有权。该数组中不可传入null。

**类型：** Object[]

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

