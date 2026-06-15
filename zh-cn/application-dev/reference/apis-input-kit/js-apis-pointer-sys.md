# @ohos.multimodalInput.pointer (Mouse Pointer) (System API)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

The **pointer** module provides APIs to query and set pointer attributes.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.multimodalInput.pointer (Mouse Pointer)](js-apis-pointer.md).

## Modules to Import

```js
import { pointer } from '@kit.InputKit';
```

## pointer.setPointerSpeed

setPointerSpeed(speed: number, callback: AsyncCallback&lt;void&gt;): void

Sets the mouse pointer speed. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                       | Mandatory  | Description                                   |
| -------- | ------------------------- | ---- | ------------------------------------- |
| speed    | number                    | Yes   | Mouse pointer speed. The value ranges from **1** to **20**. The default value is **10**.  |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message         |
| -------- | ----------------- |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the mouse pointer speed.
            pointer.setPointerSpeed(5, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting pointer speed.`);
            });
          } catch (error) {
            console.error(`Failed to set pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setPointerSpeed

setPointerSpeed(speed: number): Promise&lt;void&gt;

Sets the mouse pointer speed. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| speed | number | Yes   | Mouse pointer speed. The value ranges from **1** to **20**. The default value is **10**.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message         |
| -------- | ----------------- |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the mouse pointer speed.
            pointer.setPointerSpeed(5).then(() => {
              console.info(`Succeeded in setting pointer speed.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setPointerSpeedSync<sup>10+</sup>

setPointerSpeedSync(speed: number): void

Sets the mouse pointer speed. This API returns the result synchronously.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| speed | number | Yes   | Mouse pointer speed. The value ranges from **1** to **20**. The default value is **10**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let speed = pointer.setPointerSpeedSync(5);
            console.info(`Succeeded in setting pointer speed.`);
          } catch (error) {
            console.error(`Failed to set pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getPointerSpeed

getPointerSpeed(callback: AsyncCallback&lt;number&gt;): void

Obtains the mouse pointer speed. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                         | Mandatory  | Description            |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback&lt;number&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **number** is the mouse pointer speed. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | Permission denied, non-system app called system api. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the mouse pointer speed.
            pointer.getPointerSpeed((error: BusinessError, speed: number) => {
              if (error) {
                console.error(`Failed to get pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting pointer speed, speed: ${JSON.stringify(speed)}.`);
            });
          } catch (error) {
            console.error(`Failed to get pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getPointerSpeed

getPointerSpeed(): Promise&lt;number&gt;

Obtains the mouse pointer speed. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| Promise&lt;number&gt; | Promise used to return the mouse pointer speed.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | Permission denied, non-system app called system api. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the mouse pointer speed.
            pointer.getPointerSpeed().then(speed => {
              console.info(`Succeeded in getting pointer speed, speed: ${JSON.stringify(speed)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getPointerSpeedSync<sup>10+</sup>

getPointerSpeedSync(): number

Obtains the mouse pointer speed. This API returns the result synchronously.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| number | Mouse pointer speed. The value ranges from 1 to 20. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let speed = pointer.getPointerSpeedSync();
            console.info(`Succeeded in getting pointer speed, speed: ${JSON.stringify(speed)}.`);
          } catch (error) {
            console.error(`Failed to get pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setHoverScrollState<sup>10+</sup>

setHoverScrollState(state: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets the mouse hover scrolling switch state. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                       | Mandatory  | Description                                   |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state    | boolean                    | Yes   | Status of the mouse hover scroll switch. The value **true** indicates that the switch is enabled, and the value **false** indicates the opposite. The default value is **true**.  |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the mouse hover scrolling switch state.
            pointer.setHoverScrollState(true, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting mouse hover scroll.`);
            });
          } catch (error) {
            console.error(`Failed to set mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setHoverScrollState<sup>10+</sup>

setHoverScrollState(state: boolean): Promise&lt;void&gt;

Sets the status of the mouse hover scroll switch. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean | Yes   | Status of the mouse hover scroll switch. The value **true** indicates that the switch is enabled, and the value **false** indicates the opposite. The default value is **true**.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the mouse hover scrolling switch state.
            pointer.setHoverScrollState(true).then(() => {
              console.info(`Succeeded in setting mouse hover scroll.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getHoverScrollState<sup>10+</sup>

getHoverScrollState(callback: AsyncCallback&lt;boolean&gt;): void

Obtains the mouse hover scrolling switch state. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                         | Mandatory  | Description            |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **true** (default) will be returned if the switch is enabled while false will be returned if the switch is disabled. If the operation fails, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the mouse hover scrolling switch state.
            pointer.getHoverScrollState((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`Failed to get mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting mouse hover scroll, state: ${JSON.stringify(state)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getHoverScrollState<sup>10+</sup>

getHoverScrollState(): Promise&lt;boolean&gt;

Obtains the status of the mouse hover scroll switch. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the mouse hover scrolling switch is enabled, and the value **false** indicates that the switch is disabled. The default value is **true**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the mouse hover scrolling switch state.
            pointer.getHoverScrollState().then((state: boolean) => {
              console.info(`Succeeded in getting mouse hover scroll, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setMousePrimaryButton<sup>10+</sup>

setMousePrimaryButton(primary: PrimaryButton, callback: AsyncCallback&lt;void&gt;): void

Sets the primary mouse button. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name   | Type                     | Mandatory | Description                                   |
| -------- | ------------------------- | ----  | ------------------------------------- |
| primary  | [PrimaryButton](js-apis-pointer.md#primarybutton10)   | Yes   | Type of the primary mouse button.  |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the primary mouse button.
            pointer.setMousePrimaryButton(pointer.PrimaryButton.RIGHT, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set mouse primary button, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting mouse primary button.`);
            });
          } catch (error) {
            console.error(`Failed to set mouse primary button, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setMousePrimaryButton<sup>10+</sup>

setMousePrimaryButton(primary: PrimaryButton): Promise&lt;void&gt;

Sets the primary mouse button. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| primary | [PrimaryButton](js-apis-pointer.md#primarybutton10) | Yes   | Type of the primary mouse button.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the primary mouse button.
            pointer.setMousePrimaryButton(pointer.PrimaryButton.RIGHT).then(() => {
              console.info(`Succeeded in setting mouse primary button.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set mouse primary button, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set mouse primary button, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getMousePrimaryButton<sup>10+</sup>

getMousePrimaryButton(callback: AsyncCallback&lt;PrimaryButton&gt;): void

Obtains the current primary mouse button. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                         | Mandatory  | Description            |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback&lt;[PrimaryButton](js-apis-pointer.md#primarybutton10)&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **PrimaryButton** is the obtained key value. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the primary mouse button.
            pointer.getMousePrimaryButton((error: BusinessError, primary: pointer.PrimaryButton) => {
              if (error) {
                console.error(`Failed to get mouse primary button, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting mouse primary button, primary: ${JSON.stringify(primary)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get mouse primary button, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getMousePrimaryButton<sup>10+</sup>

getMousePrimaryButton(): Promise&lt;PrimaryButton&gt;

Obtains the current primary mouse button. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| Promise&lt;[PrimaryButton](js-apis-pointer.md#primarybutton10)&gt; | Promise used to return the primary mouse button.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the primary mouse button.
            pointer.getMousePrimaryButton().then((primary: pointer.PrimaryButton) => {
              console.info(`Succeeded in getting mouse primary button, primary: ${JSON.stringify(primary)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get mouse primary button, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get mouse primary button, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setMouseScrollRows<sup>10+</sup>

setMouseScrollRows(rows: number, callback: AsyncCallback&lt;void&gt;): void

Sets the number of mouse scroll lines. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                       | Mandatory  | Description                                   |
| -------- | ------------------------- | ---- | ------------------------------------- |
| rows     | number                    | Yes   | Number of mouse scroll lines. The value ranges from 1 to 100. The default value is **3**.  |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the number of mouse scroll lines.
            pointer.setMouseScrollRows(1, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting mouse scroll rows.`);
            });
          } catch (error) {
            console.error(`Failed to set mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setMouseScrollRows<sup>10+</sup>

setMouseScrollRows(rows: number): Promise&lt;void&gt;

Sets the number of mouse scroll lines. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| rows  | number | Yes   | Number of mouse scroll lines. The value ranges from 1 to 100. The default value is **3**.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the number of mouse scroll lines.
            pointer.setMouseScrollRows(20).then(() => {
              console.info(`Succeeded in setting mouse scroll rows.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getMouseScrollRows<sup>10+</sup>

getMouseScrollRows(callback: AsyncCallback&lt;number&gt;): void

Obtains the number of mouse scroll lines. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                         | Mandatory  | Description            |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback&lt;number&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **number** is the number of mouse scroll lines. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the number of mouse scroll lines.
            pointer.getMouseScrollRows((error: BusinessError, rows: number) => {
              if (error) {
                console.error(`Failed to get mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting mouse scroll rows, rows: ${JSON.stringify(rows)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getMouseScrollRows<sup>10+</sup>

getMouseScrollRows(): Promise&lt;number&gt;

Obtains the number of mouse scroll lines. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| Promise&lt;number&gt; | Promise used to return the number of mouse scroll lines.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the number of mouse scroll lines.
            pointer.getMouseScrollRows().then((rows: number) => {
              console.info(`Succeeded in getting mouse scroll rows, rows: ${JSON.stringify(rows)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadScrollSwitch<sup>10+</sup>

setTouchpadScrollSwitch(state: boolean, callback: AsyncCallback\<void>): void

Sets the touchpad scroll switch. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                       | Mandatory  | Description                                   |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state | boolean | Yes   | Scroll switch status. The value **true** indicates that the switch is enabled, and the value **false** indicates the opposite. The default value is **true**.  |
| callback | AsyncCallback\<void> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the touchpad scroll switch state.
            pointer.setTouchpadScrollSwitch(true, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad scroll switch.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadScrollSwitch<sup>10+</sup>

setTouchpadScrollSwitch(state: boolean): Promise\<void>

Sets the touchpad scroll switch. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean| Yes   |  Scroll switch status. The value **true** indicates that the switch is enabled, and the value **false** indicates the opposite. The default value is **true**.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the touchpad scroll switch state.
            pointer.setTouchpadScrollSwitch(false).then(() => {
              console.info(`Succeeded in setting touchpad scroll switch.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadScrollSwitch<sup>10+</sup>

getTouchpadScrollSwitch(callback:  AsyncCallback\<boolean>): void

Obtains the touchpad scroll switch state. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                         | Mandatory  | Description            |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **state** indicates whether the scroll switch state (**true** indicates yes and **false** indicates no; default value: **true**). Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the touchpad scroll switch state.
            pointer.getTouchpadScrollSwitch((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`Failed to get touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting touchpad scroll switch, state: ${JSON.stringify(state)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadScrollSwitch<sup>10+</sup>

getTouchpadScrollSwitch(): Promise\<boolean>

Obtains the touchpad scroll switch state. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise used to return the result. The value **true** indicates that the touchpad scroll switch is enabled, and the value **false** indicates that the touchpad scroll is disabled. The default value is **true**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the touchpad scroll switch state.
            pointer.getTouchpadScrollSwitch().then((state) => {
              console.info(`Succeeded in getting touchpad scroll switch, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadScrollDirection<sup>10+</sup>

setTouchpadScrollDirection(state: boolean, callback: AsyncCallback\<void>): void

Sets the touchpad scroll direction. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                       | Mandatory  | Description                                   |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state | boolean | Yes   | Touchpad scroll direction.<br>The value **true** indicates that the scroll direction is the same as the finger moving direction, and the value **false** indicates the opposite.<br>The default value is **true**.  |
| callback | AsyncCallback\<void> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the touchpad scroll direction.
            pointer.setTouchpadScrollDirection(true, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad scroll direction.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadScrollDirection<sup>10+</sup>

setTouchpadScrollDirection(state: boolean): Promise\<void>

Sets the touchpad scroll direction. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean| Yes   |  Touchpad scroll direction.<br>The value **true** indicates that the scroll direction is the same as the finger moving direction, and the value **false** indicates the opposite.<br>The default value is **true**.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the touchpad scroll direction.
            pointer.setTouchpadScrollDirection (false).then(() => {
              console.info(`Succeeded in setting touchpad scroll direction.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadScrollDirection<sup>10+</sup>

getTouchpadScrollDirection(callback:  AsyncCallback\<boolean>): void

Obtains the touchpad scroll direction. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                         | Mandatory  | Description            |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **state** indicates whether the touchpad scroll direction matches the direction of finger movement (**true** indicates yes). Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the touchpad scroll direction.
            pointer.getTouchpadScrollDirection ((error: BusinessError, state: boolean) => {
              console.info(`Succeeded in getting touchpad scroll direction, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadScrollDirection<sup>10+</sup>

getTouchpadScrollDirection(): Promise\<boolean>

Obtains the scroll direction of the touchpad. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise used to return the result. The value **true** indicates that the touchpad scroll direction matches the direction of finger movement, and the value **false** indicates the opposite. The default value is **true**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the touchpad scroll direction.
            pointer.getTouchpadScrollDirection().then((state: boolean) => {
              console.info(`Succeeded in getting touchpad scroll direction, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadTapSwitch<sup>10+</sup>

setTouchpadTapSwitch(state: boolean, callback: AsyncCallback\<void>): void

Sets the touchpad tap switch. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                       | Mandatory  | Description                                   |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state | boolean | Yes   |Tap switch status of the touchpad The value **true** indicates that the switch is enabled, and the value **false** indicates the opposite. The default value is **true**.  |
| callback | AsyncCallback\<void> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the touchpad tap switch.
            pointer.setTouchpadTapSwitch(true, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad tap switch.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`); 
          }
        })
    }
  }
}
```

## pointer.setTouchpadTapSwitch <sup>10+</sup>

setTouchpadTapSwitch(state: boolean): Promise\<void>

Sets the touchpad tap switch. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean| Yes   |  State of the touchpad tap switch. The value **true** indicates that the switch is enabled, and the value **false** indicates the opposite. The default value is **true**. |

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the touchpad tap switch.
            pointer.setTouchpadTapSwitch(false).then(() => {
              console.info(`Succeeded in setting touchpad tap switch.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadTapSwitch<sup>10+</sup>

getTouchpadTapSwitch(callback:  AsyncCallback\<boolean>): void

Obtains the touchpad tap switch state. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                         | Mandatory  | Description            |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **state** indicates whether the touchpad tap switch is enabled (**true** indicates yes and **false** indicates no; default value: **true**). Otherwise, **err** is an error object.|
**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the touchpad tap switch state.
            pointer.getTouchpadTapSwitch((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`Failed to get touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting touchpad tap switch, state: ${JSON.stringify(state)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadTapSwitch<sup>10+</sup>

getTouchpadTapSwitch(): Promise\<boolean>

Obtains the touchpad tap switch state. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise used to return the result. The value **true** indicates that the touchpad tap switch is enabled, and the value **false** indicates that the touchpad tap switch is disabled. The default value is **true**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the touchpad tap switch state.
            pointer.getTouchpadTapSwitch().then((state: boolean) => {
              console.info(`Succeeded in getting touchpad tap switch, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadPointerSpeed<sup>10+</sup>

setTouchpadPointerSpeed(speed: number, callback: AsyncCallback\<void>): void

Sets the touchpad pointer speed. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                       | Mandatory  | Description                                   |
| -------- | ------------------------- | ---- | ------------------------------------- |
| speed | number                    | Yes   |Touchpad pointer speed The value range is [1,11]. The default value is **6**. |
| callback | AsyncCallback\<void> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the touchpad pointer speed.
            pointer.setTouchpadPointerSpeed(1, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad pointer speed.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadPointerSpeed<sup>10+</sup>

setTouchpadPointerSpeed(speed: number): Promise\<void>

Sets the touchpad pointer speed. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| speed| number | Yes   | Touchpad pointer speed The value range is [1,11]. The default value is **6**.   |

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the touchpad pointer speed.
            pointer.setTouchpadPointerSpeed(10).then(() => {
              console.info(`Succeeded in setting touchpad pointer speed.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadPointerSpeed<sup>10+</sup>

getTouchpadPointerSpeed(callback: AsyncCallback\<number>): void

Obtains the touchpad pointer speed. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                         | Mandatory  | Description            |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<number> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **number** is the obtained touchpad pointer speed. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the touchpad pointer speed.
            pointer.getTouchpadPointerSpeed((error: BusinessError, speed: number) => {
              if (error) {
                console.error(`Failed to get touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting touchpad pointer speed, speed: ${JSON.stringify(speed)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadPointerSpeed<sup>10+</sup>

getTouchpadPointerSpeed(): Promise\<number>

Obtains the touchpad pointer speed. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| Promise\<number> | Promise used to return the touchpad pointer speed. The value range is [1,11].|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the touchpad pointer speed.
            pointer.getTouchpadPointerSpeed().then((speed: number) => {
              console.info(`Succeeded in getting touchpad pointer speed, speed: ${JSON.stringify(speed)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadPinchSwitch<sup>10+</sup>

setTouchpadPinchSwitch(state: boolean, callback: AsyncCallback\<void>): void

Sets the touchpad pinch switch. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                       | Mandatory  | Description                                   |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state | boolean | Yes   |Touchpad pinch switch state. The value **true** indicates that the switch is enabled, and the value **false** indicates the opposite. The default value is **true**.  |
| callback | AsyncCallback\<void> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the touchpad pinch switch.
            pointer.setTouchpadPinchSwitch(true, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad pinch switch.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadPinchSwitch<sup>10+</sup>

setTouchpadPinchSwitch(state: boolean): Promise\<void>

Sets the touchpad pinch switch. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean| Yes   |  Touchpad pinch switch state. The value **true** indicates that the switch is enabled, and the value **false** indicates the opposite. The default value is **true**. |

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the touchpad pinch switch.
            pointer.setTouchpadPinchSwitch(false).then(() => {
              console.info(`Succeeded in setting touchpad pinch switch.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadPinchSwitch<sup>10+</sup>

getTouchpadPinchSwitch(callback:  AsyncCallback\<boolean>): void

Obtains the touchpad pinch switch state. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                         | Mandatory  | Description            |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **state** indicates whether the touchpad pinch switch is enabled (**true** indicates yes and **false** indicates no; default value: **true**). Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the touchpad pinch switch state.
            pointer.getTouchpadPinchSwitch((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`Failed to get touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting touchpad pinch switch, state: ${JSON.stringify(state)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadPinchSwitch<sup>10+</sup>

getTouchpadPinchSwitch(): Promise\<boolean>

Obtains the touchpad pinch switch state. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise used to return the result. The value **true** indicates that the touchpad pinch switch is enabled, and the value **false** indicates that the touchpad pinch switch is disabled. The default value is **true**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the touchpad pinch switch state.
            pointer.getTouchpadPinchSwitch().then((state: boolean) => {
              console.info(`Succeeded in getting touchpad pinch switch, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadSwipeSwitch<sup>10+</sup>

setTouchpadSwipeSwitch(state: boolean, callback: AsyncCallback\<void>): void

Sets the touchpad multi-finger swipe switch. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                       | Mandatory  | Description                                   |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state | boolean | Yes   |Touchpad multi-finger swipe switch state. The value **true** indicates that the switch is enabled, and the value **false** indicates the opposite. The default value is **true**.  |
| callback | AsyncCallback\<void> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the touchpad multi-finger swipe switch.
            pointer.setTouchpadSwipeSwitch(true, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad swipe switch.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadSwipeSwitch<sup>10+</sup>

setTouchpadSwipeSwitch(state: boolean): Promise\<void>

Sets the touchpad multi-finger swipe switch. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean| Yes   |  Touchpad multi-finger swipe switch state. The value **true** indicates that the switch is enabled, and the value **false** indicates the opposite. The default value is **true**. |

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the touchpad multi-finger swipe switch.
            pointer.setTouchpadSwipeSwitch(false).then(() => {
              console.info(`Succeeded in setting touchpad swipe switch.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadSwipeSwitch<sup>10+</sup>

getTouchpadSwipeSwitch(callback:  AsyncCallback\<boolean>): void

Obtains the touchpad multi-finger swipe switch state. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                         | Mandatory  | Description            |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **state** indicates whether the touchpad multi-finger swipe switch is enabled (**true** indicates yes and **false** indicates no; default value: **true**). Otherwise, **err** is an error object|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the touchpad multi-finger swipe switch state.
            pointer.getTouchpadSwipeSwitch((error: BusinessError, state: boolean) => {
              console.info(`Succeeded in getting touchpad swipe switch, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadSwipeSwitch<sup>10+</sup>

getTouchpadSwipeSwitch(): Promise\<boolean>

Obtains the touchpad multi-finger swipe switch state. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise used to return the result. The value **true** indicates that the touchpad multi-finger swipe switch is enabled, and **false** indicates that the touchpad multi-finger swipe switch is disabled. The default value is **true**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the touchpad multi-finger swipe switch state.
            pointer.getTouchpadSwipeSwitch().then((state: boolean) => {
              console.info(`Succeeded in getting touchpad swipe switch, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadRightClickType<sup>10+</sup>

setTouchpadRightClickType(type: RightClickType, callback: AsyncCallback\<void>): void

Sets the touchpad right-click menu type. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                       | Mandatory  | Description                                   |
| -------- | ------------------------- | ---- | ------------------------------------- |
| type| [RightClickType](js-apis-pointer.md#rightclicktype10)| Yes   |Touchpad right-click menu type.<br>- TOUCHPAD_RIGHT_BUTTON: Tapping the right-button area of the touchpad.<br>- TOUCHPAD_LEFT_BUTTON: Tapping the left-button area of the touchpad.<br>- TOUCHPAD_TWO_FINGER_TAP: Tapping or pressing the touchpad with two fingers.<br>- TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON<sup>20+</sup>: Tapping or pressing the touchpad with two fingers, or tapping the right-button area of the touchpad.<br>- TOUCHPAD_TWO_FINGER_TAP_OR_LEFT_BUTTON<sup>20+</sup>: Tapping or pressing the touchpad with two fingers, or tapping the left-button area of the touchpad.<br>The default value is **TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON**.|
| callback | AsyncCallback\<void> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the touchpad right-click menu type.
            pointer.setTouchpadRightClickType(pointer.RightClickType.TOUCHPAD_RIGHT_BUTTON , (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad right click type.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadRightClickType<sup>10+</sup>

setTouchpadRightClickType(type: RightClickType): Promise\<void>

Sets the touchpad right-click menu type. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                       | Mandatory  | Description                                   |
| -------- | ------------------------- | ---- | ------------------------------------- |
| type| [RightClickType](js-apis-pointer.md#rightclicktype10)| Yes   |Touchpad right-click menu type.<br>- TOUCHPAD_RIGHT_BUTTON: Tapping the right-button area of the touchpad.<br>- TOUCHPAD_LEFT_BUTTON: Tapping the left-button area of the touchpad.<br>- TOUCHPAD_TWO_FINGER_TAP: Tapping or pressing the touchpad with two fingers.<br>- TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON<sup>20+</sup>: Tapping or pressing the touchpad with two fingers, or tapping the right-button area of the touchpad.<br>- TOUCHPAD_TWO_FINGER_TAP_OR_LEFT_BUTTON<sup>20+</sup>: Tapping or pressing the touchpad with two fingers, or tapping the left-button area of the touchpad.<br>The default value is **TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON**.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the touchpad right-click menu type.
            pointer.setTouchpadRightClickType(pointer.RightClickType.TOUCHPAD_RIGHT_BUTTON).then(() => {
              console.info(`Succeeded in setting touchpad right click type.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadRightClickType<sup>10+</sup>

getTouchpadRightClickType(callback: AsyncCallback\<RightClickType>): void

Obtains the touchpad right-click menu type. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                         | Mandatory  | Description            |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<[RightClickType](js-apis-pointer.md#rightclicktype10)> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**, and the object is the touchpad right-click menu type. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the touchpad right-click menu type.
            pointer.getTouchpadRightClickType((error: BusinessError, type: pointer.RightClickType) => {
              console.info(`Succeeded in getting touchpad right click type, type: ${JSON.stringify(type)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadRightClickType<sup>10+</sup>

getTouchpadRightClickType(): Promise\<RightClickType>

Obtains the touchpad right-click menu type. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| Promise\<[RightClickType](js-apis-pointer.md#rightclicktype10) > | Promise used to return the touchpad right-click menu type.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the touchpad right-click menu type.
            pointer.getTouchpadRightClickType().then((type: pointer.RightClickType) => {
              console.info(`Succeeded in getting touchpad right click type, type: ${JSON.stringify(type)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setPointerSize<sup>10+</sup>

setPointerSize(size: number, callback: AsyncCallback&lt;void&gt;): void

Sets the mouse pointer size. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                       | Mandatory  | Description                                   |
| -------- | ------------------------- | ---- | ------------------------------------- |
| size     | number                    | Yes   | Pointer size. The value ranges from **1** to **7**. The default value is **1**.  |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the mouse pointer size.
            pointer.setPointerSize(1, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting pointer size.`);
            });
          } catch (error) {
            console.error(`Failed to set pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setPointerSize<sup>10+</sup>

setPointerSize(size: number): Promise&lt;void&gt;

Sets the mouse pointer size. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| size  | number | Yes   | Pointer size. The value ranges from **1** to **7**. The default value is **1**.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the mouse pointer size.
            pointer.setPointerSize(3).then(() => {
              console.info(`Succeeded in setting pointer size.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setPointerSizeSync<sup>10+</sup>

setPointerSizeSync(size: number): void

Sets the pointer size. This API returns the result synchronously.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| size  | number | Yes   | Pointer size. The value ranges from **1** to **7**. The default value is **1**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the mouse pointer size synchronously.
            pointer.setPointerSizeSync(5);
            console.info(`Succeeded in setting pointer size sync.`);
          } catch (error) {
            console.error(`Failed to set pointer size sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getPointerSize<sup>10+</sup>

getPointerSize(callback: AsyncCallback&lt;number&gt;): void

Obtains the current mouse pointer size. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                         | Mandatory  | Description            |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback&lt;number&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **number** is the obtained mouse pointer size (value range: [1-7]). Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the mouse pointer size.
            pointer.getPointerSize((error: BusinessError, size: number) => {
              if (error) {
                console.error(`Failed to get pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting pointer size, size: ${JSON.stringify(size)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getPointerSize<sup>10+</sup>

getPointerSize(): Promise&lt;number&gt;

Obtains the current mouse pointer size. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| Promise&lt;number&gt; | Promise used to return the mouse pointer size. The value ranges from 1 to 7.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |


**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the mouse pointer size.
            pointer.getPointerSize().then((size: number) => {
              console.info(`Succeeded in getting pointer size, size: ${JSON.stringify(size)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getPointerSizeSync<sup>10+</sup>

getPointerSizeSync(): number

Obtains the pointer size. This API returns the result synchronously.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| number | Mouse pointer size. The value ranges from **1** to **7**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |


**Example**

```js
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let pointerSize = pointer.getPointerSizeSync();
            console.info(`Succeeded in getting pointer size sync, pointerSize: ${JSON.stringify(pointerSize)}.`);
          } catch (error) {
            console.error(`Failed to get pointer size sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setPointerColor<sup>10+</sup>

setPointerColor(color: number, callback: AsyncCallback&lt;void&gt;): void

Sets the mouse pointer color. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> When performing this operation, you need to connect an external device, such as a mouse or Bluetooth device.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                       | Mandatory  | Description                                   |
| -------- | ------------------------- | ---- | ------------------------------------- |
| color     | number                    | Yes   | Pointer color. The default value is **black** (0x000000).  |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the mouse pointer color.
            pointer.setPointerColor(0xF6C800, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting pointer color.`);
            });
          } catch (error) {
            console.error(`Failed to set pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setPointerColor<sup>10+</sup>

setPointerColor(color: number): Promise&lt;void&gt;

Sets the mouse pointer color. This API uses a promise to return the result.

> **NOTE**
>
> When performing this operation, you need to connect an external device, such as a mouse or Bluetooth device.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| color  | number | Yes   | Pointer color. The default value is **black** (0x000000).|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the mouse pointer color.
            pointer.setPointerColor(0xF6C800).then(() => {
              console.info(`Succeeded in setting pointer color.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setPointerColorSync<sup>10+</sup>

setPointerColorSync(color: number): void

Sets the pointer color. This API returns the result synchronously.

> **NOTE**
>
> When performing this operation, you need to connect an external device, such as a mouse or Bluetooth device.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| color  | number | Yes   | Pointer color. The default value is **black** (0x000000).|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the mouse pointer color synchronously.
            pointer.setPointerColorSync(0xF6C800);
            console.info(`Succeeded in setting pointer color sync.`);
          } catch (error) {
            console.error(`Failed to set pointer color sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getPointerColor<sup>10+</sup>

getPointerColor(callback: AsyncCallback&lt;number&gt;): void

Obtains the mouse pointer color. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                         | Mandatory  | Description            |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback&lt;number&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **number** is the obtained mouse pointer color. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the mouse pointer color.
            pointer.getPointerColor((error: BusinessError, color: number) => {
              if (error) {
                console.error(`Failed to get pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting pointer color, color: ${JSON.stringify(color)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getPointerColor<sup>10+</sup>

getPointerColor(): Promise&lt;number&gt;

Obtains the current mouse pointer color. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| Promise&lt;number&gt; | Promise used to return the mouse pointer color.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |


**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the mouse pointer color.
            pointer.getPointerColor().then((color: number) => {
              console.info(`Succeeded in getting pointer color, color: ${JSON.stringify(color)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getPointerColorSync<sup>10+</sup>

getPointerColorSync(): number

Obtains the pointer color. This API returns the result synchronously.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| number | Pointer color.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |


**Example**

```js
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let pointerColor = pointer.getPointerColorSync();
            console.info(`Succeeded in getting pointer color sync, pointerColor: ${JSON.stringify(pointerColor)}.`);
          } catch (error) {
            console.error(`Failed to get pointer color sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadDoubleTapAndDragState<sup>14+</sup>

setTouchpadDoubleTapAndDragState(isOpen: boolean, callback: AsyncCallback\<void>): void

Sets the touchpad double-tap and drag switch state. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                       | Mandatory  | Description                                   |
| -------- | ------------------------- | ---- | ------------------------------------- |
| isOpen | boolean | Yes   | State of the double-tap and drag switch. The value **true** indicates that the switch is enabled, and the value **false** indicates the opposite.|
| callback | AsyncCallback\<void> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the touchpad double-tap and drag switch state.
            pointer.setTouchpadDoubleTapAndDragState(true, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad double tap and drag state.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadDoubleTapAndDragState<sup>14+</sup>

setTouchpadDoubleTapAndDragState(isOpen: boolean): Promise\<void>

Sets the touchpad double-tap and drag switch state. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| isOpen | boolean | Yes   | State of the double-tap and drag switch. The value **true** indicates that the switch is enabled, and the value **false** indicates the opposite.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the touchpad double-tap and drag switch state.
            pointer.setTouchpadDoubleTapAndDragState(false).then(() => {
              console.info(`Succeeded in setting touchpad double tap and drag state.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadDoubleTapAndDragState<sup>14+</sup>

getTouchpadDoubleTapAndDragState(callback: AsyncCallback\<boolean>): void

Obtains the touchpad double-tap and drag switch state. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name      | Type                         | Mandatory  | Description            |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **true** is returned if the switch is enabled while **false** is returned if the switch is disabled. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the touchpad double-tap and drag switch state.
            pointer.getTouchpadDoubleTapAndDragState((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`Failed to get touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting touchpad double tap and drag state, state: ${JSON.stringify(state)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadDoubleTapAndDragState<sup>14+</sup>

getTouchpadDoubleTapAndDragState(): Promise\<boolean>

Obtains the touchpad double-tap and drag switch state. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise used to return the result. The value **true** indicates that the touchpad double-tap and drag switch is enabled, and the value **false** indicates that the touchpad double-tap and drag switch is disabled.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the touchpad double-tap and drag switch state.
            pointer.getTouchpadDoubleTapAndDragState().then((state) => {
              console.info(`Succeeded in getting touchpad double tap and drag state, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setMouseScrollDirection<sup>24+</sup>

setMouseScrollDirection(inverted: boolean): Promise\<void>

Sets the scroll direction of the mouse wheel. This API uses a promise to return the result asynchronously.

**Required permissions**: ohos.permission.INPUT_DEVICE_CONTROLLER

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Parameters**

| Name| Type   | Mandatory| Description                                                                                                        |
| ------ | ------- | ---- | ------------------------------------------------------------------------------------------------------------ |
| inverted  | boolean | Yes  | Scroll direction of the mouse wheel.<br>The value **true** indicates that scroll direction matches the finger movement on the wheel, and the value **false** indicates that the scroll direction is opposite to the finger movement.<br>The default value is **true**.|

**Return value**

| Type          | Description                                  |
| -------------- | -------------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Mouse Pointer Error Codes](./errorcode-pointer.md).

| ID  | Error Message                       |
|---------|-----------------------------|
| 201     | Permission denied.          |
| 202     | SystemAPI permission error. |
| 3800001 | Input service exception.    |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button("setMouseScrollDirection")
        .onClick(() => {
          try {
            // Set the mouse scroll direction.
            pointer.setMouseScrollDirection(false).then(() => {
              console.info(`Succeeded in setting mouse scroll direction.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getMouseScrollDirection<sup>24+</sup>

getMouseScrollDirection(): Promise\<boolean>

Obtains the scroll direction of the mouse wheel. This API uses a promise to return the result asynchronously.

**Required permissions**: ohos.permission.INPUT_DEVICE_CONTROLLER

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

**System API**: This is a system API.

**Return value**

| Type             | Description                                                                                                                        |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Promise\<boolean> | Promise used to return the result. The value **true** indicates that the mouse wheel scroll direction is the same as the finger direction, and the value **false** indicates that the mouse wheel scroll direction is opposite to the finger direction. The default value is **true**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Mouse Pointer Error Codes](./errorcode-pointer.md).

| ID  | Error Message                                                                                                                                      |
|---------| ---------------------------------------------------------------------------------------------------------------------------------------------- |
| 201     | Permission denied.          |
| 202     | SystemAPI permission error. |
| 3800001 | Input service exception.    |

**Example**

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button("getMouseScrollDirection")
        .onClick(() => {
          try {
            // Obtain the mouse scroll direction.
            pointer.getMouseScrollDirection().then((state: boolean) => {
              console.info(`Succeeded in getting mouse scroll direction, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
