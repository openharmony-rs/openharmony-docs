# Error Codes of Logic Components
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangjunman1-->
<!--Designer: @sunbees-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=d89c4be0c26be57dcac6e3a0bb8b7f968642aa19 translatedAt=2026-08-29T09:23:40.455Z pushedAt=2026-08-31T06:05:24.180Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 103801 Failed to Generate a Key Value for ForEach

**Error Message**

use of default id generator function not possible on provided data structure.Need to specify id generator function (ForEach 3rd parameter).Application Error!

**Description**

This error code is reported when the default key value generation function of [ForEach](./arkui-ts/ts-rendering-control-foreach.md) cannot generate key values based on the provided data structure.

**Possible Causes**

The data source you provide cannot generate key values. For example, the data item type is not supported by the key value generation function.

**Solution**

Modify the data source object or manually implement a key value generation function. For details, see [Key Generation Rules](../../ui/rendering-control/arkts-rendering-control-foreach.md#key-generation-rules).

## 103802 Failed to Render the Subnode

**Error Message**

lacks mandatory '.each' attribute function, i.e. has no default item builder. Application error!

**Description**

This error code is reported when the [each](./arkui-ts/ts-rendering-control-repeat.md#each) attribute is missing.

**Possible Causes**

You do not set the `each` attribute when using the **Repeat** component, causing the component to lack the default child node builder function.

**Solution**

Set `each` to provide the default child node builder function.

## 103803 Invalid Index Value

**Error Message**

\_\_RepeatVirtualScrollImpl (eg:1) onCreateNode: for index=(eg:7) with data array length (eg:5), totalCount= (eg:5) out of range error.

**Description**

This error code is reported when the node index is greater than or equal to the length of the data source.

**Possible Causes**

The length of the data source is set incorrectly, or the data source is added or deleted during node creation.

**Solution**

Set the index and data source length correctly to ensure that the index is not greater than or equal to the data source length. Avoid adding or deleting data sources during node creation.

## 103804 Invalid Operation During Lazy Loading of Repeat

**Error Message**

onLazyLoading function executed illegal operation.

**Description**

This error code is reported when invalid data operations are performed in the [lazy loading](../../ui/rendering-control/arkts-new-rendering-control-repeat.md#lazy-loading-capability) scenario.

**Possible Causes**

You call a data operation method without following the data operation constraints of the lazy loading API.

**Solution**

Call the method by following the data operation constraints of the lazy loading API. For details, see [Precise Lazy Loading](../../ui/rendering-control/arkts-new-rendering-control-repeat.md#precise-lazy-loading).

## 103805 Failed to Generate the Default Key Value

**Error Message**

Repeat(). Default key gen failed. Application Error!

**Description**

This error code is reported when the default [key value](../../ui/rendering-control/arkts-new-rendering-control-repeat.md#key-generation-rules) of [Repeat](./arkui-ts/ts-rendering-control-repeat.md) fails to be generated.

**Possible Causes**

The data source you set cannot generate a unique key value.

**Solution**

Modify the data source so that it can generate a unique key value, or manually implement a key-value generation function. For details, see [Key Generation Rules](../../ui/rendering-control/arkts-new-rendering-control-repeat.md#key-generation-rules).