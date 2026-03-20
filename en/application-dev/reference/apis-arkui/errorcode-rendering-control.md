# Error Codes of Logic Components
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangjunman1-->
<!--Designer: @sunbees-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 103801 Failed to Generate ForEach ID

**Error Message**

use of default id generator function not possible on provided data structure.Need to specify id generator function (ForEach 3rd parameter).Application Error!

**Description**

The default key value generation function of [ForEach](./arkui-ts/ts-rendering-control-foreach.md) cannot generate key values based on the provided data structure.

**Possible Causes**

The data source you provide cannot generate key values. For example, the data item type is incorrect.

**Solution**

Modify the data source object or manually implement a key value generation function. For details, see [Key Generation Rules](../../ui/rendering-control/arkts-rendering-control-foreach.md#key-generation-rules).

## 103802 Failed to Render the Subnode

**Error Message**

lacks mandatory '.each' attribute function, i.e. has no default item builder. Application error!

**Description**

The '[each](./arkui-ts/ts-rendering-control-repeat.md#each)' attribute is missing.

**Possible Causes**

The **'each'** attribute is missing.

**Solution**

Set **'each'** to provide the default component generator.

## 103803 Invalid Index Value

**Error Message**

__RepeatVirtualScrollImpl (eg:1) onCreateNode: for index=(eg:7) with data array length (eg:5), totalCount= (eg:5) out of range error.

**Description**

The node index exceeds the data source length.

**Possible Causes**

The data source length is incorrectly set, or the data source is added or deleted at an improper time.

**Solution**

Set the index and data source length correctly to ensure that the index is less than the data source length.

## 103804 Invalid Operation During Lazy Loading of Repeat

**Error Message**

onLazyLoading function executed illegal operation.

**Description**

Invalid data operations in the [lazy loading](../../ui/rendering-control/arkts-new-rendering-control-repeat.md#lazy-loading-capability) scenario.

**Possible Causes**

The lazy loading method is incorrectly used.

**Solution**

Use the lazy loading method properly. For details, see [Precise Lazy Loading](../../ui/rendering-control/arkts-new-rendering-control-repeat.md#precise-lazy-loading).

## 103805 Failed to Generate the Default Key Value

**Error Message**

Repeat(). Default key gen failed. Application Error!

**Description**

The default [key value](../../ui/rendering-control/arkts-new-rendering-control-repeat.md#key-generation-rules) of [Repeat](./arkui-ts/ts-rendering-control-repeat.md) fails to be generated.

**Possible Causes**

The data source is incorrectly set.

**Solution**

Set the data source properly. For details, see [Key Generation Rules](../../ui/rendering-control/arkts-new-rendering-control-repeat.md#key-generation-rules).
