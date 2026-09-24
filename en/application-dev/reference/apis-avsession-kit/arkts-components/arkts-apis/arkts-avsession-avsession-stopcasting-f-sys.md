# stopCasting (System API)

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## stopCasting

```TypeScript
function stopCasting(session: SessionToken, callback: AsyncCallback<void>): void
```

Stop current cast and disconnect device connection.

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| session | [SessionToken](arkts-avsession-avsession-sessiontoken-i-sys.md) | Yes | Specifies the sessionId which is to be stopped. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | A callback instance used to return when cast stopped completed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [6600109](../errorcode-avsession.md#6600109-remote-session-does-not-exist) | The remote connection is not established. |

**Examples**

```TypeScript
let sessionId = 'xxx'; // Obtain the session ID after creating a session using avSession.createAVSession.
let myToken: avSession.SessionToken = {
  sessionId: sessionId,
}
avSession.stopCasting(myToken, () => {
    console.info('Succeeded in stopping casting.');
});
```


<a id="stopcasting-1"></a>

## stopCasting

```TypeScript
function stopCasting(session: SessionToken): Promise<void>
```

Stop current cast and disconnect device connection.

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| session | [SessionToken](arkts-avsession-avsession-sessiontoken-i-sys.md) | Yes | Specifies the sessionId which is to be stopped. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise for the result |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [6600109](../errorcode-avsession.md#6600109-remote-session-does-not-exist) | The remote connection is not established. |

**Examples**

```TypeScript
let sessionId = 'xxx'; // Obtain the session ID after creating a session using avSession.createAVSession.
let myToken: avSession.SessionToken = {
  sessionId: sessionId,
}
avSession.stopCasting(myToken).then(() => {
  console.info('Succeeded in stopping casting.');
});
```
