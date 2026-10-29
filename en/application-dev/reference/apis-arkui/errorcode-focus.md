# Focus Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9c92183287fa23162e04874223c3b068eb1f8a4d translatedAt=2026-10-15T10:44:11.737Z pushedAt=2026-10-16T03:04:38.607Z -->

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

This error code is reported when the ID passed in points to a component that does not exist or is not mounted to the component tree. This error code is of the string type.

**Possible Causes**

- The ID passed in does not exist or points to an incorrect component, or the component corresponding to the ID has been destroyed.

- Focus is requested for a component that is not focusable. For details about such components, see [Component Focusability](../../ui/arkts-common-events-focus-event.md#component-focusability).

**Solution**

Use the correct ID or component, and ensure that the component is mounted, visible, and focusable.
