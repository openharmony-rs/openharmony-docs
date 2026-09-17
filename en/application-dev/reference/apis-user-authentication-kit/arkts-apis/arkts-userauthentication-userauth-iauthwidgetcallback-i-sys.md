# IAuthWidgetCallback (System API)

Defines the callback of the authentication widget. The authentication widget uses this callback to obtain commands sent by the user authentication framework and perform corresponding authentication operations based on the command content.

**Since:** 10

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## sendCommand

```TypeScript
sendCommand(cmdData: string): void
```

Triggered to receive commands from the user authentication framework. The user authentication framework uses this callback to send commands to the identity authentication widget. The widget needs to parse the command content and perform corresponding operations.

**Since:** 10

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cmdData | string | Yes | Command data. It is a JSON string, containing the command content sent by the user authentication framework to the authentication widget. The JSON structure contains fields based on the command type. Common fields include **commandType** (string, command type), **authType** (array, authentication type list), and **result** (number, authentication result code). The widget needs to parse the data and perform the corresponding operations based on the command type. |

**Examples**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

const userAuthWidgetMgrVersion = 1;
try {
  let userAuthWidgetMgr = userAuth.getUserAuthWidgetMgr(userAuthWidgetMgrVersion);
  console.info('get userAuthWidgetMgr instance successfully.');
  userAuthWidgetMgr.on('command', {
    sendCommand: (cmdData) => {
      console.info(`The cmdData is ${cmdData}`);
    }
  })
  console.info('subscribe authentication event successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`userAuth widgetMgr failed. Code is ${err?.code}, message is ${err?.message}`);
}
```
