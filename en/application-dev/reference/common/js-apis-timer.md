# Timer
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @yao_dashuai-->
<!--Designer: @yao_dashuai-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @foryourself-->

The Timer module provides basic timer capabilities. You can use the APIs of this module to execute functions at the specified time.

> **NOTE**
>
> The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> When a timer is used on the UI, the timer triggering mechanism is controlled by the underlying principles of the UI. If the UI is switched to the background, the timer will be frozen.

## setTimeout

setTimeout(handler: Function | string, delay?: number, ...arguments: any[]): number

Sets a timer for the system to call a function after the timer goes off. 
The timer is automatically deleted after the callback is executed, or you can manually delete the timer by calling clearTimeout().

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| handler | Function \| string | Yes| Function to be executed after the timer expires.<br>If the value is a string, the string content is printed in error mode and no other processing is performed.|
| delay | number | No| Number of milliseconds delayed before the execution. You are advised to pass an integer. If a decimal is passed, it will be rounded down.<br>If this parameter is omitted, the default value 0 is used.<br>**NOTE**<br>1. This timer is not a precise timer. The actual delay may be different from the expected delay.<br>2. If a value less than 1 is passed, the default value 0 is used.<br>3. The delay value is restricted by the system. If the value exceeds 2^32 - 1, the delay value overflows and the delay value is 0.|
| ...arguments | any[] | No| Additional parameter, which is passed to the handler only when the handler type is Function.<br>If the number of arguments is less than that of handler parameters, the parameters not covered by arguments are set to undefined.<br>If the number of arguments is greater than that of handler parameters, the extra arguments are ignored. However, you can access the extra arguments through the arguments object in the handler function.|

**Return value**

| Type| Description|
| -------- | -------- |
| number | ID of the timer. The timer ID is shared by processes and is an integer starting from 0 in ascending order.|

**Example 1**: no parameter is passed.

  ```ts
  setTimeout(() => {
    console.info('delay 1s');
  }, 1000);
  ```

**Example 2**: Parameters are passed to the function (the number of parameters is the same as that of arguments when handler is a function).

  ```ts
  function myFunction(param1: string, param2: string) {
    console.info(param1, param2);
  }
  setTimeout(myFunction, 1000, 'Hello', 'World');
  ```

**Example 3**: Parameters are passed to the function (the number of parameters is less than that of arguments when handler is a function).

  ```ts
  function myFunction(a: string, b: string) {
    console.info(a);
    // Output: hello
    console.info(b);
    // Output: world
    console.info(JSON.stringify(arguments));
    // Output: {"0":"hello","1":"world","2":"c++","3":"js"}
  }
  setTimeout(myFunction, 1000, 'hello', 'world', 'C++', 'js');
  ```
**Example 4**: Parameters are passed to the function (the number of parameters is greater than that of arguments when handler is a function).

  ```ts
  function myFunction(a: string, b: string) {
    console.info(a);
    // Output: hello
    console.info(b);
    // Output: undefined
    console.info(JSON.stringify(arguments));
    // Output: {"0":"hello"}
  }
  setTimeout(myFunction, 1000, 'hello');
  ```

## clearTimeout

clearTimeout(timeoutID?: number): void

Cancels a timer set via **setTimeout()**.

The timer object is stored in the thread that creates it. You need to delete the timer in the thread.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| timeoutID | number | No| ID of the timer to be canceled. The value must be the same as the return value of setTimeout(). If this parameter is omitted or the specified timer ID does not exist, no timer task is canceled.|

**Example**

  ```js
  let timeoutID = setTimeout(() => {
    console.info('do after 1s delay.');
  }, 1000);
  clearTimeout(timeoutID);
  ```


## setInterval

setInterval(handler: Function | string, delay: number, ...arguments: any[]): number

Sets a repeating timer for the system to repeatedly call a function at a fixed interval.
The timer can only be manually deleted by calling the **clearInterval** API.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| handler | Function \| string | Yes| Function function to be executed after the timer expires.<br>If the value is a string, the content of the string is printed in error mode and no other processing is performed.|
| delay | number | No| Number of milliseconds delayed before the execution. It is recommended that an integer be passed. If a decimal is passed, the decimal is rounded down.<br>If this parameter is omitted, the default value 0 is used.<br>**NOTE**<br>1. This timer is not a precise timer. The actual delay may be different from the expected delay.<br>2. If the value is less than 1, the value is set to 0 by default.<br>3. The delay value is restricted by the system. If the delay value exceeds 2^32 – 1, the delay value overflows and is set to 0.|
| ...arguments | any[] | No| Additional parameter, which takes effect only when handler is set to Function. It is passed to handler as a parameter.<br>If the number of arguments is less than the number of handler function parameters, the parameters that are not covered by arguments are set to undefined.<br>If the number of arguments is greater than the number of handler function parameters, the extra arguments are ignored. However, the extra arguments can be accessed through the arguments object in the handler function.|

**Return value**

| Type| Description|
| -------- | -------- |
| number | ID of the timer. The timer ID is shared by processes and is an integer starting from 0 in ascending order.|

**Example**

  ```js
  setInterval(() => {
    console.info('do every 1s.');
  }, 1000);
  ```


## clearInterval

clearInterval(intervalID?: number): void

Cancels the repeating timer set via **setInterval()**.

The timer object is stored in the thread that creates it. The timer needs to be deleted in the thread.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| intervalID | number | No| ID of the repeated timer to be canceled. The value must be the same as the return value of setInterval. If this parameter is omitted or the specified repeated timer ID does not exist, no timer task is canceled.|

**Example**

  ```js
  let intervalID = setInterval(() => {
    console.info('do every 1s.');
  }, 1000);
  clearInterval(intervalID);
  ```

## Other Description
### Timeout Delay
If the page is busy with other tasks, the timeout may be later than expected. The function or code snippet of setTimeout is executed in the next time period. Example:
  ```ts
  function foo() {
    console.info('OH test foo is called')
  }
  setTimeout(foo, 0);
  console.info('After OH test setTimeout')

  // output
  After OH test setTimeout
  OH test foo is called
  ```
This is because setTimeout() sets a delay of 0 ms, but the task is not executed immediately. Instead, it is placed in the queue and waits for the next event loop. The function in the queue is executed only after the current code is executed. Therefore, the final execution sequence may be different from the expected one.

### Maximum Delay
The timer uses a 32-bit signed integer to store the delay. Therefore, when the delay exceeds 2147483647 ms (about 24.8 days), the timer overflows and is executed immediately.

### Timer Suspension
The timer triggering mechanism is controlled by the bottom-layer task scheduling. After the current application is switched to the background, the timer does not trigger when it expires. Once the application is restored to the foreground, the expired timers will be triggered in sequence. You can use trace to check whether the process is still scheduled. If no scheduling is performed, the timer is frozen.
### Timer ID
setTimeout() and setInterval() use the same ID pool. Therefore, clearTimeout() and clearInterval() can be called to clear the timer. However, to improve the readability and maintainability of the code, you are advised to use the corresponding clearing methods to avoid confusion.
