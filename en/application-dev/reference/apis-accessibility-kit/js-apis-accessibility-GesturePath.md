# @ohos.accessibility.GesturePath (Gesture Path)

<!--Kit: Accessibility Kit-->
<!--Subsystem: BarrierFree-->
<!--Owner: @qiiiiiiian-->
<!--Designer: @z7o-->
<!--Tester: @A_qqq-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=16a51cad246d07c6caba5c76444e9d073c5d43d6 translatedAt=2026-08-03T09:33:35.975Z pushedAt=2026-08-03T12:29:49.155Z -->

GesturePath represents gesture path information.

This module is used to create gesture path information for accessibility gesture injection.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { GesturePath } from '@kit.AccessibilityKit';
```

## GesturePath

Represents gesture path information, used to simulate user touch gestures (such as tap, swipe, etc.) in accessibility services.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

### Properties

| Name         | Type                                                                          | Read Only | Optional | Description     |
| ------------ |---------------------------------------------------------------------------------| ---- | ---- | ------ |
| points       | Array&lt;[GesturePoint](js-apis-accessibility-GesturePoint.md#gesturepoint)&gt; | No    | No    | Sequence of touch points on the gesture path, used to form the movement trajectory of the gesture. Each touch point represents a coordinate position on the path. The array length must be greater than 0.    |
| durationTime | number                                                                          | No    | No    | Total gesture duration, in ms. The value must be greater than 0. |

### constructor<sup>(deprecated)</sup>

constructor(durationTime: number)

Creates a gesture path object by passing in the total gesture duration. After creating a GesturePath instance, you must also set the required property points.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| durationTime | number | Yes | Total gesture duration, in ms. The value must be greater than 0. |

**Example**

```ts
import { GesturePath, GesturePoint } from '@kit.AccessibilityKit';

let gesturePath = new GesturePath(20);
let startPoint = new GesturePoint(100, 100);
let endPoint = new GesturePoint(200, 200);
gesturePath.points = [startPoint, endPoint];
```