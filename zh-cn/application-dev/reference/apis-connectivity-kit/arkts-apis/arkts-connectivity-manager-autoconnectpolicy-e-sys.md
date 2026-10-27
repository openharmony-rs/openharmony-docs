# AutoConnectPolicy（系统接口）

```TypeScript
enum AutoConnectPolicy
```

表示打开星闪时的自动连接策略，为枚举值。

**起始版本：** 26.1.0

<!--Device-manager-enum AutoConnectPolicy--><!--Device-manager-enum AutoConnectPolicy-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

## AUTO_CONN_EXCEPT_AUDIO_DEVICES

```TypeScript
AUTO_CONN_EXCEPT_AUDIO_DEVICES = 1
```

打开星闪后，自动回连除音频设备外的所有已配对设备。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-AutoConnectPolicy-AUTO_CONN_EXCEPT_AUDIO_DEVICES = 1--><!--Device-AutoConnectPolicy-AUTO_CONN_EXCEPT_AUDIO_DEVICES = 1-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

## AUTO_CONN_EXCEPT_USER_DISCONNECTED_DEVICES

```TypeScript
AUTO_CONN_EXCEPT_USER_DISCONNECTED_DEVICES = 2
```

打开星闪后，自动回连除用户主动断连设备外的所有已配对设备。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-AutoConnectPolicy-AUTO_CONN_EXCEPT_USER_DISCONNECTED_DEVICES = 2--><!--Device-AutoConnectPolicy-AUTO_CONN_EXCEPT_USER_DISCONNECTED_DEVICES = 2-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

## AUTO_CONN_GENERAL

```TypeScript
AUTO_CONN_GENERAL = 0
```

打开星闪后，自动回连所有已配对设备。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-AutoConnectPolicy-AUTO_CONN_GENERAL = 0--><!--Device-AutoConnectPolicy-AUTO_CONN_GENERAL = 0-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。
