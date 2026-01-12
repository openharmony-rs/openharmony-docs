# Drag Event Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 190001 Data Not Found

**Error Message**

Data not found.

**Description**

This error code is reported when no data has been obtained using the [getData](./arkui-ts/ts-universal-events-drag-drop.md#getdata10) API of **DragEvent**.

**Possible Causes**

The **DragEvent** data has not been obtained.

**Solution**

N/A

## 190002 Data Retrieval Error

**Error Message**

Data error.

**Description**

This error code is reported when the data obtained via the [getData](./arkui-ts/ts-universal-events-drag-drop.md#getdata10) API of **DragEvent** is incorrect.

**Possible Causes**

The obtained data is incorrect.

**Solution**

N/A

## 190003 Operation Not Allowed in the Current Phase

**Error Message**

Operation not allowed for current phase.

**Description**

This error code is reported when you call an API that is only supported during the [onDrop](./arkui-ts/ts-universal-events-drag-drop.md#ondrop) phase outside of that phase.

**Possible Causes**

The operation is not allowed in the current phase.

**Solution**

Call the corresponding API in the [onDrop](./arkui-ts/ts-universal-events-drag-drop.md#ondrop) phase.

## 190004 Operation Failed

**Error Message**

Operation failed.

**Description**

This error code is reported if the [cancelDataLoading](./arkts-apis-uicontext-dragcontroller.md#canceldataloading15) API is called when data has not been loaded or loading is complete.

**Possible Causes**

The API is called at a wrong time.

**Solution**

Call the [cancelDataLoading](./arkts-apis-uicontext-dragcontroller.md#canceldataloading15) API during data loading.
