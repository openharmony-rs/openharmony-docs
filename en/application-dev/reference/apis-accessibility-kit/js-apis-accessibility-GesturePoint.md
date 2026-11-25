# @ohos.accessibility.GesturePoint (Gesture Point)

<!--Kit: Accessibility Kit-->
<!--Subsystem: BarrierFree-->
<!--Owner: @fanzexuan-->
<!--Designer: @z7o-->
<!--Tester: @A_qqq-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=b3705e4afba37476aadaf9a1df5606a3fb890cb1 translatedAt=2026-11-06T08:11:22.323Z pushedAt=2026-11-09T12:46:15.733Z nl=1 -->

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
