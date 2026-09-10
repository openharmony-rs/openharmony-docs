# Focus Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=7011f4d66e76387ef9966b7144aff937ff0dfc5c translatedAt=2026-08-29T09:20:48.475Z pushedAt=2026-08-31T03:00:57.711Z -->

> **NOTE**
>
> The focus error codes describe common issues and handling directions when a component fails to obtain focus, helping you locate focus exceptions and take appropriate measures. Only the error codes specific to this module are described below. For details about the universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 150001 Component Not Focusable

**Error Message**

the component cannot be focused.

**Description**

This error code is reported when the current component is not focusable. This error code is of the string type.

**Possible Causes**

The component is not focusable by default, or you set the **focusable** attribute of the component to **false**. For details about the focus acquisition capability, see [Component Focusability](../../ui/arkts-common-events-focus-event.md#component-focusability).

**Solution**

Check whether the current component is focusable and whether **focusable** is set to **true**.

## 150002 Ancestor Component Not Focusable

**Error Message**

This component has an unfocusable ancestor.

**Description**

This error code is reported when an ancestor of the current component is not focusable. This error code is of the string type.

**Possible Causes**

The ancestor component is not focusable by default, or you set the **focusable** attribute of the component to **false**. For details about the focus acquisition capability, see [Component Focusability](../../ui/arkts-common-events-focus-event.md#component-focusability).

**Solution**

Check whether the ancestor component is focusable and whether **focusable** is set to **true**.

## 150003 Component Does Not Exist

**Error Message**

the component is not on tree or does not exist.

**Description**

The ID passed in points to a component that does not exist or is not mounted to the component tree. This error code is of the string type.

**Possible Causes**

- The ID passed in does not exist or points to an incorrect component, or the component corresponding to the ID has been destroyed.

- Focus is requested for a component that is not focusable. For details about such components, see [Component Focusability](../../ui/arkts-common-events-focus-event.md#component-focusability).

**Solution**

Use the correct ID or node, and ensure that the node is mounted, visible, and focusable.
