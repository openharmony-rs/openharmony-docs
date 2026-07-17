# SaveButtonOnClickResult

保存控件点击后的授权结果。

**起始版本：** 10

<!--Device-unnamed-declare enum SaveButtonOnClickResult--><!--Device-unnamed-declare enum SaveButtonOnClickResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SUCCESS

```TypeScript
SUCCESS = 0
```

保存控件点击后权限授权成功。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonOnClickResult-SUCCESS = 0--><!--Device-SaveButtonOnClickResult-SUCCESS = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TEMPORARY_AUTHORIZATION_FAILED

```TypeScript
TEMPORARY_AUTHORIZATION_FAILED = 1
```

保存控件点击后权限授权失败。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonOnClickResult-TEMPORARY_AUTHORIZATION_FAILED = 1--><!--Device-SaveButtonOnClickResult-TEMPORARY_AUTHORIZATION_FAILED = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CANCELED_BY_USER

```TypeScript
CANCELED_BY_USER = 2
```

保存控件点击后，弹窗中用户取消授权。仅在调用[userCancelEvent](SaveButtonAttribute#userCancelEvent)并设置参数为true时，回调结果中才会返回该值。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonOnClickResult-CANCELED_BY_USER = 2--><!--Device-SaveButtonOnClickResult-CANCELED_BY_USER = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

