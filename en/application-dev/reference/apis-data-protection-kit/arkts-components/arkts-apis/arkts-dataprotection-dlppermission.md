# @ohos.dlpPermission(DLP)

Data loss prevention (DLP) is a system solution provided to prevent data disclosure. This module provides APIs for cross-device file access management, encrypted storage, and access authorization. DLP protects sensitive files through encryption and generates encrypted files in .dlp format (DLP files). When opening a DLP file, the system automatically creates an isolated DLP sandbox environment to ensure that the file content is not leaked to unauthorized environments.

> **NOTE:** 
> 
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> - The kit to which **@ohos.dlpPermission** belongs has been changed from `DataLossPreventionKit` to `DataProtectionKit`. You are advised to use the new module name `@kit.DataProtectionKit` to import the module. If `@kit.DataLossPreventionKit` is imported, only the APIs before the change can be called and the APIs after the change cannot be used.

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [cancelRetentionState](arkts-dataprotection-dlppermission-cancelretentionstate-f.md) | Cancels the sandbox retention state, that is, allows the sandbox application to be automatically uninstalled when the DLP file is closed. This API uses a promise to return the result. |
| [cancelRetentionState](arkts-dataprotection-dlppermission-cancelretentionstate-f.md) | Cancels the sandbox retention state, that is, allows the sandbox application to be automatically uninstalled when the DLP file is closed. This API uses an asynchronous callback to return the result. |
| [cleanSandboxAppConfig](arkts-dataprotection-dlppermission-cleansandboxappconfig-f.md) | Clears the sandbox application configuration. After the API is successfully called, the sandbox application configuration is cleared and the default state is restored. This API uses a promise to return the result. |
| [closeOpenedEnterpriseDlpFiles](arkts-dataprotection-dlppermission-closeopenedenterprisedlpfiles-f.md) | Closes all opened enterprise DLP files that meet the specified options. This API uses a promise to return the result. |
| [decryptDlpFile](arkts-dataprotection-dlppermission-decryptdlpfile-f.md) | Decrypts a DLP file to generate a plaintext file. This API can be called only by enterprise accounts. This API uses a promise to return the result. |
| [generateDlpFileForEnterprise](arkts-dataprotection-dlppermission-generatedlpfileforenterprise-f.md) | Encrypts a plaintext file to generate a DLP file for an enterprise account. This API can be called only by enterprise accounts. This API uses a promise to return the result. |
| [getControlledAppLists](arkts-dataprotection-dlppermission-getcontrolledapplists-f.md) | Obtains the list of applications controlled by enterprise DLP for the current user. This API uses a promise to return the result. |
| [getDLPFileAccessRecords](arkts-dataprotection-dlppermission-getdlpfileaccessrecords-f.md) | Obtains the list of DLP files that are accessed recently. After the API is successfully called, the file access records are returned, which can be used to track and manage the usage of DLP files. This API can be called only in non-DLP sandbox applications. This API uses a promise to return the result. |
| [getDLPFileAccessRecords](arkts-dataprotection-dlppermission-getdlpfileaccessrecords-f.md) | Obtains the list of DLP files that are accessed recently. After the API is successfully called, the file access records are returned, which can be used to track and manage the usage of DLP files. This API can be called only in non-DLP sandbox applications. This API uses an asynchronous callback to return the result. |
| [getDLPPermissionInfo](arkts-dataprotection-dlppermission-getdlppermissioninfo-f.md) | Queries the permission information of the current DLP sandbox, including permissions on the file and operations that can be performed (such as viewing, editing, and copying). This API can be called only in DLP sandbox applications. This API uses a promise to return the result. |
| [getDLPPermissionInfo](arkts-dataprotection-dlppermission-getdlppermissioninfo-f.md) | Obtains the permission information of this DLP file. The returned permission information includes permissions on the file and operations that can be performed (such as viewing, editing, and copying). This API uses an asynchronous callback to return the result. |
| [getDLPSuffix](arkts-dataprotection-dlppermission-getdlpsuffix-f.md) | Obtains the DLP file name extension. After the API is called successfully, the DLP file name extension (for example,dlp) is returned. This API returns the result synchronously. |
| [getDLPSupportedFileTypes](arkts-dataprotection-dlppermission-getdlpsupportedfiletypes-f.md) | Obtains the file name extension types that support DLP. After the API is successfully called, the list of supported file types is returned, indicating the types of files that can be used to generate DLP files. This API uses a promise to return the result. |
| [getDLPSupportedFileTypes](arkts-dataprotection-dlppermission-getdlpsupportedfiletypes-f.md) | Obtains the file name extension types that support DLP. After the API is successfully called, the list of supported file types is returned, indicating the types of files that can be used to generate DLP files. This API uses an asynchronous callback to return the result. |
| [getOriginalFileName](arkts-dataprotection-dlppermission-getoriginalfilename-f.md) | Obtains the original name of a DLP file. This API returns the result synchronously. |
| [getRetentionSandboxList](arkts-dataprotection-dlppermission-getretentionsandboxlist-f.md) | Obtains the sandbox applications in the retention state of an application. This API can be called only in non-DLP sandbox applications. This API uses a promise to return the result. |
| [getRetentionSandboxList](arkts-dataprotection-dlppermission-getretentionsandboxlist-f.md) | Obtains the sandbox applications in the retention state of an application. This API uses an asynchronous callback to return the result. |
| [getRetentionSandboxList](arkts-dataprotection-dlppermission-getretentionsandboxlist-f.md) | Obtains the sandbox applications in the retention state of an application. This API uses an asynchronous callback to return the result. |
| [getSandboxAppConfig](arkts-dataprotection-dlppermission-getsandboxappconfig-f.md) | Obtains sandbox application configuration. This API uses a promise to return the result. |
| [isDLPFeatureProvided](arkts-dataprotection-dlppermission-isdlpfeatureprovided-f.md) | Checks whether the current system provides the encryption protection feature. This API is available only for enterprise devices and must be enabled by the [MDM](../../../mdm/mdm-kit-intro.md) kit. After the API is successfully called, the query result is returned, indicating whether the system supports DLP encryption. This API uses a promise to return the result. |
| [isDLPFile](arkts-dataprotection-dlppermission-isdlpfile-f.md) | Checks whether a file is a DLP file based on the FD. This API uses a promise to return the result. |
| [isDLPFile](arkts-dataprotection-dlppermission-isdlpfile-f.md) | Checks whether a file is a DLP file based on the FD. After the API is successfully called, a result is returned. The value **true** means the file is a DLP file; the value **false** means the opposite. This API uses an asynchronous callback to return the result. |
| [isInSandbox](arkts-dataprotection-dlppermission-isinsandbox-f.md) | Checks whether this application is running in a DLP sandbox environment. This API uses a promise to return the result. |
| [isInSandbox](arkts-dataprotection-dlppermission-isinsandbox-f.md) | Checks whether this application is running in a DLP sandbox environment. This API uses an asynchronous callback to return the result. |
| [off](arkts-dataprotection-dlppermission-off-f.md#offopendlpfile) | Unsubscribes from the DLP file open event. This API can be called only in non-DLP sandbox applications. After the API is successfully called, the application will no longer receive notifications for the DLP file open event. |
| [on](arkts-dataprotection-dlppermission-on-f.md#onopendlpfile) | Subscribes to a DLP file open event. After this API is successfully called, a callback notification is sent to the current application when the DLP file is opened. This API can be called only in non-DLP sandbox applications. |
| [processPluginCommand](arkts-dataprotection-dlppermission-processplugincommand-f.md) | Process the plugin-related commands in the transparent encryption and decryption scenario. |
| [queryDlpPolicy](arkts-dataprotection-dlppermission-querydlppolicy-f.md) | Parses the file header in a DLP file to obtain the DLP plaintext policy. The returned JSON string of the DLP policy contains the [DLPProperty](arkts-dataprotection-dlppermission-dlpproperty-i.md) and [CustomProperty](arkts-dataprotection-dlppermission-customproperty-i.md) information. This API uses a promise to return the result. |
| [queryOpenedEnterpriseDlpFiles](arkts-dataprotection-dlppermission-queryopenedenterprisedlpfiles-f.md) | Queries the URIs of enterprise DLP files that have been opened and meet the specified options. This API uses a promise to return the result. |
| [setControlledAppLists](arkts-dataprotection-dlppermission-setcontrolledapplists-f.md) | Sets the list of applications controlled by enterprise DLP. This API uses a promise to return the result. |
| [setEnterprisePolicy](arkts-dataprotection-dlppermission-setenterprisepolicy-f.md) | Sets the protection policy for enterprise applications. After the API is successfully called, the DLP protection for enterprise applications is implemented based on the configured policy. |
| [setRetentionState](arkts-dataprotection-dlppermission-setretentionstate-f.md) | Sets the retention state for sandbox applications. By default, when a DLP file is opened, the system automatically creates a sandbox environment. After the file is closed, the sandbox is automatically destroyed. After the retention state is set, the sandbox environment is retained even if the DLP file is closed, allowing the system to quickly reopen the same DLP file. This is applicable to scenarios where the same DLP file needs to be frequently operated, improving the file opening efficiency. This API uses a promise to return the result. |
| [setRetentionState](arkts-dataprotection-dlppermission-setretentionstate-f.md) | Sets the retention state for sandbox applications. By default, when a DLP file is opened, the system automatically creates a sandbox environment. After the file is closed, the sandbox is automatically destroyed. After the retention state is set, the sandbox environment is retained even if the DLP file is closed, allowing the system to quickly reopen the same DLP file. This is applicable to scenarios where the same DLP file needs to be frequently operated, improving the file opening efficiency. |
| [setSandboxAppConfig](arkts-dataprotection-dlppermission-setsandboxappconfig-f.md) | Sets the configuration information of the sandbox application. The configuration information is in JSON string format and can be set by the application. After the API is successfully called, the sandbox application runs based on the configuration information. This API uses a promise to return the result. This API can be called only in non-DLP sandbox applications. |
| [startDLPManagerForResult](arkts-dataprotection-dlppermission-startdlpmanagerforresult-f.md) | Starts the DLP manager application on the current [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md) page in borderless mode. This API uses a promise to return the result. |
| [startDLPManagerForResult](arkts-dataprotection-dlppermission-startdlpmanagerforresult-f.md) | Starts the DLP manager application in a specified window in borderless mode. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [generateDLPFile](arkts-dataprotection-dlppermission-generatedlpfile-f-sys.md) | Generates a **DLPFile** object, which is an encrypted file that can be accessed only by authorized users. The users can have the full control permission or read-only permission on the DLP file. This API uses a promise to return the result. |
| [generateDLPFile](arkts-dataprotection-dlppermission-generatedlpfile-f-sys.md) | Generates a DLP file, which is an encrypted file that can be accessed only by authorized users. The users can have the full control permission or read-only permission on the DLP file. Obtains a **DLPFile** object. This API uses an asynchronous callback to return the result. After using the **DLPFile** object, call [closeDLPFile](arkts-dataprotection-dlppermission-dlpfile-i-sys.md#closedlpfile) to close the object to prevent resource leakage. |
| [getDLPGatheringPolicy](arkts-dataprotection-dlppermission-getdlpgatheringpolicy-f-sys.md) | Obtains the DLP sandbox gathering policy. This API uses a promise to return the result. |
| [getDLPGatheringPolicy](arkts-dataprotection-dlppermission-getdlpgatheringpolicy-f-sys.md) | Obtains the DLP sandbox gathering policy. This API uses an asynchronous callback to return the result. |
| [installDLPSandbox](arkts-dataprotection-dlppermission-installdlpsandbox-f-sys.md) | Installs a DLP sandbox application for an application. The DLP sandbox creates an independent running environment for protected DLP files, which is isolated from the original application process. This ensures that data is securely transferred within the authorized scope. The sandbox application inherits the functions of the original application but can access only authorized DLP files. This API uses a promise to return the result. |
| [installDLPSandbox](arkts-dataprotection-dlppermission-installdlpsandbox-f-sys.md) | Installs a DLP sandbox application for an application. This API uses an asynchronous callback to return the result. After the API is called, the system creates a DLP sandbox for the application and returns the sandbox information. |
| [off](arkts-dataprotection-dlppermission-off-f-sys.md#offuninstalldlpsandbox) | Unsubscribes from the DLP sandbox uninstall event. After the API is successfully called, the application will no longer receive callback notifications for the DLP sandbox uninstall event. |
| [on](arkts-dataprotection-dlppermission-on-f-sys.md#onuninstalldlpsandbox) | Registers a listener for the DLP sandbox uninstall event, which is used to detect changes in the sandbox environment. After the registration, the system notifies the application using a callback when the DLP sandbox is uninstalled. |
| [openDLPFile](arkts-dataprotection-dlppermission-opendlpfile-f-sys.md) | Opens a DLP file. After the API is successfully called, the **DLPFile** object is returned, which can be used to manage the permissions on the DLP file and perform related operations. This API uses a promise to return the result. |
| [openDLPFile](arkts-dataprotection-dlppermission-opendlpfile-f-sys.md) | Opens a DLP file. This API uses an asynchronous callback to return the result. After the API is successfully called, the **DLPFile** object is returned, which can be used to manage the permissions on the DLP file and perform related operations. After using the **DLPFile** object, call **closeDLPFile** to close the object to prevent resource leakage. |
| [uninstallDLPSandbox](arkts-dataprotection-dlppermission-uninstalldlpsandbox-f-sys.md) | Uninstalls a DLP sandbox application for an application. This API uses a promise to return the result. After this API is called, the system destroys the specified DLP sandbox environment and releases related resources. |
| [uninstallDLPSandbox](arkts-dataprotection-dlppermission-uninstalldlpsandbox-f-sys.md) | Uninstalls a DLP sandbox application for an application. This API uses an asynchronous callback to return the result. After this API is called, the system destroys the specified DLP sandbox environment and releases related resources. |
<!--DelEnd-->

### Classes

| Name | Description |
| --- | --- |
| [DlpConnManager](arkts-dataprotection-dlppermission-dlpconnmanager-c.md) | Calls **registerPlugin** and **unregisterPlugin** to register or unregister callback capabilities in the SA. |

### Interfaces

| Name | Description |
| --- | --- |
| [AccessedDLPFileInfo](arkts-dataprotection-dlppermission-accesseddlpfileinfo-i.md) | Represents the information about a DLP file opened. |
| [AuthUser](arkts-dataprotection-dlppermission-authuser-i.md) | Represents the user authorization information. |
| [CustomProperty](arkts-dataprotection-dlppermission-customproperty-i.md) | Represents a custom policy. |
| [DlpConnPlugin](arkts-dataprotection-dlppermission-dlpconnplugin-i.md) | Registers the callback capability with the system ability (SA). This API is used in the **registerPlugin** API. |
| [DlpFileQueryOptions](arkts-dataprotection-dlppermission-dlpfilequeryoptions-i.md) | Represents the query options about an enterprise DLP file. |
| [DLPManagerResult](arkts-dataprotection-dlppermission-dlpmanagerresult-i.md) | Represents information about the trigger of the DLP manager application. |
| [DLPPermissionInfo](arkts-dataprotection-dlppermission-dlppermissioninfo-i.md) | Represents the permission information about a DLP file. |
| [DLPProperty](arkts-dataprotection-dlppermission-dlpproperty-i.md) | Represents the authorization information. |
| [EnterprisePolicy](arkts-dataprotection-dlppermission-enterprisepolicy-i.md) | Represents an enterprise custom policy. |
| [RetentionSandboxInfo](arkts-dataprotection-dlppermission-retentionsandboxinfo-i.md) | Represents the sandbox retention information. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DLPFile](arkts-dataprotection-dlppermission-dlpfile-i-sys.md) | Provides APIs for managing DLP files. A **DLPFile** instance indicates a DLP file object. You can use [generateDLPFile](arkts-dataprotection-dlppermission-generatedlpfile-f-sys.md) or [openDLPFile](arkts-dataprotection-dlppermission-opendlpfile-f-sys.md) to obtain a **DLPFile** instance. The **DLPFile** object represents an opened DLP file handle, which encapsulates all operation APIs for DLP files. After using the object, the system must call the [closeDLPFile](arkts-dataprotection-dlppermission-dlpfile-i-sys.md#closedlpfile) API to release resources to prevent file handle leaks. Authorization is required when the **DLPFile** object is transferred across processes. |
| [DLPSandboxInfo](arkts-dataprotection-dlppermission-dlpsandboxinfo-i-sys.md) | Represents the DLP sandbox information. |
| [DLPSandboxState](arkts-dataprotection-dlppermission-dlpsandboxstate-i-sys.md) | Represents the DLP sandbox state information. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [AccountType](arkts-dataprotection-dlppermission-accounttype-e.md) | Enumerates the types of authorized accounts. |
| [ActionFlagType](arkts-dataprotection-dlppermission-actionflagtype-e.md) | Enumerates the operations that can be performed on a DLP file. For example, the DLP sandbox application can dim its button based on this parameter. |
| [ActionType](arkts-dataprotection-dlppermission-actiontype-e.md) | Enumerates the actions to be performed when the file's permission expiration time is reached. The default value is **NOT_OPEN**. |
| [DLPFileAccess](arkts-dataprotection-dlppermission-dlpfileaccess-e.md) | Enumerates the permissions on a DLP file. |
| [PluginCmd](arkts-dataprotection-dlppermission-plugincmd-e.md) | Enumerates command codes for the plugin of an enterprise security application. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [GatheringPolicyType](arkts-dataprotection-dlppermission-gatheringpolicytype-e-sys.md) | Enumerates the DLP sandbox gathering policy types. **GATHERING** allows the DLP files of the same permission type to be opened in a sandbox. For example, open different tab pages in a sandbox. **NON_GATHERING** allows different DLP files to be opened in different sandboxes. |
<!--DelEnd-->
