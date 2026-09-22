# native_type_visual.h

## Overview

Defines the visual effect types for the native module.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_TranslationOptions](capi-arkui-nativemodule-arkui-translationoptions.md) | ArkUI_TranslationOptions | Defines the translation options for component transition. |
| [ArkUI_ScaleOptions](capi-arkui-nativemodule-arkui-scaleoptions.md) | ArkUI_ScaleOptions | Defines the scaling options for component transition. |
| [ArkUI_RotationOptions](capi-arkui-nativemodule-arkui-rotationoptions.md) | ArkUI_RotationOptions | Defines the rotation options for component transition. |
| [ArkUI_PointF](capi-arkui-nativemodule-arkui-pointf.md) | ArkUI_PointF | Defines a two-dimensional point struct, with coordinates stored as float type. |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md) | ArkUI_Matrix4 | Defines a fourth-order matrix object. |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) | OH_ArkUI_ShadowOptions | Defines shadow options. |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md) | ArkUI_MotionPathOptions | Defines the motion path options for path animation. |
| [ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md) | ArkUI_Matrix4ScaleOptions | Defines a matrix scaling object. |
| [ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md) | ArkUI_Matrix4RotationOptions | Defines a matrix rotation object. |
| [ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md) | ArkUI_Matrix4TranslationOptions | Defines a matrix translation object. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ShadowType](#arkui_shadowtype) | ArkUI_ShadowType | Enumerates shadow types. |
| [ArkUI_ShadowStyle](#arkui_shadowstyle) | ArkUI_ShadowStyle | Enumerates shadow styles. |
| [ArkUI_AnimationCurve](#arkui_animationcurve) | ArkUI_AnimationCurve | Enumerates the animation curves. |
| [ArkUI_AnimationPlayMode](#arkui_animationplaymode) | ArkUI_AnimationPlayMode | Enumerates the animation playback directions. |
| [ArkUI_BlurStyle](#arkui_blurstyle) | ArkUI_BlurStyle | Enumerates the blur styles. |
| [ArkUI_BlurStyleActivePolicy](#arkui_blurstyleactivepolicy) | ArkUI_BlurStyleActivePolicy | Enumerates the activation policies for the background blur effect. |
| [ArkUI_BlendMode](#arkui_blendmode) | ArkUI_BlendMode | Enumerates the blend modes. |
| [ArkUI_ColorStrategy](#arkui_colorstrategy) | ArkUI_ColorStrategy | Enumerates foreground and shadow colors. |
| [ArkUI_MaskType](#arkui_masktype) | ArkUI_MaskType | Enumerates the mask types. A mask is a means to limit the display area of a component. It uses a specific shape to crop the component content so that only the content in the mask area is visible. |
| [ArkUI_ClipType](#arkui_cliptype) | ArkUI_ClipType | Enumerates the clipping region types. |
| [ArkUI_ShapeType](#arkui_shapetype) | ArkUI_ShapeType | Enumerates custom shape types. |
| [ArkUI_LinearGradientDirection](#arkui_lineargradientdirection) | ArkUI_LinearGradientDirection | Enumerates the gradient directions. |
| [ArkUI_TransitionEdge](#arkui_transitionedge) | ArkUI_TransitionEdge | Enumerates the slide-in and slide-out positions of the component from the screen edge during transition. |
| [ArkUI_BlendApplyType](#arkui_blendapplytype) | ArkUI_BlendApplyType | Defines how the specified blend mode is applied. |
| [ArkUI_FinishCallbackType](#arkui_finishcallbacktype) | ArkUI_FinishCallbackType | Enumerates the callback types for [OH_ArkUI_AnimatorOption_RegisterOnFinishCallback](capi-native-animate-h.md#oh_arkui_animatoroption_registeronfinishcallback) in an animation. |
| [ArkUI_RenderFit](#arkui_renderfit) | ArkUI_RenderFit | Enumerates the sizing and positioning behaviors of animated content in its final state. |
| [ArkUI_AnimationFillMode](#arkui_animationfillmode) | ArkUI_AnimationFillMode | Defines the status before and after execution of the animation in the current playback direction. |
| [ArkUI_AnimationDirection](#arkui_animationdirection) | ArkUI_AnimationDirection | Enumerates the animation playback modes. |
| [OH_ArkUI_AnimationPropertyType](#oh_arkui_animationpropertytype) | OH_ArkUI_AnimationPropertyType | Enumerates the animatable property types for property animations and keyframe animations. |
| [OH_ArkUI_AnimationGroupState](#oh_arkui_animationgroupstate) | OH_ArkUI_AnimationGroupState | Enumerates the playback states of an animation group. |
| [OH_ArkUI_AnimationFinishMode](#oh_arkui_animationfinishmode) | OH_ArkUI_AnimationFinishMode | Enumerates the finish modes of an animation group. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_MotionPathOptions* OH_ArkUI_MotionPathOptions_Create()](#oh_arkui_motionpathoptions_create) | Create a motion path option for path animation. |
| [void OH_ArkUI_MotionPathOptions_Dispose(ArkUI_MotionPathOptions* options)](#oh_arkui_motionpathoptions_dispose) | Destroys a motion path option of path animation. |
| [ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetPath(ArkUI_MotionPathOptions* options, const char* svgPath)](#oh_arkui_motionpathoptions_setpath) | Sets the motion path for the animation using an SVG path string. The path supports using **start** and **end** as placeholders for the starting and ending points, for example: **Mstart.x start.y L50 50 Lend.x end.y Z**. For details about the path string format, see {@link Path}. If this parameter is set to an empty string, it is equivalent to not setting a path animation. |
| [ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetPath(const ArkUI_MotionPathOptions* options, char* svgPathBuffer, const int32_t bufferSize, int32_t* writeLength)](#oh_arkui_motionpathoptions_getpath) | Obtains the motion path string stored in the motion path option. |
| [ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetFrom(ArkUI_MotionPathOptions* options, const float from)](#oh_arkui_motionpathoptions_setfrom) | Sets the start progress of the motion path. Progress refers to the ratio of the length of the path that has been traveled to the total length of the entire path. |
| [ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetFrom(const ArkUI_MotionPathOptions* options, float* from)](#oh_arkui_motionpathoptions_getfrom) | Obtains the start progress of the motion path from the motion path option. |
| [ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetTo(ArkUI_MotionPathOptions* options, const float to)](#oh_arkui_motionpathoptions_setto) | Sets the end progress of the motion path. Progress refers to the ratio of the length of the path that has been traveled to the total length of the entire path. |
| [ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetTo(const ArkUI_MotionPathOptions* options, float* to)](#oh_arkui_motionpathoptions_getto) | Obtains the end progress of the motion path from the motion path option. |
| [ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetRotatable(ArkUI_MotionPathOptions* options, const bool rotatable)](#oh_arkui_motionpathoptions_setrotatable) | Sets whether the component rotates along the motion path. |
| [ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetRotatable(const ArkUI_MotionPathOptions* options, bool* rotatable)](#oh_arkui_motionpathoptions_getrotatable) | Obtains whether the component rotates along the motion path. |
| [OH_ArkUI_ShadowOptions* OH_ArkUI_ShadowOptions_Create()](#oh_arkui_shadowoptions_create) | Creates a shadow option object. When the object is no longer in use, call [OH_ArkUI_ShadowOptions_Destroy](capi-native-type-visual-h.md#oh_arkui_shadowoptions_destroy) to destroy it. |
| [void OH_ArkUI_ShadowOptions_Destroy(OH_ArkUI_ShadowOptions* options)](#oh_arkui_shadowoptions_destroy) | Destroys the shadow option object. |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetRadius(OH_ArkUI_ShadowOptions* options, float radius)](#oh_arkui_shadowoptions_setradius) | Sets the blur radius for the shadow options. |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetRadius(OH_ArkUI_ShadowOptions* options, float* radius)](#oh_arkui_shadowoptions_getradius) | Obtains the blur radius for the shadow options. |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetType(OH_ArkUI_ShadowOptions* options, ArkUI_ShadowType type)](#oh_arkui_shadowoptions_settype) | Sets the shadow type for the shadow options. |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetType(OH_ArkUI_ShadowOptions* options, ArkUI_ShadowType* type)](#oh_arkui_shadowoptions_gettype) | Obtains the shadow type for the shadow options. |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetColor(OH_ArkUI_ShadowOptions* options, uint32_t color)](#oh_arkui_shadowoptions_setcolor) | Sets the shadow color for the shadow options. |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetColor(OH_ArkUI_ShadowOptions* options, uint32_t* color)](#oh_arkui_shadowoptions_getcolor) | Obtains the shadow color for the shadow options. |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetOffsetX(OH_ArkUI_ShadowOptions* options, float offsetX)](#oh_arkui_shadowoptions_setoffsetx) | Sets the shadow offset on the x-axis. |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetOffsetX(OH_ArkUI_ShadowOptions* options, float* offsetX)](#oh_arkui_shadowoptions_getoffsetx) | Obtains the shadow offset on the x-axis. |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetOffsetY(OH_ArkUI_ShadowOptions* options, float offsetY)](#oh_arkui_shadowoptions_setoffsety) | Sets the shadow offset on the y-axis. |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetOffsetY(OH_ArkUI_ShadowOptions* options, float* offsetY)](#oh_arkui_shadowoptions_getoffsety) | Obtains the shadow offset on the y-axis. |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetFill(OH_ArkUI_ShadowOptions* options, bool isFill)](#oh_arkui_shadowoptions_setfill) | Sets whether to fill a component with a shadow. |
| [ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetFill(OH_ArkUI_ShadowOptions* options, bool* isFill)](#oh_arkui_shadowoptions_getfill) | Obtains whether a component is filled with a shadow. |
| [ArkUI_Matrix4ScaleOptions* OH_ArkUI_Matrix4ScaleOptions_Create()](#oh_arkui_matrix4scaleoptions_create) | Creates a pointer to the scaling parameter object for matrix operations. In the newly created object, the default scaling coefficients in the x, y, and z directions are 1. The default values of **centerX** and **centerY**<br>of the transformation center point are 0. |
| [void OH_ArkUI_Matrix4ScaleOptions_Dispose(ArkUI_Matrix4ScaleOptions* options)](#oh_arkui_matrix4scaleoptions_dispose) | Disposes of the pointer to the scaling parameter object for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetX(ArkUI_Matrix4ScaleOptions* options, const float scaleX)](#oh_arkui_matrix4scaleoptions_setx) | Sets the scaling factor in the x direction of the scaling parameter object for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetX(const ArkUI_Matrix4ScaleOptions* options, float* scaleX)](#oh_arkui_matrix4scaleoptions_getx) | Obtains the scaling factor in the x direction of the scaling parameter object for matrix operations. If the value of x is not set, the default value of the scaling factor in the x direction is 1. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetY(ArkUI_Matrix4ScaleOptions* options, const float scaleY)](#oh_arkui_matrix4scaleoptions_sety) | Sets the scaling factor in the y direction of the scaling parameter object for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetY(const ArkUI_Matrix4ScaleOptions* options, float* scaleY)](#oh_arkui_matrix4scaleoptions_gety) | Obtains the scaling factor in the y direction of the scaling parameter object for matrix operations. If the value of y is not set, the default value of the scaling factor in the y direction is 1. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetZ(ArkUI_Matrix4ScaleOptions* options, const float scaleZ)](#oh_arkui_matrix4scaleoptions_setz) | Sets the scaling factor in the z direction of the scaling parameter object for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetZ(const ArkUI_Matrix4ScaleOptions* options, float* scaleZ)](#oh_arkui_matrix4scaleoptions_getz) | Obtains the scaling factor in the z direction of the scaling parameter object for matrix operations. If the value of z is not set, the default value of the scaling factor in the z direction is 1. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetCenterX(ArkUI_Matrix4ScaleOptions* options, const float centerX)](#oh_arkui_matrix4scaleoptions_setcenterx) | Sets the x coordinate of the transformation center point of the scaling parameter object for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetCenterX(const ArkUI_Matrix4ScaleOptions* options, float* centerX)](#oh_arkui_matrix4scaleoptions_getcenterx) | Obtains the x coordinate of the transformation center point of the scaling parameter object for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetCenterY(ArkUI_Matrix4ScaleOptions* options, const float centerY)](#oh_arkui_matrix4scaleoptions_setcentery) | Sets the y coordinate of the transformation center point of the scaling parameter object for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetCenterY(const ArkUI_Matrix4ScaleOptions* options, float* centerY)](#oh_arkui_matrix4scaleoptions_getcentery) | Obtains the y coordinate of the transformation center point of the scaling parameter object for matrix operations. |
| [ArkUI_Matrix4RotationOptions* OH_ArkUI_Matrix4RotationOptions_Create()](#oh_arkui_matrix4rotationoptions_create) | Creates a pointer to the rotation parameter object for matrix operations. In the newly created object, the default value of an x-axis offset (**centerX**) of a single matrix transformation center point relative to a component transformation center point, the default value of a y-axis offset (**centerY**) of the single matrix transformation center point relative to the component transformation center point, and the default value of a rotation angle (**angle**) are 0. If none of the direction vectors in the x, y, and z directions is specified, the value is equivalent to x=0, y=0, and z=1, indicating rotation around the z-axis. Once any of the direction vectors in the x, y, and z directions is specified, the unspecified values are equivalent to 0. |
| [void OH_ArkUI_Matrix4RotationOptions_Dispose(ArkUI_Matrix4RotationOptions* options)](#oh_arkui_matrix4rotationoptions_dispose) | Disposes of the pointer to the rotation parameter object for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetX(ArkUI_Matrix4RotationOptions* options, const float x)](#oh_arkui_matrix4rotationoptions_setx) | Sets the direction vector in the x direction of the rotation parameter object for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetX(const ArkUI_Matrix4RotationOptions* options, float* x)](#oh_arkui_matrix4rotationoptions_getx) | Obtains the direction vector in the x direction of the rotation parameter object for matrix operations. If the value of x has never been set, the value is undefined. In this case, [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetY(ArkUI_Matrix4RotationOptions* options, const float y)](#oh_arkui_matrix4rotationoptions_sety) | Sets the direction vector in the y direction of the rotation parameter object for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetY(const ArkUI_Matrix4RotationOptions* options, float* y)](#oh_arkui_matrix4rotationoptions_gety) | Obtains the direction vector in the y direction of the rotation parameter object for matrix operations. If the value of y has never been set, the value is undefined. In this case, [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetZ(ArkUI_Matrix4RotationOptions* options, const float z)](#oh_arkui_matrix4rotationoptions_setz) | Sets the direction vector in the z direction of the rotation parameter object for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetZ(const ArkUI_Matrix4RotationOptions* options, float* z)](#oh_arkui_matrix4rotationoptions_getz) | Obtains the direction vector in the z direction of the rotation parameter object for matrix operations. If the value of z has never been set, the value is undefined. In this case, [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetAngle(ArkUI_Matrix4RotationOptions* options, const float angle)](#oh_arkui_matrix4rotationoptions_setangle) | Sets the rotation angle in the rotation parameter object for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetAngle(const ArkUI_Matrix4RotationOptions* options, float* angle)](#oh_arkui_matrix4rotationoptions_getangle) | Obtains the rotation angle in the rotation parameter object for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetCenterX(ArkUI_Matrix4RotationOptions* options, const float centerX)](#oh_arkui_matrix4rotationoptions_setcenterx) | Sets the x-axis offset of a single matrix transformation center point relative to a component transformation center point. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetCenterX(const ArkUI_Matrix4RotationOptions* options, float* centerX)](#oh_arkui_matrix4rotationoptions_getcenterx) | Obtains the x-axis offset of a single matrix transformation center point relative to a component transformation center point. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetCenterY(ArkUI_Matrix4RotationOptions* options, const float centerY)](#oh_arkui_matrix4rotationoptions_setcentery) | Sets the y-axis offset of a single matrix transformation center point relative to a component transformation center point. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetCenterY(const ArkUI_Matrix4RotationOptions* options, float* centerY)](#oh_arkui_matrix4rotationoptions_getcentery) | Obtains the y-axis offset of a single matrix transformation center point relative to a component transformation center point. |
| [ArkUI_Matrix4TranslationOptions* OH_ArkUI_Matrix4TranslationOptions_Create()](#oh_arkui_matrix4translationoptions_create) | Creates a pointer to a translation object for matrix operations. In the newly created object, the default translation distances on the x, y, and z axes are 0. |
| [void OH_ArkUI_Matrix4TranslationOptions_Dispose(ArkUI_Matrix4TranslationOptions* options)](#oh_arkui_matrix4translationoptions_dispose) | Disposes of a pointer to a translation object for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_SetX(ArkUI_Matrix4TranslationOptions* options, const float x)](#oh_arkui_matrix4translationoptions_setx) | Sets the translation value of a translation object on the x-axis for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_GetX(const ArkUI_Matrix4TranslationOptions* options, float* x)](#oh_arkui_matrix4translationoptions_getx) | Obtains the translation value of a translation object on the x-axis for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_SetY(ArkUI_Matrix4TranslationOptions* options, const float y)](#oh_arkui_matrix4translationoptions_sety) | Sets the translation value of a translation object on the y-axis for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_GetY(const ArkUI_Matrix4TranslationOptions* options, float* y)](#oh_arkui_matrix4translationoptions_gety) | Obtains the translation value of a translation object on the y-axis for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_SetZ(ArkUI_Matrix4TranslationOptions* options, const float z)](#oh_arkui_matrix4translationoptions_setz) | Sets the translation value of a translation object on the z-axis for matrix operations. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_GetZ(const ArkUI_Matrix4TranslationOptions* options, float* z)](#oh_arkui_matrix4translationoptions_getz) | Obtains the translation value of a translation object on the z-axis for matrix operations. |
| [ArkUI_Matrix4* OH_ArkUI_Matrix4_CreateIdentity()](#oh_arkui_matrix4_createidentity) | Creates a fourth-order identity matrix object. |
| [ArkUI_Matrix4* OH_ArkUI_Matrix4_CreateByElements(const float* elements)](#oh_arkui_matrix4_createbyelements) | Creates a fourth-order matrix object by specifying each element of the matrix. |
| [void OH_ArkUI_Matrix4_Dispose(ArkUI_Matrix4* matrix)](#oh_arkui_matrix4_dispose) | Disposes of a fourth-order matrix object. |
| [ArkUI_Matrix4* OH_ArkUI_Matrix4_Copy(const ArkUI_Matrix4* matrix)](#oh_arkui_matrix4_copy) | Creates a copy of a fourth-order matrix object. It is used to perform operations on the same matrix to obtain different matrix objects. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_Invert(ArkUI_Matrix4* matrix)](#oh_arkui_matrix4_invert) | Performs an inverse matrix transformation on the input matrix. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_Combine(ArkUI_Matrix4* oriMatrix, const ArkUI_Matrix4* anotherMatrix)](#oh_arkui_matrix4_combine) | Combines another matrix with the original matrix and stores the resulting matrix in **oriMatrix**. The resulting matrix is equivalent to first applying the transformation of **oriMatrix** and then applying the transformation of **anotherMatrix**. This function modifies the **oriMatrix** object. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_Translate(ArkUI_Matrix4* matrix, const ArkUI_Matrix4TranslationOptions* translate)](#oh_arkui_matrix4_translate) | Applies a translation transformation to the original matrix to obtain the translated matrix. Each translation transformation is cumulative on the previous matrix. The input matrix object is modified after the transformation. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_Scale(ArkUI_Matrix4* matrix, const ArkUI_Matrix4ScaleOptions* scale)](#oh_arkui_matrix4_scale) | Applies a scaling transformation to the original matrix to obtain the scaled matrix. Each scaling transformation is cumulative on the previous matrix. This function modifies the input matrix object. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_Rotate(ArkUI_Matrix4* matrix, const ArkUI_Matrix4RotationOptions* rotate)](#oh_arkui_matrix4_rotate) | Applies a rotation transformation to the original matrix to obtain the rotated matrix. Each rotation transformation is cumulative on the previous matrix. This function modifies the input matrix object. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_Skew(ArkUI_Matrix4* matrix, const float skewX, const float skewY)](#oh_arkui_matrix4_skew) | Applies a skew transformation to the original matrix to obtain the skewed matrix. Each skew transformation is cumulative on the previous matrix. The input matrix object is modified after the transformation. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_TransformPoint(const ArkUI_Matrix4* matrix, const ArkUI_PointF* oriPoint, ArkUI_PointF* result)](#oh_arkui_matrix4_transformpoint) | Calculates the new coordinate position of a point after it is transformed by a matrix. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_SetPolyToPoly(ArkUI_Matrix4* matrix, const ArkUI_PointF* src, const ArkUI_PointF* dst, const uint32_t pointCount)](#oh_arkui_matrix4_setpolytopoly) | Maps the vertex coordinates of one polygon to the vertex coordinates of another polygon and calculates the required matrix. |
| [ArkUI_ErrorCode OH_ArkUI_Matrix4_GetElements(const ArkUI_Matrix4* matrix, float* result)](#oh_arkui_matrix4_getelements) | Obtains the 16 elements of the fourth-order matrix. |

## Enum type description

### ArkUI_ShadowType

```c
enum ArkUI_ShadowType
```

**Description**

Enumerates shadow types.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SHADOW_TYPE_COLOR = 0 | Color shadow. |
| ARKUI_SHADOW_TYPE_BLUR | Blur shadow. |

### ArkUI_ShadowStyle

```c
enum ArkUI_ShadowStyle
```

**Description**

Enumerates shadow styles.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SHADOW_STYLE_OUTER_DEFAULT_XS = 0 | Mini shadow.<br> |
| ARKUI_SHADOW_STYLE_OUTER_DEFAULT_SM | Small shadow.<br> |
| ARKUI_SHADOW_STYLE_OUTER_DEFAULT_MD | Medium shadow.<br> |
| ARKUI_SHADOW_STYLE_OUTER_DEFAULT_LG | Large shadow.<br> |
| ARKUI_SHADOW_STYLE_OUTER_FLOATING_SM | Floating small shadow.<br> |
| ARKUI_SHADOW_STYLE_OUTER_FLOATING_MD | Floating medium shadow.<br> |

### ArkUI_AnimationCurve

```c
enum ArkUI_AnimationCurve
```

**Description**

Enumerates the animation curves.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_CURVE_LINEAR = 0 | The animation speed keeps unchanged. |
| ARKUI_CURVE_EASE | The animation starts slowly, accelerates, and then slows down towards the end. |
| ARKUI_CURVE_EASE_IN | The animation starts at a low speed and then picks up speed until the end. |
| ARKUI_CURVE_EASE_OUT | The animation ends at a low speed. |
| ARKUI_CURVE_EASE_IN_OUT | The animation starts and ends at a low speed, providing a smooth and natural transition. |
| ARKUI_CURVE_FAST_OUT_SLOW_IN | The animation uses the standard curve |
| ARKUI_CURVE_LINEAR_OUT_SLOW_IN | The animation uses the deceleration curve. |
| ARKUI_CURVE_FAST_OUT_LINEAR_IN | The animation uses the acceleration curve. |
| ARKUI_CURVE_EXTREME_DECELERATION | The animation uses the extreme deceleration curve. |
| ARKUI_CURVE_SHARP | The animation uses the sharp curve. |
| ARKUI_CURVE_RHYTHM | The animation uses the rhythm curve. |
| ARKUI_CURVE_SMOOTH | The animation uses the smooth curve. |
| ARKUI_CURVE_FRICTION | The animation uses the friction curve |

### ArkUI_AnimationPlayMode

```c
enum ArkUI_AnimationPlayMode
```

**Description**

Enumerates the animation playback directions.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_ANIMATION_PLAY_MODE_NORMAL = 0 | The animation is played forwards. |
| ARKUI_ANIMATION_PLAY_MODE_REVERSE | The animation is played backwards. |
| ARKUI_ANIMATION_PLAY_MODE_ALTERNATE | The animation plays in alternating loop mode. When the animation is played for an odd number of times, the playback is in forward direction. When the animation is played for an even number of times, the playback is in reverse direction. |
| ARKUI_ANIMATION_PLAY_MODE_ALTERNATE_REVERSE | The animation plays in reverse alternating loop mode. When the animation is played for an odd number of times, the playback is in reverse direction. When the animation is played for an even number of times, the playback is in forward direction. |

### ArkUI_BlurStyle

```c
enum ArkUI_BlurStyle
```

**Description**

Enumerates the blur styles.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_BLUR_STYLE_THIN = 0 | Thin material.<br> |
| ARKUI_BLUR_STYLE_REGULAR | Regular material.<br> |
| ARKUI_BLUR_STYLE_THICK | Thick material.<br> |
| ARKUI_BLUR_STYLE_BACKGROUND_THIN | Material that creates the minimum depth of field effect.<br> |
| ARKUI_BLUR_STYLE_BACKGROUND_REGULAR | Material that creates a medium shallow depth of field effect.<br> |
| ARKUI_BLUR_STYLE_BACKGROUND_THICK | Material that creates a high shallow depth of field effect.<br> |
| ARKUI_BLUR_STYLE_BACKGROUND_ULTRA_THICK | Material that creates the maximum depth of field effect.<br> |
| ARKUI_BLUR_STYLE_NONE | No blur.<br> |
| ARKUI_BLUR_STYLE_COMPONENT_ULTRA_THIN | Component ultra-thin material.<br> |
| ARKUI_BLUR_STYLE_COMPONENT_THIN | Component thin material.<br> |
| ARKUI_BLUR_STYLE_COMPONENT_REGULAR | Component regular material.<br> |
| ARKUI_BLUR_STYLE_COMPONENT_THICK | Component thick material.<br> |
| ARKUI_BLUR_STYLE_COMPONENT_ULTRA_THICK | Component ultra-thick material.<br> |

### ArkUI_BlurStyleActivePolicy

```c
enum ArkUI_BlurStyleActivePolicy
```

**Description**

Enumerates the activation policies for the background blur effect.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 19

| Enum item | Description |
| -- | -- |
| ARKUI_BLUR_STYLE_ACTIVE_POLICY_FOLLOWS_WINDOW_ACTIVE_STATE = 0 | The blur effect changes according to the window's focus state; it is inactive when the window is not in focus and active when the window is in focus. |
| ARKUI_BLUR_STYLE_ACTIVE_POLICY_ALWAYS_ACTIVE | The blur effect is always active. |
| ARKUI_BLUR_STYLE_ACTIVE_POLICY_ALWAYS_INACTIVE | The blur effect is always inactive. |

### ArkUI_BlendMode

```c
enum ArkUI_BlendMode
```

**Description**

Enumerates the blend modes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_BLEND_MODE_NONE = 0 | The top image is superimposed on the bottom image without any blending. |
| ARKUI_BLEND_MODE_CLEAR | The target pixels covered by the source pixels are erased by being turned to completely transparent. |
| ARKUI_BLEND_MODE_SRC | r = s: Only the source pixels are displayed. |
| ARKUI_BLEND_MODE_DST | r = d: Only the target pixels are displayed. |
| ARKUI_BLEND_MODE_SRC_OVER | r = s + (1 - sa) * d: The source pixels are blended based on opacity and cover the target pixels. |
| ARKUI_BLEND_MODE_DST_OVER | r = d + (1 - da) * s: The target pixels are blended based on opacity and cover on the source pixels. |
| ARKUI_BLEND_MODE_SRC_IN | r = s * da: Only the part of the source pixels that overlap with the target pixels is displayed. |
| ARKUI_BLEND_MODE_DST_IN | r = d * sa: Only the part of the target pixels that overlap with the source pixels is displayed. |
| ARKUI_BLEND_MODE_SRC_OUT | r = s * (1 - da): Only the part of the source pixels that do not overlap with the target pixels is displayed. |
| ARKUI_BLEND_MODE_DST_OUT | r = d * (1 - sa): Only the part of the target pixels that do not overlap with the source pixels is displayed. |
| ARKUI_BLEND_MODE_SRC_ATOP | r = s * da + d * (1 - sa): The part of the source pixels that overlap with the target pixels is displayed and the part of the target pixels that do not overlap with the source pixels are displayed. |
| ARKUI_BLEND_MODE_DST_ATOP | r = d * sa + s * (1 - da): The part of the target pixels that overlap with the source pixels and the part of the source pixels that do not overlap with the target pixels are displayed. |
| ARKUI_BLEND_MODE_XOR | r = s * (1 - da) + d * (1 - sa): Only the non-overlapping part between the source pixels and the target pixels is displayed. |
| ARKUI_BLEND_MODE_PLUS | r = min(s + d, 1): New pixels resulting from adding the source pixels to the target pixels are displayed. |
| ARKUI_BLEND_MODE_MODULATE | r = s * d: New pixels resulting from multiplying the source pixels with the target pixels are displayed. |
| ARKUI_BLEND_MODE_SCREEN | r = s + d - s * d: Pixels are blended by adding the source pixels to the target pixels and subtracting the product of their multiplication. |
| ARKUI_BLEND_MODE_OVERLAY | The MULTIPLY or SCREEN mode is used based on the target pixels. |
| ARKUI_BLEND_MODE_DARKEN | rc = s + d - max(s * da, d * sa), ra = kSrcOver: When two colors overlap, whichever is darker is used. |
| ARKUI_BLEND_MODE_LIGHTEN | rc = s + d - min(s * da, d * sa), ra = kSrcOver: The final pixels are composed of the lightest values of pixels. |
| ARKUI_BLEND_MODE_COLOR_DODGE | The colors of the target pixels are lightened to reflect the source pixels. |
| ARKUI_BLEND_MODE_COLOR_BURN | The colors of the target pixels are darkened to reflect the source pixels. |
| ARKUI_BLEND_MODE_HARD_LIGHT | The MULTIPLY or SCREEN mode is used, depending on the source pixels. |
| ARKUI_BLEND_MODE_SOFT_LIGHT | The LIGHTEN or DARKEN mode is used, depending on the source pixels. |
| ARKUI_BLEND_MODE_DIFFERENCE | rc = s + d - 2 * (min(s * da, d * sa)), ra = kSrcOver: The final pixel is the result of subtracting the darker of the two pixels (source and target) from the lighter one. |
| ARKUI_BLEND_MODE_EXCLUSION | rc = s + d - two(s * d), ra = kSrcOver: The final pixel is similar to <b>DIFFERENCE</b>, but with less contrast. |
| ARKUI_BLEND_MODE_MULTIPLY | r = s * (1 - da) + d * (1 - sa) + s * d: The final pixel is the result of multiplying the source pixel by the target pixel. |
| ARKUI_BLEND_MODE_HUE | The resultant image is created with the luminance and saturation of the source image and the hue of the target image. |
| ARKUI_BLEND_MODE_SATURATION | The resultant image is created with the luminance and hue of the target image and the saturation of the source image. |
| ARKUI_BLEND_MODE_COLOR | The resultant image is created with the saturation and hue of the source image and the luminance of the target image. |
| ARKUI_BLEND_MODE_LUMINOSITY | The resultant image is created with the saturation and hue of the target image and the luminance of the source image. |

### ArkUI_ColorStrategy

```c
enum ArkUI_ColorStrategy
```

**Description**

Enumerates foreground and shadow colors.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_COLOR_STRATEGY_INVERT = 0 | The foreground colors are the inverse of the component background colors. |
| ARKUI_COLOR_STRATEGY_AVERAGE | The shadow colors of the component are the average color obtained from the component background shadow area. |
| ARKUI_COLOR_STRATEGY_PRIMARY | The shadow colors of the component are the primary color obtained from the component background shadow area. |

### ArkUI_MaskType

```c
enum ArkUI_MaskType
```

**Description**

Enumerates the mask types. A mask is a means to limit the display area of a component. It uses a specific shape to crop the component content so that only the content in the mask area is visible.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_MASK_TYPE_RECTANGLE = 0 | Rectangle. |
| ARKUI_MASK_TYPE_CIRCLE | Circle. |
| ARKUI_MASK_TYPE_ELLIPSE | Ellipse. |
| ARKUI_MASK_TYPE_PATH | Path. |
| ARKUI_MASK_TYPE_PROGRESS | Progress indicator. |

### ArkUI_ClipType

```c
enum ArkUI_ClipType
```

**Description**

Enumerates the clipping region types.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_CLIP_TYPE_RECTANGLE = 0 | Rectangle. |
| ARKUI_CLIP_TYPE_CIRCLE | Circle. |
| ARKUI_CLIP_TYPE_ELLIPSE | Ellipse. |
| ARKUI_CLIP_TYPE_PATH | Path. |

### ArkUI_ShapeType

```c
enum ArkUI_ShapeType
```

**Description**

Enumerates custom shape types.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SHAPE_TYPE_RECTANGLE = 0 | Rectangle. |
| ARKUI_SHAPE_TYPE_CIRCLE | Circle. |
| ARKUI_SHAPE_TYPE_ELLIPSE | Ellipse. |
| ARKUI_SHAPE_TYPE_PATH | Path. |

### ArkUI_LinearGradientDirection

```c
enum ArkUI_LinearGradientDirection
```

**Description**

Enumerates the gradient directions.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT = 0 | From right to left. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_TOP | From bottom to top. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT | From left to right. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_BOTTOM | From top to bottom. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_TOP | From lower right to upper left. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM | From upper right to lower left. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT_TOP | From lower left to upper right. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_RIGHT_BOTTOM | From upper left to lower right. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_NONE | No gradient. |
| ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM | Custom direction. |

### ArkUI_TransitionEdge

```c
enum ArkUI_TransitionEdge
```

**Description**

Enumerates the slide-in and slide-out positions of the component from the screen edge during transition.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TRANSITION_EDGE_TOP = 0 | Top edge of the window. |
| ARKUI_TRANSITION_EDGE_BOTTOM | Bottom edge of the window. |
| ARKUI_TRANSITION_EDGE_START | Left edge of the window. |
| ARKUI_TRANSITION_EDGE_END | Right edge of the window. |

### ArkUI_BlendApplyType

```c
enum ArkUI_BlendApplyType
```

**Description**

Defines how the specified blend mode is applied.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| BLEND_APPLY_TYPE_FAST = 0 | The content of the view is blended in sequence on the target image. |
| BLEND_APPLY_TYPE_OFFSCREEN | The content of the component and its child components are drawn on the offscreen canvas, and then blended with the existing content on the canvas. |

### ArkUI_FinishCallbackType

```c
enum ArkUI_FinishCallbackType
```

**Description**

Enumerates the callback types for [OH_ArkUI_AnimatorOption_RegisterOnFinishCallback](capi-native-animate-h.md#oh_arkui_animatoroption_registeronfinishcallback) in an animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_FINISH_CALLBACK_REMOVED = 0 | The callback is invoked when the entire animation is removed once it has finished. |
| ARKUI_FINISH_CALLBACK_LOGICALLY | The callback is invoked when the animation logically enters the falling state, though it may still be in its long tail state. |

### ArkUI_RenderFit

```c
enum ArkUI_RenderFit
```

**Description**

Enumerates the sizing and positioning behaviors of animated content in its final state.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_RENDER_FIT_CENTER = 0 | Maintains the content size of the animation's final state, and the content is always centered with the component. |
| ARKUI_RENDER_FIT_TOP | Maintains the content size of the animation's final state, and the content is always aligned with the top center of the component. |
| ARKUI_RENDER_FIT_BOTTOM | Maintains the content size of the animation's final state, and the content is always aligned with the bottom center of the component. |
| ARKUI_RENDER_FIT_LEFT | Maintains the content size of the animation's final state, and the content is always aligned to the left of the component. |
| ARKUI_RENDER_FIT_RIGHT | Maintains the content size of the animation's final state, and the content is always right-aligned with the component. |
| ARKUI_RENDER_FIT_TOP_LEFT | Maintains the content size of the animation's final state, and the content is always aligned with the top left corner of the component. |
| ARKUI_RENDER_FIT_TOP_RIGHT | Keep the content size of the animation final state, and the content is always aligned with the upper right corner of the component. |
| ARKUI_RENDER_FIT_BOTTOM_LEFT | Keep the content size of the animation final state, and the content always aligns with the lower-left corner of the component. |
| ARKUI_RENDER_FIT_BOTTOM_RIGHT | Keep the content size of the animation final state, and the content always aligns with the lower-right corner of the component. |
| ARKUI_RENDER_FIT_RESIZE_FILL | The aspect ratio of the animation's final state content is not considered, and the content is always scaled to the size of the component. |
| ARKUI_RENDER_FIT_RESIZE_CONTAIN | Reduce or enlarge the aspect ratio of the animation final state content, so that the content is fully displayed in the component, and keep the center aligned with the component. |
| ARKUI_RENDER_FIT_RESIZE_CONTAIN_TOP_LEFT | Keep the aspect ratio of the animation final state content to reduce or enlarge, so that the content is fully displayed in the component. When there is left over in the broad direction of the component, the content is aligned to the left of the component, and when there is left over in the high direction of the component, the content is aligned to the top of the component. |
| ARKUI_RENDER_FIT_RESIZE_CONTAIN_BOTTOM_RIGHT | Keep the aspect ratio of the animation final state content to reduce or enlarge, so that the content is fully displayed in the component. When there is left in the wide direction of the component, the content is aligned with the component on the right. When there is left in the high direction of the component, the content is aligned with the component on the bottom. |
| ARKUI_RENDER_FIT_RESIZE_COVER | Keep the aspect ratio of the animation final state content reduced or enlarged, so that both sides of the content are greater than or equal to both sides of the component, and keep the center aligned with the component to display the middle part of the content. |
| ARKUI_RENDER_FIT_RESIZE_COVER_TOP_LEFT | Keep the aspect ratio of the final content of the animation reduced or enlarged so that both sides of the content are exactly greater than or equal to both sides of the component. When the content width is left, the content is aligned to the left of the component, and the left portion of the content is displayed. When the content is left in the high direction, the content and the component remain top aligned, showing the top side of the content. |
| ARKUI_RENDER_FIT_RESIZE_COVER_BOTTOM_RIGHT | Keep the aspect ratio of the final content of the animation reduced or enlarged so that both sides of the content are exactly greater than or equal to both sides of the component. When the content width is left, the content and the component remain right aligned, and the right part of the content is displayed. When the content is left in the high direction, the content and the component remain aligned at the bottom, and the bottom part of the content is displayed. |

### ArkUI_AnimationFillMode

```c
enum ArkUI_AnimationFillMode
```

**Description**

Defines the status before and after execution of the animation in the current playback direction.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_ANIMATION_FILL_MODE_NONE | Before execution, the animation does not apply any styles to the target component. After execution, the animation restores the target component to its default state. |
| ARKUI_ANIMATION_FILL_MODE_FORWARDS | The target component retains the state set by the last keyframe encountered during execution of the animation. |
| ARKUI_ANIMATION_FILL_MODE_BACKWARDS | The animation applies the values defined in the first relevant keyframe once it is applied to the target component, and retains the values during the period set by delay. |
| ARKUI_ANIMATION_FILL_MODE_BOTH | The animation follows the rules for both Forwards and Backwards, extending the animation attributes in both directions. |

### ArkUI_AnimationDirection

```c
enum ArkUI_AnimationDirection
```

**Description**

Enumerates the animation playback modes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_ANIMATION_DIRECTION_NORMAL = 0 | The animation plays in forward loop mode. |
| ARKUI_ANIMATION_DIRECTION_REVERSE | The animation plays in reverse loop mode. |
| ARKUI_ANIMATION_DIRECTION_ALTERNATE | The animation plays in alternating loop mode. When the animation is played for an odd number of times, the playback is in forward direction. When the animation is played for an even number of times, the playback is in reverse direction. |
| ARKUI_ANIMATION_DIRECTION_ALTERNATE_REVERSE | The animation plays in reverse alternating loop mode. When the animation is played for an odd number of times, the playback is in reverse direction. When the animation is played for an even number of times, the playback is in forward direction. |

### OH_ArkUI_AnimationPropertyType

```c
enum OH_ArkUI_AnimationPropertyType
```

**Description**

Enumerates the animatable property types for property animations and keyframe animations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

| Enum item | Description |
| -- | -- |
| OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION = 0 | Translation in both x and y directions. The value parameter requires two f32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) elements: [x, y], in px.<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION_X = 1 | Translation in the x direction. The value parameter requires one f32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) element: [x], in px.<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION_Y = 2 | Translation in the y direction. The value parameter requires one f32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) element: [y], in px.<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION_Z = 3 | Translation in the z direction. The value parameter requires one f32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) element: [z], in px.<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_PROPERTY_SCALE = 4 | Scale in both x and y directions. The value parameter requires two f32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) elements: [x, y].<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_PROPERTY_SCALE_X = 5 | Scale in the x direction. The value parameter requires one f32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) element: [x].<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_PROPERTY_SCALE_Y = 6 | Scale in the y direction. The value parameter requires one f32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) element: [y].<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_PROPERTY_ROTATION = 7 | Rotation angle for all axes. The value parameter requires three f32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) elements: [angleX, angleY, angleZ], in degrees.<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_PROPERTY_ROTATION_X = 8 | Rotation angle around the x-axis. The value parameter requires one f32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) element: [angle], in degrees.<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_PROPERTY_ROTATION_Y = 9 | Rotation angle around the y-axis. The value parameter requires one f32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) element: [angle], in degrees.<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_PROPERTY_ROTATION_Z = 10 | Rotation angle around the z-axis. The value parameter requires one f32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) element: [angle], in degrees.<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_PROPERTY_OPACITY = 11 | Opacity of the component. The value parameter requires one f32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) element: [opacity]. Value range: [0, 1].<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_PROPERTY_BOUNDS = 12 | Bounds (position and size). The value parameter requires four i32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) elements: [x, y, width, height], in px.<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_PROPERTY_BOUNDS_X = 13 | Position x within bounds. The value parameter requires one i32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) element: [x], in px.<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_PROPERTY_BOUNDS_Y = 14 | Position y within bounds. The value parameter requires one i32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) element: [y], in px.<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_PROPERTY_BOUNDS_WIDTH = 15 | Width of the bounds. The value parameter requires one i32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) element: [width], in px.<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_PROPERTY_BOUNDS_HEIGHT = 16 | Height of the bounds. The value parameter requires one i32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) element: [height], in px.<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_PROPERTY_BACKGROUND_COLOR = 17 | Background color of the component. The value parameter requires one u32 [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) element: [color].<br>**Since**: 26.0.1 |

### OH_ArkUI_AnimationGroupState

```c
enum OH_ArkUI_AnimationGroupState
```

**Description**

Enumerates the playback states of an animation group.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

| Enum item | Description |
| -- | -- |
| OH_ARKUI_ANIMATION_GROUP_STATE_RUNNING = 0 | The animation group is running.<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_GROUP_STATE_PAUSED = 1 | The animation group is paused.<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_GROUP_STATE_INACTIVE = 2 | The animation group is inactive, for example, when the animation has finished or when the group is in an invalid state.<br>**Since**: 26.0.1 |

### OH_ArkUI_AnimationFinishMode

```c
enum OH_ArkUI_AnimationFinishMode
```

**Description**

Enumerates the finish modes of an animation group.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

| Enum item | Description |
| -- | -- |
| OH_ARKUI_ANIMATION_FINISH_TO_START = 0 | Finishes the animation group and jumps to the start state.<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_FINISH_TO_CURRENT = 1 | Finishes the animation group and stays at the current value.<br>**Since**: 26.0.1 |
| OH_ARKUI_ANIMATION_FINISH_TO_END = 2 | Finishes the animation group and jumps to the end state.<br>**Since**: 26.0.1 |


## Function description

### OH_ArkUI_MotionPathOptions_Create()

```c
ArkUI_MotionPathOptions* OH_ArkUI_MotionPathOptions_Create()
```

**Description**

Create a motion path option for path animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_MotionPathOptions*](capi-arkui-nativemodule-arkui-motionpathoptions.md) | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md).      <br>In the newly created [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md) object, path (motion path) is an empty string,       from (start progress) is 0, to (end progress) is 1, and rotatable (whether the component      rotates along the path) is false. |

### OH_ArkUI_MotionPathOptions_Dispose()

```c
void OH_ArkUI_MotionPathOptions_Dispose(ArkUI_MotionPathOptions* options)
```

**Description**

Destroys a motion path option of path animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md). |

### OH_ArkUI_MotionPathOptions_SetPath()

```c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetPath(ArkUI_MotionPathOptions* options, const char* svgPath)
```

**Description**

Sets the motion path for the animation using an SVG path string. The path supports using **start** and **end** as placeholders for the starting and ending points, for example: **Mstart.x start.y L50 50 Lend.x end.y Z**. For details about the path string format, see {@link Path}. If this parameter is set to an empty string, it is equivalent to not setting a path animation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md). |
| const char* svgPath | Motion path string for the path animation. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_MotionPathOptions_GetPath()

```c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetPath(const ArkUI_MotionPathOptions* options, char* svgPathBuffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the motion path string stored in the motion path option.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md). |
| char* svgPathBuffer | Buffer pointer to the motion path string. |
| const int32_t bufferSize | Buffer size of the **svgPathBuffer** parameter. |
| int32_t* writeLength | Indicates the string length actually written to the buffer when [ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. Indicates the minimum buffer size that can accommodate the target string when [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul> .          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          <li>[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the buffer size is less than the minimum buffer size.</li>          </ul> |

### OH_ArkUI_MotionPathOptions_SetFrom()

```c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetFrom(ArkUI_MotionPathOptions* options, const float from)
```

**Description**

Sets the start progress of the motion path. Progress refers to the ratio of the length of the path that has been traveled to the total length of the entire path.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md). |
| const float from | Start progress of the motion path. The value ranges from **0.0** to **1.0**. The value of **from** must be less than or equal to that of **to**; otherwise, [ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. For details about the meaning of **to**, see [OH_ArkUI_MotionPathOptions_SetTo](capi-native-type-visual-h.md#oh_arkui_motionpathoptions_setto). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          <li>[ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if from is out of the range [0.0, 1.0] or from is               greater than to.</li>          </ul> |

### OH_ArkUI_MotionPathOptions_GetFrom()

```c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetFrom(const ArkUI_MotionPathOptions* options, float* from)
```

**Description**

Obtains the start progress of the motion path from the motion path option.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md). |
| float* from | Pointer to the variable used to receive the start progress of the motion path. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_MotionPathOptions_SetTo()

```c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetTo(ArkUI_MotionPathOptions* options, const float to)
```

**Description**

Sets the end progress of the motion path. Progress refers to the ratio of the length of the path that has been traveled to the total length of the entire path.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md). |
| const float to | End progress of the motion path. The value ranges from **0.0** to **1.0**. The value of **to** must be greater than or equal to that of **from**; otherwise, [ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned. For details about the meaning of **from**, see [OH_ArkUI_MotionPathOptions_SetFrom](capi-native-type-visual-h.md#oh_arkui_motionpathoptions_setfrom). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>.          <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          <li>[ARKUI_ERROR_CODE_PARAM_OUT_OF_RANGE](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if to is out of the range [0.0, 1.0] or to is less than           from.</li>          </ul> |

### OH_ArkUI_MotionPathOptions_GetTo()

```c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetTo(const ArkUI_MotionPathOptions* options, float* to)
```

**Description**

Obtains the end progress of the motion path from the motion path option.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md). |
| float* to | Pointer to the variable used to receive the end progress of the motion path. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_MotionPathOptions_SetRotatable()

```c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_SetRotatable(ArkUI_MotionPathOptions* options, const bool rotatable)
```

**Description**

Sets whether the component rotates along the motion path.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md). |
| const bool rotatable | Whether the component rotates along the path. The value **true** means that the component rotates along the path, and **false** means that the component does not rotate along the path. The default value is **false**. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_MotionPathOptions_GetRotatable()

```c
ArkUI_ErrorCode OH_ArkUI_MotionPathOptions_GetRotatable(const ArkUI_MotionPathOptions* options, bool* rotatable)
```

**Description**

Obtains whether the component rotates along the motion path.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md)* options | Pointer to [ArkUI_MotionPathOptions](capi-arkui-nativemodule-arkui-motionpathoptions.md). |
| bool* rotatable | Pointer to the variable used to receive the value of **rotatable**, which indicates whether the component rotates along the path. The value **true** means that the component rotates along the path, and **false** means that the component does not rotate along the path. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_ShadowOptions_Create()

```c
OH_ArkUI_ShadowOptions* OH_ArkUI_ShadowOptions_Create()
```

**Description**

Creates a shadow option object. When the object is no longer in use, call [OH_ArkUI_ShadowOptions_Destroy](capi-native-type-visual-h.md#oh_arkui_shadowoptions_destroy) to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_ShadowOptions*](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) | Pointer to the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object. |

### OH_ArkUI_ShadowOptions_Destroy()

```c
void OH_ArkUI_ShadowOptions_Destroy(OH_ArkUI_ShadowOptions* options)
```

**Description**

Destroys the shadow option object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | Pointer to the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object. |

### OH_ArkUI_ShadowOptions_SetRadius()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetRadius(OH_ArkUI_ShadowOptions* options, float radius)
```

**Description**

Sets the blur radius for the shadow options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | Pointer to the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object. |
| float radius | Blur radius of the shadow, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_ShadowOptions_GetRadius()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetRadius(OH_ArkUI_ShadowOptions* options, float* radius)
```

**Description**

Obtains the blur radius for the shadow options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | Pointer to the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object. |
| float* radius | Pointer to the blur radius of the shadow, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_ShadowOptions_SetType()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetType(OH_ArkUI_ShadowOptions* options, ArkUI_ShadowType type)
```

**Description**

Sets the shadow type for the shadow options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | Pointer to the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object. |
| [ArkUI_ShadowType](capi-native-type-visual-h.md#arkui_shadowtype) type | Shadow type ([ArkUI_ShadowType](capi-native-type-visual-h.md#arkui_shadowtype)). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_ShadowOptions_GetType()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetType(OH_ArkUI_ShadowOptions* options, ArkUI_ShadowType* type)
```

**Description**

Obtains the shadow type for the shadow options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | Pointer to the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object. |
| [ArkUI_ShadowType](capi-native-type-visual-h.md#arkui_shadowtype)* type | Shadow type ([ArkUI_ShadowType](capi-native-type-visual-h.md#arkui_shadowtype)). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_ShadowOptions_SetColor()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetColor(OH_ArkUI_ShadowOptions* options, uint32_t color)
```

**Description**

Sets the shadow color for the shadow options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | Pointer to the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object. |
| uint32_t color | Shadow color, in 0xARGB format. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_ShadowOptions_GetColor()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetColor(OH_ArkUI_ShadowOptions* options, uint32_t* color)
```

**Description**

Obtains the shadow color for the shadow options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | Pointer to the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object. |
| uint32_t* color | Pointer to the shadow color, in 0xARGB format. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_ShadowOptions_SetOffsetX()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetOffsetX(OH_ArkUI_ShadowOptions* options, float offsetX)
```

**Description**

Sets the shadow offset on the x-axis.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | Pointer to the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object. |
| float offsetX | Shadow offset on the x-axis, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_ShadowOptions_GetOffsetX()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetOffsetX(OH_ArkUI_ShadowOptions* options, float* offsetX)
```

**Description**

Obtains the shadow offset on the x-axis.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | Pointer to the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object. |
| float* offsetX | Pointer to the shadow offset on the x-axis, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_ShadowOptions_SetOffsetY()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetOffsetY(OH_ArkUI_ShadowOptions* options, float offsetY)
```

**Description**

Sets the shadow offset on the y-axis.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | Pointer to the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object. |
| float offsetY | Shadow offset on the y-axis, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_ShadowOptions_GetOffsetY()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetOffsetY(OH_ArkUI_ShadowOptions* options, float* offsetY)
```

**Description**

Obtains the shadow offset on the y-axis.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | Pointer to the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object. |
| float* offsetY | Pointer to the shadow offset on the y-axis, in vp. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_ShadowOptions_SetFill()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_SetFill(OH_ArkUI_ShadowOptions* options, bool isFill)
```

**Description**

Sets whether to fill a component with a shadow.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | Pointer to the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object. |
| bool isFill | Whether to fill a component with a shadow. **true** means to fill a component with a shadow, and **<br>false** means the opposite. The default value is **false**. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_ShadowOptions_GetFill()

```c
ArkUI_ErrorCode OH_ArkUI_ShadowOptions_GetFill(OH_ArkUI_ShadowOptions* options, bool* isFill)
```

**Description**

Obtains whether a component is filled with a shadow.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md)* options | Pointer to the [OH_ArkUI_ShadowOptions](capi-arkui-nativemodule-oh-arkui-shadowoptions.md) object. |
| bool* isFill | Pointer to the **isFill** parameter indicating whether a component is filled with a shadow. **true**<br>means that a component is filled with a shadow, and **false** means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4ScaleOptions_Create()

```c
ArkUI_Matrix4ScaleOptions* OH_ArkUI_Matrix4ScaleOptions_Create()
```

**Description**

Creates a pointer to the scaling parameter object for matrix operations. In the newly created object, the default scaling coefficients in the x, y, and z directions are 1. The default values of **centerX** and **centerY**<br>of the transformation center point are 0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_Matrix4ScaleOptions*](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md) | Pointer to the new [ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md) object. |

### OH_ArkUI_Matrix4ScaleOptions_Dispose()

```c
void OH_ArkUI_Matrix4ScaleOptions_Dispose(ArkUI_Matrix4ScaleOptions* options)
```

**Description**

Disposes of the pointer to the scaling parameter object for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the [ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md) object to be destroyed. |

### OH_ArkUI_Matrix4ScaleOptions_SetX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetX(ArkUI_Matrix4ScaleOptions* options, const float scaleX)
```

**Description**

Sets the scaling factor in the x direction of the scaling parameter object for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the scaling parameter object for matrix operations. |
| const float scaleX | Scaling factor in the x direction. The value range is (-∞, +∞). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4ScaleOptions_GetX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetX(const ArkUI_Matrix4ScaleOptions* options, float* scaleX)
```

**Description**

Obtains the scaling factor in the x direction of the scaling parameter object for matrix operations. If the value of x is not set, the default value of the scaling factor in the x direction is 1.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the scaling parameter object for matrix operations. |
| float* scaleX | Pointer to the scaling factor in the x direction. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4ScaleOptions_SetY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetY(ArkUI_Matrix4ScaleOptions* options, const float scaleY)
```

**Description**

Sets the scaling factor in the y direction of the scaling parameter object for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the scaling parameter object for matrix operations. |
| const float scaleY | Scaling factor in the y direction. The value range is (-∞, +∞). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4ScaleOptions_GetY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetY(const ArkUI_Matrix4ScaleOptions* options, float* scaleY)
```

**Description**

Obtains the scaling factor in the y direction of the scaling parameter object for matrix operations. If the value of y is not set, the default value of the scaling factor in the y direction is 1.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the scaling parameter object for matrix operations. |
| float* scaleY | Pointer to the scaling factor in the y direction. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4ScaleOptions_SetZ()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetZ(ArkUI_Matrix4ScaleOptions* options, const float scaleZ)
```

**Description**

Sets the scaling factor in the z direction of the scaling parameter object for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the scaling parameter object for matrix operations. |
| const float scaleZ | Scaling factor in the z direction. The value range is (-∞, +∞). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4ScaleOptions_GetZ()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetZ(const ArkUI_Matrix4ScaleOptions* options, float* scaleZ)
```

**Description**

Obtains the scaling factor in the z direction of the scaling parameter object for matrix operations. If the value of z is not set, the default value of the scaling factor in the z direction is 1.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the scaling parameter object for matrix operations. |
| float* scaleZ | Pointer to the scaling factor in the z direction. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4ScaleOptions_SetCenterX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetCenterX(ArkUI_Matrix4ScaleOptions* options, const float centerX)
```

**Description**

Sets the x coordinate of the transformation center point of the scaling parameter object for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the scaling parameter object for matrix operations. |
| const float centerX | X-coordinate of the transformation center point. The value range is (-∞, +∞). **0** indicates that there is no x-axis offset based on the transformation center. The unit is px. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4ScaleOptions_GetCenterX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetCenterX(const ArkUI_Matrix4ScaleOptions* options, float* centerX)
```

**Description**

Obtains the x coordinate of the transformation center point of the scaling parameter object for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the scaling parameter object for matrix operations. |
| float* centerX | Pointer to the X-coordinate of the transformation center point. The unit is px. The default value is *<br>**0**. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4ScaleOptions_SetCenterY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_SetCenterY(ArkUI_Matrix4ScaleOptions* options, const float centerY)
```

**Description**

Sets the y coordinate of the transformation center point of the scaling parameter object for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the scaling parameter object for matrix operations. |
| const float centerY | Y-coordinate of the transformation center point. The value range is (-∞, +∞). **0** indicates that there is no y-axis offset based on the transformation center. The unit is px. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4ScaleOptions_GetCenterY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4ScaleOptions_GetCenterY(const ArkUI_Matrix4ScaleOptions* options, float* centerY)
```

**Description**

Obtains the y coordinate of the transformation center point of the scaling parameter object for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* options | Pointer to the scaling parameter object for matrix operations. |
| float* centerY | Pointer to the Y-coordinate of the transformation center point. The unit is px. The default value is *<br>**0**. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4RotationOptions_Create()

```c
ArkUI_Matrix4RotationOptions* OH_ArkUI_Matrix4RotationOptions_Create()
```

**Description**

Creates a pointer to the rotation parameter object for matrix operations. In the newly created object, the default value of an x-axis offset (**centerX**) of a single matrix transformation center point relative to a component transformation center point, the default value of a y-axis offset (**centerY**) of the single matrix transformation center point relative to the component transformation center point, and the default value of a rotation angle (**angle**) are 0. If none of the direction vectors in the x, y, and z directions is specified, the value is equivalent to x=0, y=0, and z=1, indicating rotation around the z-axis. Once any of the direction vectors in the x, y, and z directions is specified, the unspecified values are equivalent to 0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_Matrix4RotationOptions*](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md) | Pointer to the new [ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md) object. |

### OH_ArkUI_Matrix4RotationOptions_Dispose()

```c
void OH_ArkUI_Matrix4RotationOptions_Dispose(ArkUI_Matrix4RotationOptions* options)
```

**Description**

Disposes of the pointer to the rotation parameter object for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the rotation parameter object for matrix operations. |

### OH_ArkUI_Matrix4RotationOptions_SetX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetX(ArkUI_Matrix4RotationOptions* options, const float x)
```

**Description**

Sets the direction vector in the x direction of the rotation parameter object for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the rotation parameter object for matrix operations. |
| const float x | Value of the direction vector in the x direction. The value range is (-∞, +∞). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4RotationOptions_GetX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetX(const ArkUI_Matrix4RotationOptions* options, float* x)
```

**Description**

Obtains the direction vector in the x direction of the rotation parameter object for matrix operations. If the value of x has never been set, the value is undefined. In this case, [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the rotation parameter object for matrix operations. |
| float* x | Pointer to the value of the direction vector in the x direction. If the value of x has never been set, the value is undefined. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4RotationOptions_SetY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetY(ArkUI_Matrix4RotationOptions* options, const float y)
```

**Description**

Sets the direction vector in the y direction of the rotation parameter object for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the rotation parameter object for matrix operations. |
| const float y | Value of the direction vector in the y direction. The value range is (-∞, +∞). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4RotationOptions_GetY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetY(const ArkUI_Matrix4RotationOptions* options, float* y)
```

**Description**

Obtains the direction vector in the y direction of the rotation parameter object for matrix operations. If the value of y has never been set, the value is undefined. In this case, [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the rotation parameter object for matrix operations. |
| float* y | Pointer to the value of the direction vector in the y direction. If the value of y has never been set, the value is undefined. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4RotationOptions_SetZ()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetZ(ArkUI_Matrix4RotationOptions* options, const float z)
```

**Description**

Sets the direction vector in the z direction of the rotation parameter object for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the rotation parameter object for matrix operations. |
| const float z | Value of the direction vector in the z direction. The value range is (-∞, +∞). |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4RotationOptions_GetZ()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetZ(const ArkUI_Matrix4RotationOptions* options, float* z)
```

**Description**

Obtains the direction vector in the z direction of the rotation parameter object for matrix operations. If the value of z has never been set, the value is undefined. In this case, [ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) is returned.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the rotation parameter object for matrix operations. |
| float* z | Pointer to the value of the direction vector in the z direction. If the value of z has never been set, the value is undefined. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4RotationOptions_SetAngle()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetAngle(ArkUI_Matrix4RotationOptions* options, const float angle)
```

**Description**

Sets the rotation angle in the rotation parameter object for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the rotation parameter object for matrix operations. |
| const float angle | Value of the rotation angle. The value range is (-∞, +∞). The unit is degree. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4RotationOptions_GetAngle()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetAngle(const ArkUI_Matrix4RotationOptions* options, float* angle)
```

**Description**

Obtains the rotation angle in the rotation parameter object for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the rotation parameter object for matrix operations. |
| float* angle | Pointer to the value of the rotation angle. The unit is degree. If the angle has never been set, the default value is **0**. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4RotationOptions_SetCenterX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetCenterX(ArkUI_Matrix4RotationOptions* options, const float centerX)
```

**Description**

Sets the x-axis offset of a single matrix transformation center point relative to a component transformation center point.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the rotation parameter object for matrix operations. |
| const float centerX | X-axis offset of a single matrix transformation center point relative to a component transformation center point. The value range is (-∞, +∞). **0** indicates that there is no x-axis offset based on the transformation center. The unit is px. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4RotationOptions_GetCenterX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetCenterX(const ArkUI_Matrix4RotationOptions* options, float* centerX)
```

**Description**

Obtains the x-axis offset of a single matrix transformation center point relative to a component transformation center point.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the rotation parameter object for matrix operations. |
| float* centerX | Pointer to the x-axis offset of a single matrix transformation center point relative to a component transformation center point. The unit is px. If **centerX** has never been set, the default value is **0**. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4RotationOptions_SetCenterY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_SetCenterY(ArkUI_Matrix4RotationOptions* options, const float centerY)
```

**Description**

Sets the y-axis offset of a single matrix transformation center point relative to a component transformation center point.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the rotation parameter object for matrix operations. |
| const float centerY | Y-axis offset of a single matrix transformation center point relative to a component transformation center point. The value range is (-∞, +∞). **0** indicates that there is no y-axis offset based on the transformation center. The unit is px. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4RotationOptions_GetCenterY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4RotationOptions_GetCenterY(const ArkUI_Matrix4RotationOptions* options, float* centerY)
```

**Description**

Obtains the y-axis offset of a single matrix transformation center point relative to a component transformation center point.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* options | Pointer to the rotation parameter object for matrix operations. |
| float* centerY | Pointer to the y-axis offset of a single matrix transformation center point relative to a component transformation center point. The unit is px. If **centerY** has never been set, the default value is **0**. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul>curs. |

### OH_ArkUI_Matrix4TranslationOptions_Create()

```c
ArkUI_Matrix4TranslationOptions* OH_ArkUI_Matrix4TranslationOptions_Create()
```

**Description**

Creates a pointer to a translation object for matrix operations. In the newly created object, the default translation distances on the x, y, and z axes are 0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_Matrix4TranslationOptions*](capi-arkui-nativemodule-arkui-matrix4translationoptions.md) | Pointer to the new [ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md) object. |

### OH_ArkUI_Matrix4TranslationOptions_Dispose()

```c
void OH_ArkUI_Matrix4TranslationOptions_Dispose(ArkUI_Matrix4TranslationOptions* options)
```

**Description**

Disposes of a pointer to a translation object for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md)* options | Pointer to the [ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md) object to be disposed. |

### OH_ArkUI_Matrix4TranslationOptions_SetX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_SetX(ArkUI_Matrix4TranslationOptions* options, const float x)
```

**Description**

Sets the translation value of a translation object on the x-axis for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md)* options | Pointer to the translation parameter object for matrix operations. |
| const float x | Translation value on the x-axis. The value range is (-∞, +∞). The unit is px. If the value of x has never been set, the default value is **0**. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4TranslationOptions_GetX()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_GetX(const ArkUI_Matrix4TranslationOptions* options, float* x)
```

**Description**

Obtains the translation value of a translation object on the x-axis for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md)* options | Pointer to the translation parameter object for matrix operations. |
| float* x | Pointer to the translation value on the x-axis. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4TranslationOptions_SetY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_SetY(ArkUI_Matrix4TranslationOptions* options, const float y)
```

**Description**

Sets the translation value of a translation object on the y-axis for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md)* options | Pointer to the translation parameter object for matrix operations. |
| const float y | Translation value on the y-axis. The value range is (-∞, +∞). The unit is px. If the value of y has never been set, the default value is **0**. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4TranslationOptions_GetY()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_GetY(const ArkUI_Matrix4TranslationOptions* options, float* y)
```

**Description**

Obtains the translation value of a translation object on the y-axis for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md)* options | Pointer to the translation parameter object for matrix operations. |
| float* y | Pointer to the translation value on the y-axis. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4TranslationOptions_SetZ()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_SetZ(ArkUI_Matrix4TranslationOptions* options, const float z)
```

**Description**

Sets the translation value of a translation object on the z-axis for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md)* options | Pointer to the translation parameter object for matrix operations. |
| const float z | Translation value on the z-axis. The value range is (-∞, +∞). The unit is px. If the value of z has never been set, the default value is **0**. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul>. |

### OH_ArkUI_Matrix4TranslationOptions_GetZ()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4TranslationOptions_GetZ(const ArkUI_Matrix4TranslationOptions* options, float* z)
```

**Description**

Obtains the translation value of a translation object on the z-axis for matrix operations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md)* options | Pointer to the translation parameter object for matrix operations. |
| float* z | Pointer to the translation value on the z-axis. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4_CreateIdentity()

```c
ArkUI_Matrix4* OH_ArkUI_Matrix4_CreateIdentity()
```

**Description**

Creates a fourth-order identity matrix object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_Matrix4*](capi-arkui-nativemodule-arkui-matrix4.md) | Pointer to the created fourth-order identity matrix object. |

### OH_ArkUI_Matrix4_CreateByElements()

```c
ArkUI_Matrix4* OH_ArkUI_Matrix4_CreateByElements(const float* elements)
```

**Description**

Creates a fourth-order matrix object by specifying each element of the matrix.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const float* elements | Pointer to the array of expected matrix element data. The array length must be greater than or equal to 16. This parameter cannot be set to a null pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_Matrix4*](capi-arkui-nativemodule-arkui-matrix4.md) | Pointer to the created fourth-order matrix object. If the elements pointer is a null pointer, a null      value is returned. |

### OH_ArkUI_Matrix4_Dispose()

```c
void OH_ArkUI_Matrix4_Dispose(ArkUI_Matrix4* matrix)
```

**Description**

Disposes of a fourth-order matrix object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the fourth-order matrix object to be disposed. |

### OH_ArkUI_Matrix4_Copy()

```c
ArkUI_Matrix4* OH_ArkUI_Matrix4_Copy(const ArkUI_Matrix4* matrix)
```

**Description**

Creates a copy of a fourth-order matrix object. It is used to perform operations on the same matrix to obtain different matrix objects.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the original fourth-order matrix object. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_Matrix4*](capi-arkui-nativemodule-arkui-matrix4.md) | Pointer to the created fourth-order matrix object. |

### OH_ArkUI_Matrix4_Invert()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_Invert(ArkUI_Matrix4* matrix)
```

**Description**

Performs an inverse matrix transformation on the input matrix.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the fourth-order matrix object to be inverted. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4_Combine()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_Combine(ArkUI_Matrix4* oriMatrix, const ArkUI_Matrix4* anotherMatrix)
```

**Description**

Combines another matrix with the original matrix and stores the resulting matrix in **oriMatrix**. The resulting matrix is equivalent to first applying the transformation of **oriMatrix** and then applying the transformation of **anotherMatrix**. This function modifies the **oriMatrix** object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* oriMatrix | Pointer to the original fourth-order matrix object. |
| [const ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* anotherMatrix | Pointer to another matrix object to be combined. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4_Translate()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_Translate(ArkUI_Matrix4* matrix, const ArkUI_Matrix4TranslationOptions* translate)
```

**Description**

Applies a translation transformation to the original matrix to obtain the translated matrix. Each translation transformation is cumulative on the previous matrix. The input matrix object is modified after the transformation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the fourth-order matrix object to be translated. |
| [const ArkUI_Matrix4TranslationOptions](capi-arkui-nativemodule-arkui-matrix4translationoptions.md)* translate | Pointer to the translation object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4_Scale()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_Scale(ArkUI_Matrix4* matrix, const ArkUI_Matrix4ScaleOptions* scale)
```

**Description**

Applies a scaling transformation to the original matrix to obtain the scaled matrix. Each scaling transformation is cumulative on the previous matrix. This function modifies the input matrix object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the fourth-order matrix object to be scaled. |
| [const ArkUI_Matrix4ScaleOptions](capi-arkui-nativemodule-arkui-matrix4scaleoptions.md)* scale | Pointer to the scaling object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4_Rotate()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_Rotate(ArkUI_Matrix4* matrix, const ArkUI_Matrix4RotationOptions* rotate)
```

**Description**

Applies a rotation transformation to the original matrix to obtain the rotated matrix. Each rotation transformation is cumulative on the previous matrix. This function modifies the input matrix object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the fourth-order matrix object to be rotated. |
| [const ArkUI_Matrix4RotationOptions](capi-arkui-nativemodule-arkui-matrix4rotationoptions.md)* rotate | Pointer to the rotation object. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4_Skew()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_Skew(ArkUI_Matrix4* matrix, const float skewX, const float skewY)
```

**Description**

Applies a skew transformation to the original matrix to obtain the skewed matrix. Each skew transformation is cumulative on the previous matrix. The input matrix object is modified after the transformation.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the fourth-order matrix object to be skewed. |
| const float skewX | Skew coefficient in the x direction. |
| const float skewY | Skew coefficient in the y direction. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4_TransformPoint()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_TransformPoint(const ArkUI_Matrix4* matrix, const ArkUI_PointF* oriPoint, ArkUI_PointF* result)
```

**Description**

Calculates the new coordinate position of a point after it is transformed by a matrix.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the fourth-order matrix object. |
| [const ArkUI_PointF](capi-arkui-nativemodule-arkui-pointf.md)* oriPoint | Pointer to the original coordinate point. |
| [ArkUI_PointF](capi-arkui-nativemodule-arkui-pointf.md)* result | Pointer to the result point. This parameter cannot be set to a null pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4_SetPolyToPoly()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_SetPolyToPoly(ArkUI_Matrix4* matrix, const ArkUI_PointF* src, const ArkUI_PointF* dst, const uint32_t pointCount)
```

**Description**

Maps the vertex coordinates of one polygon to the vertex coordinates of another polygon and calculates the required matrix.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the fourth-order matrix object, which is used to store the result matrix. |
| [const ArkUI_PointF](capi-arkui-nativemodule-arkui-pointf.md)* src | Pointer to the array of original polygon coordinate points. The array length must be at least **pointCount**. |
| [const ArkUI_PointF](capi-arkui-nativemodule-arkui-pointf.md)* dst | Pointer to the array of mapped polygon coordinate points. The array length must be at least **pointCount**. |
| const uint32_t pointCount | Number of polygon points, which must be one of the values 0, 1, 2, 3, or 4. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |

### OH_ArkUI_Matrix4_GetElements()

```c
ArkUI_ErrorCode OH_ArkUI_Matrix4_GetElements(const ArkUI_Matrix4* matrix, float* result)
```

**Description**

Obtains the 16 elements of the fourth-order matrix.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md)* matrix | Pointer to the fourth-order matrix object. |
| float* result | Pointer to an array that can hold 16 floating-point numbers. This parameter cannot be set to a null pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | <ul>           <li>[ARKUI_ERROR_CODE_NO_ERROR](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if the operation is successful.</li>          <li>[ARKUI_ERROR_CODE_PARAM_INVALID](../../apis-arkdata/c-apis/capi-error-code-h.md#arkui_errorcode) if a parameter exception occurs.</li>          </ul> |


