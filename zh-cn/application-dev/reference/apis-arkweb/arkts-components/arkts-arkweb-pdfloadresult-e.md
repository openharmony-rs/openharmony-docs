# PdfLoadResult

定义PDF页面的加载结果，用于标识PDF文件加载过程中的各种状态和错误类型，帮助开发者在PDF显示失败时进行错误诊断和用户提示。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## LOAD_SUCCESS

```TypeScript
LOAD_SUCCESS = 0
```

PDF页面加载成功。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## PARSE_ERROR_FILE

```TypeScript
PARSE_ERROR_FILE = 1
```

PDF文件加载失败。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## PARSE_ERROR_FORMAT

```TypeScript
PARSE_ERROR_FORMAT = 2
```

PDF文件格式不支持。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## PARSE_ERROR_PASSWORD

```TypeScript
PARSE_ERROR_PASSWORD = 3
```

PDF文件密码不正确。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## PARSE_ERROR_HANDLER

```TypeScript
PARSE_ERROR_HANDLER = 4
```

PDF文件处理失败。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core
