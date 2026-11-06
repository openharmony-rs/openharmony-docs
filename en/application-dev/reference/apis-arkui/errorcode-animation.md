# Animation and Visual Effect Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=7d5188956273f69fd8f9bca5f8c28b1536d0dc21 translatedAt=2026-11-03T08:44:02.124Z pushedAt=2026-11-04T07:29:56.909Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 106211 Attribute Not Found

**Error Message**

The attribute was not found because it was not set before.

**Description**

This error code is reported when the attribute is not found because it was not set before.

**Possible Causes**

When an API is called to obtain an attribute value, the attribute was not set through the corresponding setting API before. For example, when [OH_ArkUI_NativeModule_PropertyAnimation_GetFromValue](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_getfromvalue) is called, the attribute was not set through [OH_ArkUI_NativeModule_PropertyAnimation_SetFromValue](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_setfromvalue) before.

**Solution**

Set the attribute through the corresponding setting API first, and then call the API to obtain the attribute value.

## 106212 Invalid Sub-animation Parameter

**Error Message**

The sub-animation parameter is invalid.

**Description**

This error code is reported when the sub-animation parameter added to the animation group is invalid.

**Possible Causes**

1. When a property animation is added through [OH_ArkUI_NativeModule_AnimationGroup_AddPropertyAnimation](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_addpropertyanimation): the end value is not set for the property animation ([OH_ArkUI_NativeModule_PropertyAnimation_SetToValue](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_settovalue) is not called).
2. When a keyframe animation is added through [OH_ArkUI_NativeModule_AnimationGroup_AddKeyframeAnimation](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_addkeyframeanimation): the keyframe time points are in an incorrect order (a subsequent keyframe time point is smaller than the previous one), or the [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) values corresponding to [propertyType](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_create) passed in during the keyframe animation creation are not completely set through [OH_ArkUI_NativeModule_KeyframeAnimation_SetValue](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setvalue) or [OH_ArkUI_NativeModule_KeyframeAnimation_SetValues](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setvalues).
3. When an animation group is registered through [OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup): the sub-animation does not have a target render node set, and the animation group does not have a default target render node set either, so the target node cannot be resolved.

**Solution**

1. Ensure that the end value is set for the property animation through [OH_ArkUI_NativeModule_PropertyAnimation_SetToValue](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_settovalue).
2. Ensure that the [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) value corresponding to the **propertyType** is set for each keyframe of the keyframe animation through [OH_ArkUI_NativeModule_KeyframeAnimation_SetValue](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setvalue) or [OH_ArkUI_NativeModule_KeyframeAnimation_SetValues](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setvalues). When setting keyframe time points through [OH_ArkUI_NativeModule_KeyframeAnimation_SetKeyTime](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_setkeytime), ensure that the keyframe time points are in the correct order (a subsequent keyframe time point is not smaller than the previous one).
3. Set the target render node for the sub-animation through [OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_settargetnode), [OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_settargetnode), or [OH_ArkUI_NativeModule_PathAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_settargetnode), or set the default target render node of the animation group through [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode).

## 106213 Specified Animation Group Not Found on the UIContext

**Error Message**

The animation group is not found on the UIContext.

**Description**

This error code is reported when the animation group identified by the specified key is not found on the UIContext.

**Possible Causes**

1. A key that has not been registered through [OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup) is used to search for the animation group.
2. The animation group has finished playing and is automatically removed by the system after the animation ends.

**Solution**

Confirm that the key has been registered through [OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup) and that the animation group has not ended yet. After the animation group ends naturally, [OH_ArkUI_NativeModule_FinishAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_finishanimationgroup) is called, or the target node is destroyed, the animation end callback is triggered, and the system automatically removes the animation group after the callback is executed. If necessary, use [OH_ArkUI_NativeModule_HasAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_hasanimationgroup) to check whether the animation group exists.

## 106214 Re-entrant Call to Animation Group APIs Detected on the Same Thread

**Error Message**

A re-entrant call to animation group APIs is detected on the same thread.

**Description**

This error code is reported in the following scenario: On the same thread, while a call to an animation group API has not yet returned, the thread makes a nested call to another animation group API.

**Possible Causes**

On the same thread, while a call to an animation group API has not yet returned, the thread makes a nested call to another animation group API.

**Solution**

Ensure that the next call to an animation group API is made only after the previous call has fully returned, and avoid nested calls to animation group APIs on the same thread.

## 106215 Animation Group Not in the Required State for the Operation

**Error Message**

The animation group is not in the required state for the operation.

**Description**

This error code is reported when the current state of the animation group does not meet the state required for the API call.

**Possible Causes**

1. When [OH_ArkUI_NativeModule_PauseAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_pauseanimationgroup) is called, the animation group is not in the [OH_ARKUI_ANIMATION_GROUP_STATE_RUNNING](capi-native-type-visual-h.md#oh_arkui_animationgroupstate) state.
2. When [OH_ArkUI_NativeModule_ResumeAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_resumeanimationgroup) is called, the animation group is not in the [OH_ARKUI_ANIMATION_GROUP_STATE_PAUSED](capi-native-type-visual-h.md#oh_arkui_animationgroupstate) state.
3. When [OH_ArkUI_NativeModule_FinishAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_finishanimationgroup) is called, the animation group is not in the [OH_ARKUI_ANIMATION_GROUP_STATE_RUNNING](capi-native-type-visual-h.md#oh_arkui_animationgroupstate) or [OH_ARKUI_ANIMATION_GROUP_STATE_PAUSED](capi-native-type-visual-h.md#oh_arkui_animationgroupstate) state.

**Solution**

Query the current state of the animation group through [OH_ArkUI_NativeModule_GetAnimationGroupState](capi-native-animate-h.md#oh_arkui_nativemodule_getanimationgroupstate), and call the corresponding API only after confirming that the state is correct.

## 106216 Resolved Target Node Not Belong to the UIContext of the Context Passed for Registering the Animation Group

**Error Message**

The resolved target node does not belong to the same UIContext as the context parameter.

**Description**

This error code is reported when the resolved target node does not belong to the same UIContext as the context.

**Possible Causes**

When an animation group is registered through [OH_ArkUI_NativeModule_AddAnimationGroup](capi-native-animate-h.md#oh_arkui_nativemodule_addanimationgroup), the UIContext to which the target render node resolved by the sub-animation belongs is inconsistent with the UIContext to which the context parameter belongs.

**Solution**

Ensure that the target render node set for the sub-animation through [OH_ArkUI_NativeModule_PropertyAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_propertyanimation_settargetnode), [OH_ArkUI_NativeModule_KeyframeAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_keyframeanimation_settargetnode), or [OH_ArkUI_NativeModule_PathAnimation_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_pathanimation_settargetnode), or the default target render node of the animation group set through [OH_ArkUI_NativeModule_AnimationGroup_SetTargetNode](capi-native-animate-h.md#oh_arkui_nativemodule_animationgroup_settargetnode) belongs to the same UIContext as the context passed when registering the animation group.

<!--no_check-->