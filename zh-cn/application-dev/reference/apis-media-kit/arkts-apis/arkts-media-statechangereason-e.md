# StateChangeReason

表示播放或录制实例状态机切换原因的枚举，伴随state一起上报。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.Core

## USER

```TypeScript
USER = 1
```

表示用户行为造成的状态切换，由用户或客户端主动调用接口产生。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## BACKGROUND

```TypeScript
BACKGROUND = 2
```

表示后台系统行为造成的状态切换，比如应用未注册播控中心权限，退到后台时被系统强制暂停或停止。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

