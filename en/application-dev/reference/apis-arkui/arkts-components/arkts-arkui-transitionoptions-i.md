# TransitionOptions

Defines the transition effect by setting parameters in the struct.

> **NOTE:** 
> 
> 1. When set to a value of the **TransitionOptions** type, the **transition** attribute must work with [animateTo](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#animateto). The animation duration,curve, and delay follow the settings in **animateTo**.
> 
> 2. If the value of the **TransitionOptions** type has only **type** specified, the transition effect will take on the default opacity. For example, **{type: TransitionType.Insert}** produces the same effect as
> **{type: TransitionType.Insert, opacity: 0}**. If a specific style is specified, the transition effect will not
> take on the default opacity.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [TransitionEffect](arkts-arkui-transitioneffect-c.md)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## opacity

```TypeScript
opacity?: number
```

Opacity of the component during transition, which is the value of the start point of insertion and the end point of deletion.

Value range: [0, 1]

**NOTE:** 

If the value specified is less than 0, the value **0** is used. If the value specified is greater than 1, the value **1** is used.

**Type:** number

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [opacity](arkts-arkui-transitioneffect-c.md#opacity)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rotate

```TypeScript
rotate?: RotateOptions
```

Rotation of the component during transition, which is the value of the start point of insertion and the end point of deletion.

- **x**: X-component of the rotation vector.  
- **y**: Y-component of the rotation vector.  
- **z**: Z-component of the rotation vector.  
- **centerX** and **centerY**: rotation center point. The default values are both **"50%"**, indicating the center  
point of the page.  
- If the center point is (0, 0), it refers to the upper left corner of the component.

**Type:** [RotateOptions](arkts-arkui-rotateoptions-i.md)

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [rotate](arkts-arkui-transitioneffect-c.md#rotate)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale?: ScaleOptions
```

Scaling of the component during transition, which is the value of the start point of insertion and the end point of deletion.

- **x**: scale factor along the x-axis.  
- **y**: scale factor along the y-axis.  
- **z**: scale factor along the z-axis (not effective for the current 2D graphics).  
- **centerX** and **centerY**: scale center point. The default values are both **"50%"**, indicating the center  
point of the page.  
- If the center point is (0, 0), it refers to the upper left corner of the component.

**NOTE:** 

If **centerX** or **centerY** is set to an invalid string (for example, **"illegalString"**), the default value **"0"** is used.

**Type:** [ScaleOptions](arkts-arkui-scaleoptions-i.md)

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [scale](arkts-arkui-transitioneffect-c.md#scale)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## translate

```TypeScript
translate?: TranslateOptions
```

Translation of the component during transition, which is the value of the start point of insertion and the end point of deletion.

-**x**: distance to translate along the x-axis.

-**y**: distance to translate along the y-axis.

-**z**: distance to translate along the z-axis.

**Type:** [TranslateOptions](arkts-arkui-translateoptions-i.md)

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [translate](arkts-arkui-transitioneffect-c.md#translate)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: TransitionType
```

Transition type.

Default value: **TransitionType.All**

**NOTE:** 

If **type** is not specified, the default value **TransitionType.All** is used, which means that the transition effect works for both component addition and deletion.

**Type:** [TransitionType](../arkts-apis/arkts-arkui-transitiontype-e.md)

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [TransitionEffect](arkts-arkui-transitioneffect-c.md)

**System capability:** SystemCapability.ArkUI.ArkUI.Full
