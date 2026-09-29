# Matrix4

```TypeScript
export type Matrix4 = [
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number
]
```

Sets a 4 x 4 matrix.

This type is a 4 x 4 matrix represented by `number[]` of length 16, which is used to set transformation information for components. The following is an example:  
```
const transform: Matrix4 = [
1, 0, 45, 0,
0, 1, 0, 0,
0, 0, 1, 0,
0, 0, 0, 1
]
```.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-unnamed-export type Matrix4 = [  number,  number,  number,  number,  number,  number,  number,  number,  number,  number,  number,  number,  number,  number,  number,  number]--><!--Device-unnamed-export type Matrix4 = [  number,  number,  number,  number,  number,  number,  number,  number,  number,  number,  number,  number,  number,  number,  number,  number]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Type:** [
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number,
  number
]
