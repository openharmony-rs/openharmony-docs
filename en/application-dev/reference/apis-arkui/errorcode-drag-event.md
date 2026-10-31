# Drag Event Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=7011f4d66e76387ef9966b7144aff937ff0dfc5c translatedAt=2026-08-29T09:19:21.979Z pushedAt=2026-08-31T02:39:52.370Z -->

> **NOTE**
>
> This topic describes the error codes specific to the drag event module, covering common exceptions in data retrieval, operation phases, and data loading, to help you identify the causes of errors and take corresponding measures. For universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 190001 Data Not Found

**Error Message**

Data not found.

**Description**

This error code is reported when you call [getData](./arkui-ts/ts-universal-events-drag-drop.md#getdata10) of **DragEvent** but the data has not been obtained yet. The error code is of the string type.

**Possible Causes**

The **DragEvent** data has not been obtained.

**Solution**

N/A

## 190002 Data Retrieval Error

**Error Message**

Data error.

**Description**

This error code is reported when you call [getData](./arkui-ts/ts-universal-events-drag-drop.md#getdata10) of **DragEvent** but the obtained data is incorrect. The error code is of the string type.

**Possible Causes**

The obtained data is incorrect.

**Solution**

N/A

## 190003 Operation Not Allowed in the Current Phase

**Error Message**

Operation not allowed for current phase.

**Description**

This error code is reported when you call an API that is supported only in the [onDrop](./arkui-ts/ts-universal-events-drag-drop.md#ondrop) phase outside that phase. The error code is of the string type.

**Possible Causes**

The current phase is not the [onDrop](./arkui-ts/ts-universal-events-drag-drop.md#ondrop) phase.

**Solution**

Call the corresponding API in the [onDrop](./arkui-ts/ts-universal-events-drag-drop.md#ondrop) phase.

## 190004 Operation Failed

**Error Message**

Operation failed.

**Description**

This error code is reported when you do not call [cancelDataLoading](./arkts-apis-uicontext-dragcontroller.md#canceldataloading15) during the data loading process after the drag is released. The error code is of the string type.

**Possible Causes**

The API is called at a wrong time.

**Solution**

Call the [cancelDataLoading](./arkts-apis-uicontext-dragcontroller.md#canceldataloading15) API during data loading.
