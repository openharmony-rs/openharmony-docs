# HiRetrievalConfig

应用灰度活动配置。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.HiviewDFX.HiRetrieval

## deviceModel

```TypeScript
deviceModel: string
```

设备型号参数，用于标识具体设备型号（具体值由开发者根据业务需求定义）。参数值由开发者自定义，无格式和字符类型限制，最长支持128个字符，超出部分将被截断。
这些参数将作为算法输入，影响灰度圈选策略。

**类型：** string

**起始版本：** 26.0.0

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiRetrieval

## deviceType

```TypeScript
deviceType: string
```

设备类型参数，用于标识设备分类特征（具体值由开发者根据业务需求定义）。参数值由开发者自定义，无格式和字符类型限制，最长支持128个字符，超出部分将被截断。
这些参数将作为算法输入，影响灰度圈选策略。

**类型：** string

**起始版本：** 26.0.0

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiRetrieval

## userType

```TypeScript
userType: string
```

用户类型参数，用于标识用户群体特征，如'newUser'、'vipUser'等。参数值由开发者自定义，无格式和字符类型限制，最长支持128个字符，超出部分将被截断。
这些参数将作为算法输入，影响灰度圈选策略。

**类型：** string

**起始版本：** 26.0.0

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiRetrieval

