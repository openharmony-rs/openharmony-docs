# commonEventSubscriber

<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=227499a15769ff89e238d0afb653f1633e59b877 translatedAt=2026-07-21T08:36:10.955Z pushedAt=2026-07-22T09:00:29.164Z -->

> **NOTE**
> - This module supports both ArkTS-Dyn and ArkTS-Sta.
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## CommonEventSubscriber

Represents the subscriber of a common event. The **CommonEventSubscriber** module provides the capabilities for processing ordered common events, including obtaining and setting the data and code transferred by events, checking whether the current common event is an ordered or sticky event, terminating an ordered common event or clearing the termination status, ending the processing of the current ordered common event, and obtaining subscription information of a subscriber. This module is applicable to data processing and process control of the received common event by the subscriber.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

### How to Use

Before using the **CommonEventSubscriber** module, you must obtain a **subscriber** object by calling [commonEventManager.createSubscriber](js-apis-commonEventManager.md#commoneventmanagercreatesubscriber-1).

<!--code_no_check-->

```ts
import { commonEventManager } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Define a subscriber to save the created subscriber object for subsequent subscription and unsubscription.
let subscriber: commonEventManager.CommonEventSubscriber | null = null;
// Subscriber information.
let subscribeInfo: commonEventManager.CommonEventSubscribeInfo = {
  events: ['event']
};
// Create a subscriber.
subscriber = commonEventManager.createSubscriberSync(subscribeInfo);
```

### getCode

ArkTS-Dyn: getCode(callback: AsyncCallback\<number>): void

ArkTS-Sta: getCode(callback: AsyncCallback\<int>): void

ArkTS-Dyn: Obtains the result code (number type) of an ordered common event. This API uses an asynchronous callback to return the result.

ArkTS-Sta: Obtains the result code (int type) of an ordered common event. This API uses an asynchronous callback to return the result.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Parameters**

| Name  | Type                  | Mandatory | Description              |
| -------- | ---------------------- | ---- | ------------------ |
| callback | ArkTS-Dyn: AsyncCallback\<number\><br/>ArkTS-Sta: AsyncCallback\<int\> | Yes | Callback used to return the result. If the result code of an ordered common event is successfully obtained, **err** is **undefined**, and data is the code obtained; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.      |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.getCode((err: BusinessError, code: number) => {
  if (err) {
    console.error(`Failed to get code. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting code, code is ${JSON.stringify(code)}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.getCode((err: BusinessError | null, code: int | undefined | null) => {
  if (err) {
    console.error(`Failed to get code. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting code, code is ${JSON.stringify(code)}`);
});
```

### getCode

ArkTS-Dyn: getCode(): Promise\<number>

ArkTS-Sta: getCode(): Promise\<int>

ArkTS-Dyn: Obtains the result code (number type) of an ordered common event. This API uses a promise to return the result.

ArkTS-Sta: Obtains the result code (int type) of an ordered common event. This API uses a promise to return the result.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Return value**

| Type            | Description                |
| ---------------- | -------------------- |
| ArkTS-Dyn: Promise\<number><br/>ArkTS-Sta:Promise\<int> | Promise used to return the code delivered by the ordered common event. |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.getCode().then((code: number) => {
  console.info(`Succeeded in getting code, code is ${JSON.stringify(code)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get code. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.getCode().then((code: int) => {
  console.info(`Succeeded in getting code, code is ${JSON.stringify(code)}`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get code. Code is ${error.code}, message is ${error.message}`);
});
```

### getCodeSync<sup>10+</sup>

ArkTS-Dyn: getCodeSync(): number

ArkTS-Sta: getCodeSync(): int

ArkTS-Dyn: Obtains the result code (number type) of an ordered common event. This API returns the result synchronously.

ArkTS-Sta: Obtains the result code (int type) of an ordered common event. This API returns the result synchronously.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 10

**ArkTS-Sta start version:** 23

**Return value**

| Type            | Description                |
| ---------------- | -------------------- |
| ArkTS-Dyn: number<br/>ArkTS-Sta: int | Code delivered by the ordered common event. |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
let code: number = subscriber.getCodeSync();
console.info(`Succeeded in getting code, code is ${JSON.stringify(code)}`);
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
let code: int = subscriber.getCodeSync();
console.info(`Succeeded in getting code, code is ${JSON.stringify(code)}`);
```

### setCode

ArkTS-Dyn: setCode(code: number, callback: AsyncCallback\<void>): void

ArkTS-Sta: setCode(code: int, callback: AsyncCallback\<void>): void

ArkTS-Dyn: Sets the result code (number type) of an ordered common event. This API uses an asynchronous callback to return the result.

ArkTS-Sta: Sets the result code (int type) of an ordered common event. This API uses an asynchronous callback to return the result.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Parameters**

| Name  | Type                | Mandatory| Description                  |
| -------- | -------------------- | ---- | ---------------------- |
| code     | ArkTS-Dyn: number<br/>ArkTS-Sta: int | Yes   | Code delivered by the ordered common event.   |
| callback | AsyncCallback\<void> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.      |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.setCode(1, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set code. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting code.`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.setCode(1, (err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to set code. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting code.`);
});
```

### setCode

ArkTS-Dyn: setCode(code: number): Promise\<void>

ArkTS-Sta: setCode(code: int): Promise\<void>

ArkTS-Dyn: Sets the result code (number type) of an ordered common event. This API uses a promise to return the result.

ArkTS-Sta: Sets the result code (int type) of an ordered common event. This API uses a promise to return the result.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| code   | ArkTS-Dyn: number<br/>ArkTS-Sta: int | Yes   | Code delivered by the ordered common event. |

**Return value**

| Type            | Description                |
| ---------------- | -------------------- |
| Promise\<void>   | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.      |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.setCode(1).then(() => {
  console.info(`Succeeded in setting code.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set code. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.setCode(1).then(() => {
  console.info(`Succeeded in setting code.`);
}).catch((err: Error): void  => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to set code. Code is ${error.code}, message is ${error.message}`);
});
```

### setCodeSync<sup>10+</sup>

ArkTS-Dyn: setCodeSync(code: number): void

ArkTS-Sta: setCodeSync(code: int): void

ArkTS-Dyn: Sets the result code (number type) of an ordered common event. This API returns the result synchronously.

ArkTS-Sta: Sets the result code (int type) of an ordered common event. This API returns the result synchronously.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 10

**ArkTS-Sta start version:** 23

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| code   | ArkTS-Dyn: number<br/>ArkTS-Sta: int | Yes   | Code delivered by the ordered common event. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401      | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.                    |

**Example**

<!--code_no_check-->

```ts
try {
  subscriber.setCodeSync(1);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to set code. Code is ${err.code}, message is ${err.message}`);
}
```

### getData

getData(callback: AsyncCallback\<string>): void

Obtains the result data of an ordered common event. This API uses an asynchronous callback to return the result.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Parameters**

| Name  | Type                  | Mandatory| Description                |
| -------- | ---------------------- | ---- | -------------------- |
| callback | AsyncCallback\<string> | Yes | Callback used to return the result. If the result data (string type) of an ordered common event is successfully obtained, **err** is **undefined**, and **data** is the data obtained; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.      |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
// Obtain the result data (string type) of an ordered common event.
subscriber.getData((err: BusinessError, data: string) => {
  if (err) {
    console.error(`Failed to get data. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting data, data is ${JSON.stringify(data)}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
// Obtain the result data (string type) of an ordered common event.
subscriber.getData((err: BusinessError | null, data: string | undefined | null) => {
  if (err) {
    console.error(`Failed to get data. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting data, data is ${JSON.stringify(data)}`);
});
```

### getData

getData(): Promise\<string>

Obtains the result data of an ordered common event. This API uses a promise to return the result.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Return value**

| Type            | Description              |
| ---------------- | ------------------ |
| Promise\<string> | Promise used to return the result data (string type) of an ordered common event.|

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.getData().then((data: string) => {
  console.info(`Succeeded in getting data, data is ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get data. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.getData().then((data: string) => {
  console.info(`Succeeded in getting data, data is ${JSON.stringify(data)}`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get data. Code is ${error.code}, message is ${error.message}`);
});
```

### getDataSync<sup>10+</sup>

getDataSync(): string

Obtains the result data of an ordered common event. This API returns the result synchronously.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 10

**ArkTS-Sta start version:** 23

**Return value**

| Type            | Description              |
| ---------------- | ------------------ |
| string | Data delivered by the ordered common event. |

**Example**

<!--code_no_check-->

```ts
let data: string = subscriber.getDataSync();
console.info(`Succeeded in getting data, data is ${data}`);
```

### setData

setData(data: string, callback: AsyncCallback\<void>): void

Sets the data of an ordered common event. This API uses an asynchronous callback to return the result.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Parameters**

| Name  | Type                | Mandatory| Description                |
| -------- | -------------------- | ---- | -------------------- |
| data     | string               | Yes   | Data delivered by the ordered common event. The value is a string containing a maximum of 65,536 characters. If the length exceeds the limit, the API setting becomes invalid.   |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.      |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.setData('publish_data_changed', (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set data. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting data.`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.setData('publish_data_changed', (err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to set data. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting data.`);
});
```

### setData

setData(data: string): Promise\<void>

Sets the result data of an ordered common event. This API uses a promise to return the result.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| data   | string | Yes   | Data delivered by the ordered common event. The value is a string containing a maximum of 65,536 characters. If the length exceeds the limit, the API setting becomes invalid. |

**Return value**

| Type            | Description                |
| ---------------- | -------------------- |
| Promise\<void>   | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.      |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.setData('publish_data_changed').then(() => {
  console.info(`Succeeded in setting data.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set data. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.setData('publish_data_changed').then(() => {
  console.info(`Succeeded in setting data.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to set data. Code is ${error.code}, message is ${error.message}`);
});
```

### setDataSync<sup>10+</sup>

setDataSync(data: string): void

Sets the result data of an ordered common event. This API returns the result synchronously.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 10

**ArkTS-Sta start version:** 23

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| data | string | Yes | Data delivered by the ordered common event. The value is a string containing a maximum of 65,536 characters. If the length exceeds the limit, the API setting becomes invalid. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401      | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.                    |

**Example**

<!--code_no_check-->

```ts
try {
  subscriber.setDataSync('publish_data_changed');
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to set data. Code is ${err.code}, message is ${err.message}`);
}
```

### setCodeAndData

ArkTS-Dyn: setCodeAndData(code: number, data: string, callback:AsyncCallback\<void>): void

ArkTS-Sta: setCodeAndData(code: int, data: string, callback:AsyncCallback\<void>): void

Sets the code and data of an ordered common event. This API uses an asynchronous callback to return the result.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Parameters**

| Name  | Type                | Mandatory| Description                  |
| -------- | -------------------- | ---- | ---------------------- |
| code     | ArkTS-Dyn: number<br/>ArkTS-Sta: int | Yes   | Code delivered by the ordered common event.   |
| data     | string               | Yes   | Data delivered by the ordered common event. The value is a string containing a maximum of 65,536 characters. If the length exceeds the limit, the API setting becomes invalid.   |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.      |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.setCodeAndData(1, 'publish_data_changed', (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set code and data. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting code and data.`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.setCodeAndData(1, 'publish_data_changed', (err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to set code and data. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting code and data.`);
});
```

### setCodeAndData

ArkTS-Dyn: setCodeAndData(code: number, data: string): Promise\<void>

ArkTS-Sta: setCodeAndData(code: int, data: string): Promise\<void>

Sets the result code and data of an ordered common event. This API uses a promise to return the result.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| code   | ArkTS-Dyn: number<br/>ArkTS-Sta: int | Yes   | Code delivered by the ordered common event. |
| data   | string | Yes   | Data delivered by the ordered common event. The value is a string containing a maximum of 65,536 characters. If the length exceeds the limit, the API setting becomes invalid. |

**Return value**

| Type            | Description                |
| ---------------- | -------------------- |
| Promise\<void>   | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.      |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.setCodeAndData(1, 'publish_data_changed').then(() => {
  console.info(`Succeeded in setting code and data.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set code and data. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta example:

```ts
subscriber.setCodeAndData(1, 'publish_data_changed').then(() => {
  console.info(`Succeeded in setting code and data.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to set code and data. Code is ${error.code}, message is ${error.message}`);
});
```

### setCodeAndDataSync<sup>10+</sup>

ArkTS-Dyn: setCodeAndDataSync(code: number, data: string): void

ArkTS-Sta: setCodeAndDataSync(code: int, data: string): void

Sets the result code and data of an ordered common event. This API returns the result synchronously.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 10

**ArkTS-Sta start version:** 23

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| code   | ArkTS-Dyn: number<br/>ArkTS-Sta: int | Yes   | Code delivered by the ordered common event. |
| data   | string | Yes   | Data delivered by the ordered common event. The value is a string containing a maximum of 65,536 characters. If the length exceeds the limit, the API setting becomes invalid. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401      | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.                    |

**Example**

<!--code_no_check-->

```ts
try {
  subscriber.setCodeAndDataSync(1, 'publish_data_changed');
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to set code and data. Code is ${err.code}, message is ${err.message}`);
}

```

### isOrderedCommonEvent

isOrderedCommonEvent(callback: AsyncCallback\<boolean>): void

Checks whether the current common event is an ordered common event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Parameters**

| Name  | Type                   | Mandatory| Description                              |
| -------- | ----------------------- | ---- | ---------------------------------- |
| callback | AsyncCallback\<boolean> | Yes | Callback used to return the result. If the query is successful, **err** is **undefined**. If **data** is **true**, the common event is ordered; if **data** is **false**, the common event is not ordered. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.      |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.isOrderedCommonEvent((err: BusinessError, isOrdered: boolean) => {
  if (err) {
    console.error(`isOrderedCommonEvent failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`isOrderedCommonEvent ${JSON.stringify(isOrdered)}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.isOrderedCommonEvent((err: BusinessError | null, isOrdered: boolean | undefined | null) => {
  if (err) {
    console.error(`isOrderedCommonEvent failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`isOrderedCommonEvent ${JSON.stringify(isOrdered)}`);
});
```

### isOrderedCommonEvent

isOrderedCommonEvent(): Promise\<boolean>

Checks whether the current common event is an ordered common event. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Return value**

| Type             | Description                            |
| ----------------- | -------------------------------- |
| Promise\<boolean> | Promise used to return the result. Returns **true** if the common event is an ordered one; returns **false** if the common event is an unordered one.|

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.isOrderedCommonEvent().then((isOrdered: boolean) => {
  console.info(`isOrderedCommonEvent ${JSON.stringify(isOrdered)}`);
}).catch((err: BusinessError) => {
  console.error(`isOrderedCommonEvent failed, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.isOrderedCommonEvent().then((isOrdered: boolean) => {
  console.info(`isOrderedCommonEvent ${JSON.stringify(isOrdered)}`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`isOrderedCommonEvent failed, code is ${error.code}, message is ${error.message}`);
});
```

### isOrderedCommonEventSync<sup>10+</sup>

isOrderedCommonEventSync(): boolean

Checks whether a common event is an ordered common event. This API returns the result synchronously.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 10

**ArkTS-Sta start version:** 23

**Return value**

| Type             | Description                            |
| ----------------- | -------------------------------- |
| boolean |Returns **true** if the common event is an ordered one; returns **false** if the common event is an unordered one.|

**Example**

<!--code_no_check-->

```ts
let isOrdered: boolean = subscriber.isOrderedCommonEventSync();
console.info(`isOrderedCommonEventSync ${JSON.stringify(isOrdered)}`);
```

### isStickyCommonEvent

isStickyCommonEvent(callback: AsyncCallback\<boolean>): void

Checks whether the current common event is a sticky common event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Parameters**

| Name  | Type                   | Mandatory| Description                              |
| -------- | ----------------------- | ---- | ---------------------------------- |
| callback | AsyncCallback\<boolean> | Yes | Callback used to return the result. If the query is successful, **err** is **undefined**. If **data** is **true**, the common event is sticky; if **data** is **false**, the common event is not sticky. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.      |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.isStickyCommonEvent((err: BusinessError, isSticky: boolean) => {
  if (err) {
    console.error(`isStickyCommonEvent failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`isStickyCommonEvent ${JSON.stringify(isSticky)}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.isStickyCommonEvent((err: BusinessError | null, isSticky: boolean | undefined | null) => {
  if (err) {
    console.error(`isStickyCommonEvent failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`isStickyCommonEvent ${JSON.stringify(isSticky)}`);
});
```

### isStickyCommonEvent

isStickyCommonEvent(): Promise\<boolean>

Checks whether the current common event is a sticky common event. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Return value**

| Type             | Description                            |
| ----------------- | -------------------------------- |
| Promise\<boolean> | Promise used to return the result. Returns **true** if the common event is a sticky one; returns **false** otherwise.|

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.isStickyCommonEvent().then((isSticky: boolean) => {
  console.info(`isStickyCommonEvent ${JSON.stringify(isSticky)}`);
}).catch((err: BusinessError) => {
  console.error(`isStickyCommonEvent failed, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.isStickyCommonEvent().then((isSticky: boolean) => {
  console.info(`isStickyCommonEvent ${JSON.stringify(isSticky)}`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`isStickyCommonEvent failed, code is ${error.code}, message is ${error.message}`);
});
```

### isStickyCommonEventSync<sup>10+</sup>

isStickyCommonEventSync(): boolean

Checks whether the current common event is a sticky common event. This API returns the result synchronously.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 10

**ArkTS-Sta start version:** 23

**Return value**

| Type             | Description                            |
| ----------------- | -------------------------------- |
| boolean | Returns **true** if the common event is a sticky one; returns **false** otherwise.|

**Example**

<!--code_no_check-->

```ts
let isSticky: boolean = subscriber.isStickyCommonEventSync();
console.info(`isStickyCommonEventSync ${JSON.stringify(isSticky)}`);
```

### abortCommonEvent

abortCommonEvent(callback: AsyncCallback\<void>): void

Aborts an ordered common event. This API is used with [finishCommonEvent](#finishcommonevent9). After the abort, the common event is not sent to the next subscriber. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Parameters**

| Name  | Type                | Mandatory| Description                |
| -------- | -------------------- | ---- | -------------------- |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.      |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.abortCommonEvent((err: BusinessError) => {
  if (err) {
    console.error(`Failed to abort common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in aborting common event.`);
});
subscriber.finishCommonEvent((err: BusinessError) => {
  if (err) {
    console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in finishing common event.`);
});
```

ArkTS-Sta example:

```ts
subscriber.abortCommonEvent((err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to abort common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in aborting common event.`);
});
subscriber.finishCommonEvent((err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in finishing common event.`);
});
```

### abortCommonEvent

abortCommonEvent(): Promise\<void>

Aborts this ordered common event. This API is used with [finishCommonEvent](#finishcommonevent9). After the abort, the common event is not sent to the next subscriber. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Return value**

| Type            | Description                |
| ---------------- | -------------------- |
| Promise\<void>   | Promise that returns no value.|

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.abortCommonEvent().then(() => {
  console.info(`Succeeded in aborting common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to abort common event. Code is ${err.code}, message is ${err.message}`);
});
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.abortCommonEvent().then(() => {
  console.info(`Succeeded in aborting common event.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to abort common event. Code is ${error.code}, message is ${error.message}`);
});
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to finish common event. Code is ${error.code}, message is ${error.message}`);
});
```

### abortCommonEventSync<sup>10+</sup>

abortCommonEventSync(): void

Aborts an ordered common event when used with [finishCommonEvent](#finishcommonevent9). With the abort state, the common event is not sent to the next subscriber. This API returns the result synchronously.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 10

**ArkTS-Sta start version:** 23

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.abortCommonEventSync();
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.abortCommonEventSync();
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to finish common event. Code is ${error.code}, message is ${error.message}`);
});
```

### clearAbortCommonEvent

clearAbortCommonEvent(callback: AsyncCallback\<void>): void

Clears the abort state of an ordered common event. Use this API together with [finishCommonEvent](#finishcommonevent9), and the common event can be passed to the next subscriber. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Parameters**

| Name  | Type                | Mandatory| Description                |
| -------- | -------------------- | ---- | -------------------- |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.      |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.clearAbortCommonEvent((err: BusinessError) => {
  if (err) {
    console.error(`Failed to clear abort common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in clearing abort common event.`);
});
subscriber.finishCommonEvent((err: BusinessError) => {
  if (err) {
    console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in finishing common event.`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.clearAbortCommonEvent((err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to clear abort common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in clearing abort common event.`);
});
subscriber.finishCommonEvent((err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in finishing common event.`);
});
```

### clearAbortCommonEvent

clearAbortCommonEvent(): Promise\<void>

Clears the abort state of this ordered common event. Use this API together with [finishCommonEvent](#finishcommonevent9), and the common event can be passed to the next subscriber. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Return value**

| Type            | Description                |
| ---------------- | -------------------- |
| Promise\<void>   | Promise that returns no value.|

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.clearAbortCommonEvent().then(() => {
  console.info(`Succeeded in clearing abort common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to clear abort common event. Code is ${err.code}, message is ${err.message}`);
});
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.clearAbortCommonEvent().then(() => {
  console.info(`Succeeded in clearing abort common event.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to clear abort common event. Code is ${error.code}, message is ${error.message}`);
});
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: Error): void  => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to finish common event. Code is ${error.code}, message is ${error.message}`);
});
```

### clearAbortCommonEventSync<sup>10+</sup>

clearAbortCommonEventSync(): void

Clears the abort state of an ordered common event when used with [finishCommonEvent](#finishcommonevent9). After the clearance, the common event is sent to the next subscriber. This API returns the result synchronously.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 10

**ArkTS-Sta start version:** 23

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.clearAbortCommonEventSync();
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.clearAbortCommonEventSync();
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to finish common event. Code is ${error.code}, message is ${error.message}`);
});
```

### getAbortCommonEvent

getAbortCommonEvent(callback: AsyncCallback\<boolean>): void

Checks whether this ordered common event should be aborted. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Parameters**

| Name  | Type                   | Mandatory| Description                              |
| -------- | ----------------------- | ---- | ---------------------------------- |
| callback | AsyncCallback\<boolean> | Yes | Callback used to return the result. If the query is successful, **err** is **undefined** and **data** is **true** if the current ordered common event is in the abort state, or **false** if the current ordered common event is not in the abort state. If the operation fails, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.      |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.getAbortCommonEvent((err: BusinessError, abortEvent: boolean) => {
  if (err) {
    console.error(`Failed to get abort common event. Code is ${err.code}, message is ${err.message}`);
    return;
  } 
  console.info(`Succeeded in getting abort common event, abortEvent is ${JSON.stringify(abortEvent)}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.getAbortCommonEvent((err: BusinessError | null, abortEvent: boolean | undefined | null) => {
  if (err) {
    console.error(`Failed to get abort common event. Code is ${err.code}, message is ${err.message}`);
    return;
  } 
  console.info(`Succeeded in getting abort common event, abortEvent is ${JSON.stringify(abortEvent)}`);
});
```

### getAbortCommonEvent

getAbortCommonEvent(): Promise\<boolean>

Checks whether this ordered common event should be aborted. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Return value**

| Type             | Description                              |
| ----------------- | ---------------------------------- |
| Promise\<boolean> | Promise used to return the result. The **true** indicates that the ordered common event is in the abort state; the value **false** indicates otherwise. |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.getAbortCommonEvent().then((abortEvent: boolean) => {
  console.info(`Succeeded in getting abort common event, abortEvent is ${JSON.stringify(abortEvent)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get abort common event. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.getAbortCommonEvent().then((abortEvent: boolean) => {
  console.info(`Succeeded in getting abort common event, abortEvent is ${JSON.stringify(abortEvent)}`);
}).catch((err: Error): void  => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get abort common event. Code is ${error.code}, message is ${error.message}`);
});
```

### getAbortCommonEventSync<sup>10+</sup>

getAbortCommonEventSync(): boolean

Checks whether an ordered common event is aborted. This API returns the result synchronously.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 10

**ArkTS-Sta start version:** 23

**Return value**

| Type             | Description                              |
| ----------------- | ---------------------------------- |
| boolean | The value **true** indicates that the ordered common event is in the abort state; the value **false** indicates otherwise. |

**Example**

<!--code_no_check-->

```ts
let abortEvent: boolean = subscriber.getAbortCommonEventSync();
console.info(`Succeeded in getting abort common event, abortEvent is ${JSON.stringify(abortEvent)}`);
```

### getSubscribeInfo

getSubscribeInfo(callback: AsyncCallback\<CommonEventSubscribeInfo>): void

Obtains the subscriber information. This API uses an asynchronous callback to return the result.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Parameters**

| Name  | Type                                                        | Mandatory| Description                  |
| -------- | ------------------------------------------------------------ | ---- | ---------------------- |
| callback | AsyncCallback\<[CommonEventSubscribeInfo](./js-apis-inner-commonEvent-commonEventSubscribeInfo.md)> | Yes | Callback used to return the result. If the subscriber information is successfully obtained, **err** is **undefined** and **data** is the subscription information of the subscriber. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.      |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.getSubscribeInfo((err: BusinessError, subscribeInfo: commonEventManager.CommonEventSubscribeInfo) => {
  if (err) {
    console.error(`Failed to get subscribe info. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting subscribe info, subscribe info is ${JSON.stringify(subscribeInfo)}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.getSubscribeInfo((err: BusinessError | null, subscribeInfo: commonEventManager.CommonEventSubscribeInfo | undefined | null) => {
  if (err) {
    console.error(`Failed to get subscribe info. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting subscribe info, subscribe info is ${JSON.stringify(subscribeInfo)}`);
});
```

### getSubscribeInfo

ArkTS-Dyn: getSubscribeInfo(): Promise\<CommonEventSubscribeInfo>

ArkTS-Sta: getSubscribeInfo(): Promise\<CommonEventSubscribeInfo|null>

Obtains the subscriber information. This API uses a promise to return the result.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 7

**ArkTS-Sta start version:** 23

**Return value**

| Type                                                        | Description                  |
| ------------------------------------------------------------ | ---------------------- |
| ArkTS-Dyn: Promise\<[CommonEventSubscribeInfo](./js-apis-inner-commonEvent-commonEventSubscribeInfo.md)> <br>ArkTS-Sta: Promise\<[CommonEventSubscribeInfo](./js-apis-inner-commonEvent-commonEventSubscribeInfo.md)\|null> | Promise used to return the subscriber's subscription information. |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.getSubscribeInfo().then((subscribeInfo: commonEventManager.CommonEventSubscribeInfo) => {
  console.info(`Succeeded in getting subscribe info, subscribe info is ${JSON.stringify(subscribeInfo)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get subscribe info. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.getSubscribeInfo().then((subscribeInfo: commonEventManager.CommonEventSubscribeInfo | null) => {
  console.info(`Succeeded in getting subscribe info, subscribe info is ${JSON.stringify(subscribeInfo)}`);
}).catch((err: BusinessError): void => {
  console.error(`Failed to get subscribe info. Code is ${err.code}, message is ${err.message}`);
});
```

### getSubscribeInfoSync<sup>10+</sup>

ArkTS-Dyn: getSubscribeInfoSync(): CommonEventSubscribeInfo

ArkTS-Sta: getSubscribeInfoSync(): CommonEventSubscribeInfo|null

Obtains the subscriber information. This API returns the result synchronously.

**Atomic service API (ArkTS-Dyn only):** This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 10

**ArkTS-Sta start version:** 23

**Return value**

| Type                                                        | Description                  |
| ------------------------------------------------------------ | ---------------------- |
| ArkTS-Dyn: [CommonEventSubscribeInfo](./js-apis-inner-commonEvent-commonEventSubscribeInfo.md) <br>ArkTS-Sta: [CommonEventSubscribeInfo](./js-apis-inner-commonEvent-commonEventSubscribeInfo.md)\|null | Subscriber information. |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
let subscribeInfo1: commonEventManager.CommonEventSubscribeInfo = subscriber.getSubscribeInfoSync();
console.info(`Succeeded in getting subscribe info, subscribe info is ${JSON.stringify(subscribeInfo1)}`);
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
let getSubscribeInfo = subscriber.getSubscribeInfoSync();
console.info(`Succeeded in getting subscribe info, subscribe info is ${JSON.stringify(getSubscribeInfo)}`);
```

### finishCommonEvent<sup>9+</sup>

finishCommonEvent(callback: AsyncCallback\<void>): void

Finishes this ordered common event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 9

**ArkTS-Sta start version:** 23

**Parameters**

| Name  | Type                 | Mandatory| Description                             |
| -------- | -------------------- | ---- | -------------------------------- |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the subscriber successfully finishes this ordered common event, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed.      |

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.finishCommonEvent((err: BusinessError) => {
  if (err) {
    console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in finishing common event.`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.finishCommonEvent((err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in finishing common event.`);
});
```

### finishCommonEvent<sup>9+</sup>

finishCommonEvent(): Promise\<void>

Finishes this ordered common event. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 9

**ArkTS-Sta start version:** 23

**Return value**

| Type            | Description                |
| ---------------- | -------------------- |
| Promise\<void>   | Promise that returns no value.|

**Example**

ArkTS-Dyn example:

<!--code_no_check-->

```ts
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta example:

<!--code_no_check-->

```ts
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to finish common event. Code is ${error.code}, message is ${error.message}`);
});
```

## Converting CommonEventSubscriber Types Using @ohos.transfer

Uses an ArkTS-Sta **CommonEventSubscriber** object in ArkTS-Dyn.

**Example**

- In the ArkTS-Sta module, convert the ArkTS-Sta **CommonEventSubscriber** to the ArkTS-Dyn **CommonEventSubscriber** and pass it to the ArkTS-Dyn submodule **library**.

  ArkTS-Sta example:

  ```TypeScript
  'use static'
  import { transfer } from '@kit.ArkTS';
  import { CommonEventSubscriberStaticToDynamic } from 'library';
  import { commonEventManager, BusinessError } from '@kit.BasicServicesKit';

  let subscriber: commonEventManager.CommonEventSubscriber;
  let subscribeInfo: commonEventManager.CommonEventSubscribeInfo = {
    events: ['event']
  };
  try {
    subscriber = commonEventManager.createSubscriberSync(subscribeInfo);
    let dynamicHandler = transfer.transferDynamic(subscriber, 'CommonEventManager.CommonEventSubscriber');
    CommonEventSubscriberStaticToDynamic(dynamicHandler as commonEventManager.CommonEventSubscriber);
  } catch (err) {
    console.error('transferDynamic catch error:-----------' + err.message);
  }
  ```

- Export the dependency **CommonEventSubscriberStaticToDynamic** in the **library/src/index.ets** file.

  ```TypeScript
  export { CommonEventSubscriberStaticToDynamic } from './src/main/ets/components/MainPage';
  ```

- Create an ArkTS-Dyn submodule **library**, and provide a method for receiving the ArkTS-Dyn **CommonEventSubscriber** in the **library/src/main/ets/components** directory.

  ArkTS-Dyn example:

  ```TypeScript
  import { commonEventManager, BusinessError } from '@kit.BasicServicesKit';
  export function CommonEventSubscriberStaticToDynamic(subscriber_: commonEventManager.CommonEventSubscriber) {
    try {
      let subscriber: commonEventManager.CommonEventSubscriber = subscriber_ as commonEventManager.CommonEventSubscriber;
      let subscribeInfo = subscriber.getSubscribeInfoSync();
      console.info(`Succeeded in getting subscribe info, subscribe info is ${JSON.stringify(subscribeInfo)}`);
    } catch (err) {
      console.error('CommonEventSubscriberStaticToDynamic catch Error: ' + err.message);
    }
  }
  ```

Uses the ArkTS-Dyn **CommonEventSubscriber** object in ArkTS-Sta.

**Example**

- In the ArkTS-Dyn module, create an ArkTS-Dyn **CommonEventSubscriber** object and pass it to the ArkTS-Sta submodule **library**.

  ArkTS-Dyn example:

  ```TypeScript
  import { CommonEventSubscriberDynamicToStatic } from 'library';
  import { commonEventManager, BusinessError } from '@kit.BasicServicesKit';

  let dynamicSubscriber: commonEventManager.CommonEventSubscriber;
  let subscribeInfo: commonEventManager.CommonEventSubscribeInfo = {
    events: ['event']
  };
  try {
    dynamicSubscriber = commonEventManager.createSubscriberSync(subscribeInfo);
    CommonEventSubscriberDynamicToStatic(dynamicSubscriber);
  } catch (err) {
    console.error('transferDynamic catch error:' + err.message);
  }
  ```

- Export the dependency **CommonEventSubscriberDynamicToStatic** in the **library/src/index.ets** file.

  ```TypeScript
  export { CommonEventSubscriberDynamicToStatic } from './src/main/ets/components/MainPage';
  ```

- Create an ArkTS-Sta submodule **library**, and provide a method for receiving the ArkTS-Dyn **CommonEventSubscriber** in the **library/src/main/ets/components** directory.

  ArkTS-Sta example:

  ```TypeScript
  'use static'
  import { transfer } from '@kit.ArkTS';
  import { commonEventManager, BusinessError } from '@kit.BasicServicesKit';

  export function CommonEventSubscriberDynamicToStatic(dynObject: Object | undefined | null) :void {
    try {
      let staticSubscriber: commonEventManager.CommonEventSubscriber = transfer.transferStatic(dynObject, 'CommonEventManager.CommonEventSubscriber') as commonEventManager.CommonEventSubscriber;
      let subscribeInfo = staticSubscriber.getSubscribeInfoSync();
      console.info(`Succeeded in getting subscribe info, subscribe info is ${JSON.stringify(subscribeInfo)}`);
    } catch (err) {
        console.error('CommonEventSubscriberDynamicToStatic catch error:' + err.message);
    }
  }
  ```