# Input Event Injection Error Codes

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 3800001 Input Service Error

**Error Message**

Input service exception.

**Description**

This error code is generated if an internal error occurs in the input service when an input event injection API is called.

**Possible Causes**

1. Memory allocation failed.
2. The thread is busy.
3. The service runs abnormally.
4. Other unexpected errors.

**Solution**

Try again later. If the fault persists, check the system resource usage.

## 4300001 Status Error

**Error Message**

Status error, which indicates different situations in different APIs and scenarios.

**Description**

This error code indicates different status errors in different APIs:

- **pressKey API**: The key is already pressed and is not the most recently pressed key, or the number of pressed keys exceeds 5.

  This error code is generated when the **pressKey** API of the keyboard controller is called and the key has been pressed but is not the most recently pressed key, or more than five keys have been pressed.

  **Possible Causes**: The key has been pressed but is not the most recently pressed key, or more than five keys have been pressed.

  **Solution**: Ensure that a key can only be pressed when it is in the released state. If a key is already pressed, ensure that it is the most recently pressed key. Ensure that the number of keys pressed simultaneously does not exceed five.

- **releaseKey API**: The key is not pressed.

  This error code is generated when the **releaseKey** API of the keyboard controller is called and the key is not pressed.

  **Possible Causes**: An attempt is made to release a key that is not pressed.

  **Solution**: Ensure that the key to be released is pressed.

- **pressButton API**: The mouse button is already pressed.

  This error code is generated when the **pressButton** API of the mouse controller is called and the mouse button has been pressed.

  **Possible Causes**: The mouse button has been pressed.

  **Solution**: Ensure that the mouse button is in the released state.

- **releaseButton API**: The mouse button is not pressed.

  This error code is generated when the **releaseButton** API of the mouse controller is called and the mouse button is not pressed.

  **Possible Causes**: An attempt is made to release a mouse button that is not pressed.

  **Solution**: Ensure that the mouse button to be released is pressed.

- **beginAxis API**: The axis event is in progress.

  This error code is generated when the **beginAxis** API of the mouse controller is called and an axis event is in progress.

  **Possible Causes**: An axis event sequence is in progress and has not ended.

  **Solution**: Ensure that the ongoing axis event sequence is ended before a new one is started.

- **updateAxis/endAxis API**: The axis event is not in progress.

  This error code is generated when the **updateAxis** or **endAxis API** of the mouse controller is called and no axis event is in progress.

  **Possible Causes**: An attempt is made to update or end an axis event sequence that has not started.

  **Solution**: Ensure that **beginAxis** is called to start an axis event sequence before calling **updateAxis** or **endAxis**.

- **touchDown API**: The touch point is contacting the screen, or the touch point ID is not within the valid range [0, 9].

  This error code is generated when the **touchDown** API of the touch controller is called and the touch point is contacting the screen or the touch point ID is not within the valid range [0, 9].

  **Possible Causes**: The touch point is already in the pressed state, or the touch point ID is not within the valid range [0, 9].

  **Solution**: Before calling the **touchDown** API, ensure that the corresponding touch point is not yet touching the screen and that the touch point ID is within the valid range [0, 9].

- **touchMove/touchUp API**: The touch point is not yet touching the screen, or the touch point ID is not within the valid range [0, 9].

  This error code is generated when the **touchMove** or **touchUp** API of the touch controller is called and the touch point is not yet touching the screen or the touch point ID is not within the valid range [0, 9].

  **Possible Causes**: The touch point is not in the pressed state, or the touch point ID is not within the valid range [0, 9].

  **Solution**: Before calling the **touchMove** or **touchUp** API, call the **touchDown** API to make the touch point touch the screen and ensure that the touch point ID is within the valid range [0, 9].
## 4300002 Display Does Not Exist

**Error Message**

The display does not exist.

**Description**

This error code is generated when the **moveTo** API of the mouse controller or the **touchDown** API of the touch controller is called and the specified display does not exist.

**Possible Causes**

The display corresponding to the specified display ID does not exist.

**Solution**

Use a valid display ID. You can query the list of available displays through the display management API.
