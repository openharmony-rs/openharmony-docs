# DownloadConfiguration（系统接口）

下载过程中的属性配置。

**起始版本：** 18

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## forceDisableProfile

```TypeScript
forceDisableProfile: boolean
```

是否可直接去激活配置文件。true表示切换配置文件时，如果需要去激活当前的配置文件，则可以直接操作。false表示如果需要去激活当前的配置文件，则会返回错误，并得到用户授权后再继续调用该接口，执行切换配置文件操作。

**类型：** boolean

**起始版本：** 18

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## isPprAllowed

```TypeScript
isPprAllowed: boolean
```

是否得到用户授权。true表示得到用户授权，服务提供商可实施配置文件策略规则；false表示未得到用户授权，不允许实施配置文件策略规则。

**类型：** boolean

**起始版本：** 18

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## switchAfterDownload

```TypeScript
switchAfterDownload: boolean
```

下载成功后是否启用配置文件。true表示启用，false表示不启用。

**类型：** boolean

**起始版本：** 18

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。
