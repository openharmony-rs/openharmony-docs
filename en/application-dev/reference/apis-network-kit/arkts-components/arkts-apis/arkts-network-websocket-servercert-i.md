# ServerCert

```TypeScript
export interface ServerCert
```

Certificate information, which includes the paths of the WebSocketServer certificate file and private key file.

**Since:** 19

<!--Device-webSocket-export interface ServerCert--><!--Device-webSocket-export interface ServerCert-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { webSocket } from '@kit.NetworkKit';
```

## certPath

```TypeScript
certPath: string
```

Path of the server certificate file.

**Type:** string

**Since:** 19

<!--Device-ServerCert-certPath: string--><!--Device-ServerCert-certPath: string-End-->

**System capability:** SystemCapability.Communication.NetStack

## keyPath

```TypeScript
keyPath: string
```

Path of the private key file of the server certificate.

**Type:** string

**Since:** 19

<!--Device-ServerCert-keyPath: string--><!--Device-ServerCert-keyPath: string-End-->

**System capability:** SystemCapability.Communication.NetStack
