# UserRecognitionStatus

```TypeScript
enum UserRecognitionStatus
```

用户识别状态枚举。

**设备行为差异：** 该接口仅在Car设备中可正常调用，在其他设备类型中返回null。

**起始版本：** 26.0.1

<!--Device-userAuth-enum UserRecognitionStatus--><!--Device-userAuth-enum UserRecognitionStatus-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## MATCH

```TypeScript
MATCH = 2
```

识别的用户与前台用户匹配。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-UserRecognitionStatus-MATCH = 2--><!--Device-UserRecognitionStatus-MATCH = 2-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## MISMATCH

```TypeScript
MISMATCH = 1
```

识别的用户与前台用户不匹配。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-UserRecognitionStatus-MISMATCH = 1--><!--Device-UserRecognitionStatus-MISMATCH = 1-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## UNCERTAIN

```TypeScript
UNCERTAIN = 0
```

不确定机主。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-UserRecognitionStatus-UNCERTAIN = 0--><!--Device-UserRecognitionStatus-UNCERTAIN = 0-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core
