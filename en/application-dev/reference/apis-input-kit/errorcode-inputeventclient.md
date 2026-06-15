# Input Event Injection Error Codes

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=574e1b97c419a831e3ff5b620b1254fe667a5306 translatedAt=2026-06-12T02:21:14.313Z pushedAt=2026-06-12T06:19:44.440Z -->

> **NOTE**
>
> The following describes only the error codes specific to this module. For general error codes, refer to [General Error Codes](../errorcode-universal.md).

## 3800001 Input Service Exception

**Error Message**

Input service exception.

**Error Description**

This error code is generated when an exception occurs inside the input service while calling input event injection related interfaces.

**Possible Cause**

1. Memory allocation failure.
2. Thread busy.
3. The service is running abnormally.
4. Other unexpected errors.

**Solution**

It is recommended to try again later. If the problem persists, check the system resource usage.

## 4300001 Status Error

**Error Message**

Status error. The specific situation varies depending on the interface and scenario.

**Error Description**

This error code indicates different status errors in different interfaces:

- **pressKey interface**: The key is already pressed and is not the most recently pressed key, or the number of pressed keys exceeds 5.

  When calling the pressKey interface of the keyboard controller, this error code is generated if the key is already pressed and is not the most recently pressed key, or if the number of pressed keys exceeds 5.

  **Possible Cause**: The key is already pressed and is not the most recently pressed key, or the number of pressed keys exceeds 5.

  **Solution**: Ensure that the key is in the released state before it can be pressed; if the key is already pressed, ensure it is the most recently pressed key; ensure that the number of simultaneously pressed keys does not exceed 5.

- **releaseKey Interface**: The key is not pressed.

  When calling the releaseKey interface of the keyboard controller, this error code is generated if the key is not pressed.

  **Possible Cause**: Attempting to release a key that is not pressed.

  **Solution**: Ensure that only keys that are already pressed are released.

- **pressButton API**: The mouse button is already pressed.

  This error code is generated when the pressButton API of the mouse controller is called while the mouse button is already pressed.

  **Possible Cause**: The mouse button is already in the pressed state.

  **Solution**: Ensure that the mouse button is in the released state before it can be pressed.

- **releaseButton API**: The mouse button is not pressed.

  When calling the releaseButton API of the mouse controller, this error code is generated if the mouse button is not pressed.

  **Possible Cause**: Attempting to release a mouse button that is not pressed.

  **Solution**: Ensure that only mouse buttons that are already pressed are released.

- **beginAxis API**: The axis event is in progress.

  When calling the beginAxis API of the mouse controller, this error code is generated if an axis event is already in progress.

  **Possible Cause**: An axis event sequence is already in progress and has not yet ended.

  **Solution**: Ensure that the current axis event sequence is ended before starting a new one.

- **updateAxis/endAxis API**: The axis event is not in progress.

This error code is generated when the updateAxis or endAxis interface of the mouse controller is called while no axis event is in progress.

**Possible Cause**: An attempt was made to update or end an axis event sequence that has not been started.

**Solution**: Ensure that beginAxis is called to start an axis event sequence before calling updateAxis or endAxis.

- **touchDown interface**: The touch point is already touching the screen, or the touch point ID is not within the valid range [0, 9].

This error code is generated when the touchDown interface of the touch controller is called while the touch point is already touching the screen or the touch point ID is not within the valid range [0, 9].

**Possible Cause**: The touch point is already in the pressed state, or the touch point ID is not within the valid range [0, 9].

**Solution**: Before calling touchDown, ensure that the corresponding touch point is not already touching the screen and that the touch point ID is within the valid range [0, 9].

- **touchMove/touchUp APIs**: The touch point is not touching the screen, or the touch point ID is not within the valid range [0, 9].

When calling the touchMove or touchUp API of the touch controller, this error code is generated if the touch point is not touching the screen or the touch point ID is not within the valid range [0, 9].

**Possible Cause**: The touch point is not in the pressed state, or the touch point ID is not within the valid range [0, 9].

  **Solution**: Before calling touchMove or touchUp, call touchDown first to make the corresponding touch point contact the screen, and ensure the touch point ID is within the valid range [0, 9].
## 4300002 Display Does Not Exist

**Error Message**

The display does not exist.

**Error Description**

This error code is generated when the specified display does not exist when calling the moveTo API of the mouse controller or the touchDown API of the touch controller.

**Possible Cause**

The display corresponding to the specified displayId does not exist.

**Solution**

Use a valid display ID. You can query the list of available displays through the display management API.