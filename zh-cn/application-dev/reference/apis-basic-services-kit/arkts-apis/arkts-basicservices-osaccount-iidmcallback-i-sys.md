# IIdmCallback（系统接口）

表示身份管理回调类。

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

身份管理信息获取回调函数。

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
let idmCallback: osAccount.IIdmCallback = {
  onResult: (result: number, extraInfo: Object) => {
    console.info('callback result = ' + result)
    console.info('callback onResult = ' + JSON.stringify(extraInfo));
  },
  onAcquireInfo: (module: number, acquire: number, extraInfo: Uint8Array) => {
    console.info('callback module = ' + module);
    console.info('callback acquire = ' + acquire);
    console.info('callback onacquireinfo = ' + JSON.stringify(extraInfo));
  }
};
```

## onResult

```TypeScript
onResult: (result: number, extraInfo: RequestResult) => void
```

身份管理操作结果回调函数，返回结果码和请求结果信息。

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | number | 是 |  |
| extraInfo | RequestResult | 是 |  |

**示例**

```TypeScript
let idmCallback: osAccount.IIdmCallback = {
  onResult: (result: number, extraInfo: osAccount.RequestResult) => {
    console.info('callback result = ' + result)
    console.info('callback extraInfo = ' + JSON.stringify(extraInfo));
  }
};
```
