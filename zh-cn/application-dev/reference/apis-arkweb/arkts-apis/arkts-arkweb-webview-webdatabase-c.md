# WebDataBase

Web组件数据库管理对象。

**起始版本：** 9

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## deleteHttpAuthCredentials

```TypeScript
static deleteHttpAuthCredentials(): void
```

清除所有已保存的HTTP身份验证凭据，该方法为同步方法。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**示例**

```TypeScript
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('deleteHttpAuthCredentials')
        .onClick(() => {
          try {
            webview.WebDataBase.deleteHttpAuthCredentials();
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## existHttpAuthCredentials

```TypeScript
static existHttpAuthCredentials(): boolean
```

判断是否存在任何已保存的HTTP身份验证凭据，该方法为同步方法。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否存在任何已保存的HTTP身份验证凭据。 |

**示例**

```TypeScript
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('existHttpAuthCredentials')
        .onClick(() => {
          try {
            if (webview.WebDataBase.existHttpAuthCredentials()) {
                console.info('HTTP auth credentials exist.');
              } else {
                console.info('No HTTP auth credentials found.');
              }
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## getHttpAuthCredentials

```TypeScript
static getHttpAuthCredentials(host: string, realm: string): Array<string>
```

检索给定主机和域的HTTP身份验证凭据，该方法为同步方法。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | string | 是 | HTTP身份验证凭据应用的主机地址，格式如'www.example.com'或'192.168.1.1'，不包含协议和端口号。 |
| realm | string | 是 | HTTP身份验证凭据应用的认证域，表示在同一主机下进行身份验证的范围或保护区域，通常由服务器返回的WWW-Authenticate头指定。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;string & gt; | 包含用户名和密码的数组，检索失败返回空数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.  2. Incorrect parameter types. 3.Parameter verification failed. |

**示例**

```TypeScript
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  host: string = 'www.spincast.org';
  realm: string = 'protected example';
  usernamePassword: string[] = [];

  build() {
    Column() {
      Button('getHttpAuthCredentials')
        .onClick(() => {
          try {
            this.usernamePassword = webview.WebDataBase.getHttpAuthCredentials(this.host, this.realm);
            console.info('num: ' + this.usernamePassword.length);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## saveHttpAuthCredentials

```TypeScript
static saveHttpAuthCredentials(host: string, realm: string, username: string, password: string): void
```

保存给定主机和域的HTTP身份验证凭据，该方法为同步方法。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | string | 是 | HTTP身份验证凭据应用的主机，用于匹配凭据对应的主机。 |
| realm | string | 是 | HTTP身份验证凭据应用的域，用于匹配凭据对应的认证域。 |
| username | string | 是 | 用于HTTP身份验证的用户名，表示访问受保护资源的身份标识。 |
| password | string | 是 | 用于HTTP身份验证的密码，配合用户名完成身份验证。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.  2. Incorrect parameter types. 3.Parameter verification failed. |

**示例**

```TypeScript
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  host: string = 'www.spincast.org';
  realm: string = 'protected example';

  build() {
    Column() {
      Button('saveHttpAuthCredentials')
        .onClick(() => {
          try {
            webview.WebDataBase.saveHttpAuthCredentials(this.host, this.realm, 'Stromgol', 'Laroche');
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```
