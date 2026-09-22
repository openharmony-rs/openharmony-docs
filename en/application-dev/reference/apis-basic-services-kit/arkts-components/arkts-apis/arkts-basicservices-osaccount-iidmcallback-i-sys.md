# IIdmCallback (System API)

```TypeScript
interface IIdmCallback
```

Provides callbacks for IDM.

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## onAcquireInfo

```TypeScript
onAcquireInfo?: (module: number, acquire: number, extraInfo: Uint8Array) => void
```

Called to acquire IDM information.

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| module | number | Yes |  |
| acquire | number | Yes |  |
| extraInfo | Uint8Array | Yes |  |

**Examples**

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

Called to return the result code and request result information.

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | number | Yes |  |
| extraInfo | [RequestResult](arkts-basicservices-osaccount-requestresult-i-sys.md) | Yes |  |

**Examples**

```TypeScript
let idmCallback: osAccount.IIdmCallback = {
  onResult: (result: number, extraInfo: osAccount.RequestResult) => {
    console.info('callback result = ' + result)
    console.info('callback extraInfo = ' + JSON.stringify(extraInfo));
  }
};
```
