# IUserAuthCallback（系统接口）

表示用户认证回调类。

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## onAcquireInfo

```TypeScript
onAcquireInfo?: (module: number, acquire: number, extraInfo: Uint8Array) => void
```

身份认证信息获取回调函数。

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| module | number | 是 |  |
| acquire | number | 是 |  |
| extraInfo | Uint8Array | 是 |  |

**示例**

```TypeScript
let authCallback: osAccount.IUserAuthCallback = {
  onResult: (result: number, extraInfo: osAccount.AuthResult) => {
    console.info('auth result = ' + result)
    console.info('auth extraInfo = ' + JSON.stringify(extraInfo));
  },
  onAcquireInfo: (module: number, acquire: number, extraInfo: Uint8Array) => {
    console.info('auth module = ' + module);
    console.info('auth acquire = ' + acquire);
    console.info('auth extraInfo = ' + JSON.stringify(extraInfo));
  }
};
```

## onResult

```TypeScript
onResult: (result: number, extraInfo: AuthResult) => void
```

身份认证结果回调函数，返回结果码和认证结果信息。

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | number | 是 |  |
| extraInfo | AuthResult | 是 |  |

**示例**

```TypeScript
let authCallback: osAccount.IUserAuthCallback = {
  onResult: (result: number, extraInfo: osAccount.AuthResult) => {
    console.info('auth result = ' + result);
    console.info('auth extraInfo = ' + JSON.stringify(extraInfo));
  }
};
```
