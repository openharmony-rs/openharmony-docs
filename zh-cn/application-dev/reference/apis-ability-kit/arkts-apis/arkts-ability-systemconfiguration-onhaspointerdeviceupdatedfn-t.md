# OnHasPointerDeviceUpdatedFn

```TypeScript
type OnHasPointerDeviceUpdatedFn = (hasPointerDevice: boolean) => void
```

在注册系统环境变化的监听后，当指针设备连接或者断开时触发回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hasPointerDevice | boolean | 是 | 指针设备是否已连接，如键盘、鼠标、触控板等。true表示设备已连接，false表示设备未连接。 |
