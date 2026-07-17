# BusinessId（系统接口）

业务ID枚举。业务ID是伴随设备支持的某个业务场景的唯一标识。不同的伴随设备由于认证安全性差异，支持的业务场景范围也不同，例如免解锁执行语音指令。

不同业务ID的伴随设备关系是独立的，互不干扰，可以独立添加、删除、认证。

当前伴随设备模块的业务有：OH默认业务、锁屏解锁、解锁应用锁以及语音指令在锁屏执行前的身份鉴权等。

业务的添加对于服务端设备支持的场景有要求，如多屏协同业务，要求服务端设备支持委托认证场景。

**起始版本：** 23

<!--Device-companionDeviceAuth-enum BusinessId--><!--Device-companionDeviceAuth-enum BusinessId-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## DEFAULT

```TypeScript
DEFAULT = 0
```

默认业务ID。系统预设的默认业务标识，用于基本的伴随设备认证场景。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BusinessId-DEFAULT = 0--><!--Device-BusinessId-DEFAULT = 0-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## VENDOR_BEGIN

```TypeScript
VENDOR_BEGIN = 10000
```

厂商自定义业务标识取值起点。厂商可在此值基础上自定义扩展业务ID，实际取值需大于等于10000，避免与系统保留值[0-9999]冲突。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BusinessId-VENDOR_BEGIN = 10000--><!--Device-BusinessId-VENDOR_BEGIN = 10000-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

