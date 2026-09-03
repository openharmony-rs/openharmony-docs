# @ohos.accessibility.GesturePoint (Gesture Point)

<!--Kit: Accessibility Kit-->
<!--Subsystem: BarrierFree-->
<!--Owner: @qiiiiiiian-->
<!--Designer: @z7o-->
<!--Tester: @A_qqq-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=16a51cad246d07c6caba5c76444e9d073c5d43d6 translatedAt=2026-08-03T09:33:41.469Z pushedAt=2026-08-03T12:35:30.436Z -->

GesturePoint represents a gesture touch point and is the basic unit that constitutes a gesture path (GesturePath).

This module is used to create touch point information for gesture paths, for use by accessibility applications to inject gestures.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { GesturePoint } from '@kit.AccessibilityKit';
```

## GesturePoint

Represents a gesture touch point, which is the basic unit that constitutes a GesturePath node and is used to define the touch position in the gesture trajectory for accessibility gesture injection. For details about how to use it, see [GesturePath](js-apis-accessibility-GesturePath.md).

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

### Attributes

| Name       | Type  | Read-Only  | Optional  | Description     |
| --------- | ------ | ---- | ---- | ------- |
| positionX | number | No   | No   | X coordinate of the touch point, in pixels (px).|
| positionY | number | No   | No   | Y coordinate of the touch point, in pixels (px).|

### constructor<sup>(deprecated)</sup>

constructor(positionX: number, positionY: number)

Creates a **GesturePoint** instance based on the given X and Y coordinates.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| positionX | number | Yes| X coordinate of the touch point, in pixels (px).|
| positionY | number | Yes | Y coordinate of the touch point, in pixels (px).|

**Example**

```ts
import { GesturePoint } from '@kit.AccessibilityKit';

let gesturePoint = new GesturePoint(1, 2);
```