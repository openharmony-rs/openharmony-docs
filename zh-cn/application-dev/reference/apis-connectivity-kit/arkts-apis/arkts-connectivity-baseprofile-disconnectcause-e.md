# DisconnectCause

```TypeScript
enum DisconnectCause
```

枚举，Profile断开连接的原因。

**起始版本：** 12

<!--Device-baseProfile-enum DisconnectCause--><!--Device-baseProfile-enum DisconnectCause-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## CONNECT_FAIL_INTERNAL

```TypeScript
CONNECT_FAIL_INTERNAL = 5
```

内部错误。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DisconnectCause-CONNECT_FAIL_INTERNAL = 5--><!--Device-DisconnectCause-CONNECT_FAIL_INTERNAL = 5-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## CONNECT_FROM_CAR

```TypeScript
CONNECT_FROM_CAR = 3
```

连接请求需从车机侧发起。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DisconnectCause-CONNECT_FROM_CAR = 3--><!--Device-DisconnectCause-CONNECT_FROM_CAR = 3-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## CONNECT_FROM_KEYBOARD

```TypeScript
CONNECT_FROM_KEYBOARD = 1
```

连接请求需从键盘侧发起。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DisconnectCause-CONNECT_FROM_KEYBOARD = 1--><!--Device-DisconnectCause-CONNECT_FROM_KEYBOARD = 1-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## CONNECT_FROM_MOUSE

```TypeScript
CONNECT_FROM_MOUSE = 2
```

连接请求需从鼠标侧发起。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DisconnectCause-CONNECT_FROM_MOUSE = 2--><!--Device-DisconnectCause-CONNECT_FROM_MOUSE = 2-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## TOO_MANY_CONNECTED_DEVICES

```TypeScript
TOO_MANY_CONNECTED_DEVICES = 4
```

当前连接数量超过上限。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DisconnectCause-TOO_MANY_CONNECTED_DEVICES = 4--><!--Device-DisconnectCause-TOO_MANY_CONNECTED_DEVICES = 4-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## USER_DISCONNECT

```TypeScript
USER_DISCONNECT = 0
```

用户主动断开连接。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DisconnectCause-USER_DISCONNECT = 0--><!--Device-DisconnectCause-USER_DISCONNECT = 0-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core
