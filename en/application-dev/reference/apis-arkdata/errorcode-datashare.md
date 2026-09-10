# DataShare Error Codes
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @lvcong_oh-->
<!--Designer: @lvcong_oh-->
<!--Tester: @chenwan188; @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=290991ba34a14252faa986897a6b8fc4198384bb translatedAt=2026-09-04T03:15:55.215Z pushedAt=2026-09-09T09:11:03.694Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 15700000 Internal Error

**Error Message**

Inner error.

**Description**

Internal error.

**Possible Causes**

View the error log to determine the cause of the error. Possible causes include the following:
1. Abnormal internal state.
2. Incorrect use of APIs.
3. Incorrect permission configuration.
4. System errors, such as null pointers, insufficient memory, unexpected restart of data services, I/O errors, IPC exceptions, and JS engine exceptions.

**Solution**

1. Check whether a closed object is reused.
2. Check whether the APIs are called correctly. If not, apply necessary corrections.
3. Check whether the permission configuration is correct.
4. If the problem persists, ask the user to restart or update the application or upgrade the device version.

<!--Del-->
## 15700010 Failed to Create a DataShareHelper

**Error Message**

The DataShareHelper fails to be initialized.

**Description**

The **DataShareHelper** class fails to be created.

**Possible Causes**

1. The **uri** specified in **createDataShareHelper** is incorrect when creating a **DataShareHelper**.
2. The **context** specified in **createDataShareHelper** is incorrect when creating a **DataShareHelper**.
3. When creating **DataShareHelper**, the client does not have the background startup permission configured for starting **DataShareExtension** from the background.

**Solution**

1. Obtain the correct URI.
2. Check that the context of the stage model is used.
3. Check whether the client has the read or write permission on data. Perform the following steps:<br>
    (1) Obtain the data provider bundle name from the URI. For example, the bundle name in **uri = "datashareproxy://com.acts.ohos.data.datasharetest/test"** is **com.acts.ohos.data.datasharetest**.<br>
    (2) Obtain the configuration based on the bundle name. For example, run **bm dump --bundle-name com.acts.ohos.data.datasharetest** to find the **DataShareExtension** configuration and check whether the data visitor has the permission configured in **readPermission** or **writePermission**.
<!--DelEnd-->

## 15700011 URI Does Not Exist

**Error Message**

The URI does not exist.

**Description**

This error code is generated when a template fails to be added or deleted, or an incorrect URI or path is passed in when silent access is enabled or disabled.

**Possible Causes**

1. The input URI is incorrect.
2. The input URI is in incorrect format.

**Solution**

Obtain the correct URI.

<!--Del-->
## 15700012 Data Area Not Exist

**Error Message**

The data area does not exist.

**Description**

This error code is returned when a data update fails.

**Possible Causes**

The input parameter **bundleName** of **publish()** is incorrect.

**Solution**

Obtain the correct **bundleName** value from the DataShare server provider.

## 15700013 DataShareHelper Instance Closed

**Error Message**

The DataShareHelper instance is already closed.

**Description**

This error code is generated when a closed **DataShareHelper** instance is used.

**Possible Causes**

The closed **DataShareHelper** instance cannot be used.

**Solution**

Create a new **DataShareHelper** instance for use.
<!--DelEnd-->

## 15700014 Incorrect Parameters for Shared Configuration

**Error Message**

The parameter format is incorrect or the value range is invalid.

**Description**

1. This error code is reported if the parameter format is incorrect.

2. This error code is reported if the value of the parameter exceeds the expected range.

**Possible Causes**

1. The URI length exceeds 256 bytes.

2. The value length of **proxyData** (proxy data configuration item) exceeds 4096 bytes.

3. The number of elements in the URI array passed by the API exceeds 32.

4. The number of elements in the **proxyData** array passed by the API exceeds 32.

5. URI format verification fails.

**Solution**

1. Check whether the length of a URI in the URI array or **proxyData** array exceeds 256 bytes.

2. Check whether the length of a value in the **proxyData** array exceeds 4096 bytes.

3. Check whether the number of elements in the URI array exceeds 32.

4. Check whether the number of elements in the **proxyData** array exceeds 32.

5. Check whether the URIs in the URI array or **proxyData** array passed in to the API meet the format verification: <br>
    The fixed format of a URI is `"datashareproxy://{bundleName}/{path}"`, where bundleName is the bundle name of the application that publishes the configuration, and path can be filled in arbitrarily.

## 15700015 Access URI Permission Error

**Error Message**

No permission to access the data specified by the URI.

**Description**

No permission to access the data specified by the URI.

**Possible Causes**

The permission required to access the specified data has not been requested.

**Solution**

Consult the data provider about the permission required to access the specified data.