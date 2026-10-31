# Error Codes of Bundle Management Quick Fix Commands
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=5f0e51d369517715ece8ed7b2a692095630aae0c translatedAt=2026-09-03T08:29:30.809Z pushedAt=2026-09-05T10:47:30.097Z -->

Describes the error codes of the quick fix commands, as well as the causes of failures and the solutions.

> **NOTE**
>
> The following describes only the error codes of the quick fix commands. The command returns only the error code, without any description.

## 6 System Exception

**Description**

System exception.

**Possible Causes**

An unknown issue occurs in the system, causing the service to become abnormal.

**Procedure**

Please restart the device and retry. If the problem persists, it indicates that an unknown issue has occurred in the system and the developer cannot handle it by themselves. <!--RP1-->Please [submit an issue](https://atomgit.com/openharmony/docs/issues) to get help. <!--RP1End-->

## 7 Permission Verification Exception

**Description**

A permission verification exception occurs during command execution.

**Possible Causes**

When the bm quickfix command is executed, an exception occurs in the permissions of the bm process, causing the command execution to fail.

**Procedure**

Please restart the device and retry. If the problem persists, an unknown issue has occurred in the permissions of the bm process or in the permission verification logic, which the developer cannot handle by themselves. <!--RP1-->Please [submit an issue](https://atomgit.com/openharmony/docs/issues) to get help.<!--RP1End-->

## 8 bundleName Error

**Description**

The bundleName is incorrect.

**Possible Causes**

During a quick fix query, the bundleName passed in is not installed, or the application corresponding to the bundleName has no patch package.

**Procedure**

Check the correctness of the bundleName entered in the command, and ensure that the application bundle name entered has a corresponding patch package.<!--Del-->

## 20 System Application Permission Verification Failed

**Description**

The caller is not a system application and has no permission to perform this operation.

**Possible Causes**

1. The application that executes the command has not obtained the system signature.

2. An attempt was made to call a protected permission that is available only to system applications.

**Procedure**

1. Confirm whether the caller is a system application. To call this API, apply for the system application permission or use the corresponding public API.

2. The command operation failed. Restart the device and retry. If the problem persists, an unknown issue has occurred in the system permission verification logic and cannot be handled by the developer. <!--RP1-->Submit an [issue](https://atomgit.com/openharmony/docs/issues) to get help. <!--RP1End--><!--DelEnd-->

## 8388613 IPC Communication Exception

**Description**

An exception occurs during IPC communication.

**Possible Causes**

Data serialization or deserialization fails during IPC communication.

**Procedure**

Restart the device and try again. If the problem persists, an unknown issue occurs in IPC communication, which the developer cannot handle by themselves. <!--RP1-->Submit an [Issue](https://atomgit.com/openharmony/docs/issues) for help. <!--RP1End-->

## 8520705 Internal Error

**Description**

An unknown exception occurs in the system, causing the service to be unavailable.

**Possible Causes**

Internal error. An internal component of the service is abnormal.

**Procedure**

Please restart the device and retry. If the problem persists, an unknown issue appears in the system, which the developer cannot handle by themselves. <!--RP1-->Please [submit an Issue](https://atomgit.com/openharmony/docs/issues) to get help.<!--RP1End-->

## 8520706 Parameter Error

**Description**

The input parameters are incorrect.

**Possible Causes**

The parameters passed during the call do not meet the requirements.

**DeployQuickFix scenario:**
1. The patch file path list is an empty array.
2. The targetPath parameter is invalid (contains ".", "..", or "/" characters).
3. When creating a directory, the file name is empty or is not of the .hqf file type.
4. When copying a file, the source file information is empty or the file path verification fails.
5. The path is invalid (contains a relative path or is not in a secure directory).

**DeleteQuickFix scenario:**
1. bundleName is an empty string.

**Procedure**

Check the parameters of the command or API call:
- Ensure that bundleFilePaths is not empty and the paths are valid.
- Ensure that bundleName is not empty and the corresponding application exists.
- Ensure that targetPath does not contain path traversal characters.

## 8520707 Failed to Parse File

**Description**

An error occurred while parsing the patch file.

**Possible Causes**

Failed to parse the patch configuration file.

1. The patch file format is incorrect and cannot be parsed.
2. The configuration information in the patch file is missing or invalid.
3. hqfInfos is empty, and module information is missing.
4. The patch type is unknown (QuickFixType::UNKNOWN).

**Procedure**

Check the patch file:
- Confirm that the patch file format is correct.
- Confirm that the patch file contains complete configuration information (bundleName, versionCode, etc.).
- Confirm that the patch file contains valid module information.

## 8520708 Inconsistent bundleName

**Description**

When deploying multiple patch files, the bundleName in the files is inconsistent.

**Possible Causes**

The bundleName in multiple patch files is inconsistent.

When deploying multiple patch files, all patch files must belong to the same application package.

**Procedure**

Ensure all patch files have the same bundleName and point to the same application.

## 8520709 versionCode Mismatch

**Description**

The application version fixed by the patch file is inconsistent with the version of the installed application.

**Possible Causes**

The versionCode of the application fixed by the patch file is inconsistent with the versionCode of the installed application.

**Procedure**

Ensure that the versionCode of the application fixed by the patch file matches the versionCode of the installed application.

## 8520711 Patch File Version Mismatch

**Description**

Multiple patch files have inconsistent versions.

**Possible Causes**

When deploying multiple patch files, the versionCode of the patch files is inconsistent.

**Procedure**

Ensure that the versionCode of all patch files is consistent.

## 8520713 Inconsistent Patch File Types

**Description**

Multiple patch files have inconsistent types.

**Possible Causes**

The patch types of multiple patch files are inconsistent.

The patch type can be PATCH or HOT_RELOAD, and the types of multiple patch files must be consistent.

**Procedure**

Ensure that the patch types of all patch files are consistent.

## 8520714 Duplicate Module Name

**Description**

When deploying multiple patch files, patch packages with the same module name exist.

**Possible Causes**

Multiple patch files contain the same module name.

**Procedure**

Check the patch files and ensure that each patch corresponds to a different module name.

## 8520715 Invalid Patch Type

**Description**

The patch type obtained during patch deployment is invalid.

**Possible Causes**

The patch type is unknown or invalid.

The patch type must be PATCH or HOT_RELOAD, and cannot be any other type.

**Procedure**

Check the configuration of the patch file and ensure that the patch type is PATCH or HOT_RELOAD.

## 8520716 so incompatibility

**Description**

The Native So library of the patch is incompatible.

**Possible Causes**

The Native So library of the patch is incompatible with the installed application.

1. The cpuAbi of the patch is inconsistent with that of the installed application.
2. The nativeLibraryPath of the patch is inconsistent with that of the installed application.
3. The Native So configurations of multiple patch files are inconsistent.

**Procedure**

Ensure that the Native So configuration of the patch is compatible with the installed application:
- The cpuAbi must be consistent.
- The nativeLibraryPath must match.

## 8520717 bundleName Does Not Exist

**Description**

The bundleName in the patch file does not exist.

**Possible Causes**

The application bundle name does not exist.

1. The bundleName of the patch does not match the bundleName of the installed application.
2. The target application is not installed.

**Procedure**

Confirm that the target application is installed and that the bundleName of the patch is consistent with the target application.

## 8520718 Module Name Does Not Exist

**Description**

The module name of the patch application does not exist.

**Possible Causes**

The module name of the patch does not exist in the installed application.

A patch can only be applied to existing modules of the installed application.

**Procedure**

Confirm that the module name of the patch has a corresponding module in the target application.

## 8520719 Inconsistent Signature Information

**Description**

The signature information of the patch is inconsistent with that of the installed application.

**Possible Causes**

The signature information of the patch is inconsistent with that of the installed application.

1. The application privilege level (apl) is inconsistent.
2. The appIdentifier is inconsistent.
3. The appId is inconsistent.
4. The bundleName in the provision is inconsistent with the bundleName of the application.

**Procedure**

Ensure that the signature information of the patch is consistent with that of the installed application:
- Use the same signing certificate.
- Ensure that the apl level is consistent.
- Ensure the appIdentifier is consistent.

## 8520720 Failed to Convert Patch Information

**Description**

Failed to convert the patch information into the internal object InnerAppQuickFix.

**Possible Causes**

Failed to add the patch information.

Failed to add the patch information to InnerAppQuickFix, possibly due to an abnormal data structure.

**Procedure**

Check the completeness of the configuration information in the patch file. If the problem persists, the system appears to have an unknown issue that the developer cannot handle by themselves. <!--RP1-->Please [submit an issue](https://atomgit.com/openharmony/docs/issues) to get help.<!--RP1End-->

## 8520721 Failed to Store Patch Information in Database

**Description**

Failed to store the patch information in the database.

**Possible Causes**

Failed to save the patch information to the database.

The database write operation failed, possibly due to a database exception or a permission issue.

**Procedure**

A database exception is an internal system error. Restart the device and try again. If the problem persists, <!--RP1-->submit an [Issue](https://atomgit.com/openharmony/docs/issues) for help.<!--RP1End-->

## 8520722 Patch Version Error

**Description**

The patch versionCode of the patch is less than or equal to the versionCode of the deployed or being-deployed patch.

**Possible Causes**

The patch version code is incorrect.

1. The patch versionCode of the patch is not greater than the versionCode of the deployed patch.
2. The patch versionCode of the patch is not greater than the versionCode of the patch being deployed.

The patch version code must be greater than the existing patch version code to ensure version increment.

**Procedure**

Ensure that the patch versionCode of the patch is greater than the versionCode of the deployed patch.

## 8520723 Failed to Extract the Diff File

**Description**

During patch deployment, failed to read the diff file from the patch file.

**Possible Causes**

Failed to extract the diff file.

When applying a diff patch of the Patch type, failed to extract the diff so file from the hqf file.

**Procedure**

Check the integrity of the patch file and ensure that the diff file is valid. If the problem persists, an unknown issue has occurred in the system and the developer cannot handle it by themselves. <!--RP1-->Please [submit an issue](https://atomgit.com/openharmony/docs/issues) to get help.<!--RP1End-->

## 8520724 Failure to Apply the SO File of a Patch File

**Description**

Failed to apply the SO file of the patch file.

**Possible Causes**

Failed to apply the differential patch.

The patch type patch failed when applying the differential patch to the target SO file.

**Procedure**

Check the patch file and the original SO file to ensure that they are compatible. If the problem persists, the system appears to have an unknown issue that the developer cannot handle by themselves. <!--RP1-->Please [submit an issue](https://atomgit.com/openharmony/docs/issues) to get help.<!--RP1End-->

## 8520726 Patch File Status Error

**Description**

Failed to obtain the patch status or update the patch status.

**Possible Causes**

The patch status is invalid.

1. When deploying a patch, the current patch status is neither DEPLOY_START nor DEPLOY_END.
2. When deleting a patch, updating the status to DELETE_START fails.

The patch must be in a valid status before the corresponding operation can be performed.

**Procedure**

Check the current patch status and ensure that it is valid before performing the operation. If the status is abnormal, wait for the previous operation to complete or restart the device and retry.

## 8520727 Data Information Query Failure

**Description**

Failed to obtain the patch application information.

**Possible Causes**

The BundleInfo of the application does not exist.

Data is abnormal, causing the application information to be unavailable.

**Procedure**

Confirm that the target application is correctly installed. If the application exists but the query fails, check the data manager status.

## 8520728 Failed to Delete Directory

**Description**

Failed to delete the patch directory during patch deployment.

**Possible Causes**

1. Failed to delete the directory of the deployed patch.
2. Failed to delete the directory of the patch being deployed.
3. Failed to delete the directory.

**Procedure**

Check the file system permissions and ensure sufficient permissions to delete the patch directory. If the problem persists, restart the device and retry.

## 8520729 Failed to Create Directory

**Description**

Failed to create the patch directory during patch deployment.

**Possible Causes**

Failed to create the patch directory.

1. Insufficient file system permissions.
2. Insufficient disk space.
3. Failed to create the directory.

**Procedure**

Check the file system permissions and disk space, and ensure sufficient permissions to create the patch directory.

## 8520730 File Move Failure

**Description**

The patch file fails to be moved during patch deployment.

**Possible Causes**

Failed to move the patch file.

1. Failed to copy the file.
2. Failed to copy the patch file to the target path.
3. The file copy operation failed.

**Procedure**

Check the file system permissions and the target path to ensure that the file copy operation works properly.

## 8520731 Patch Type Application Error

**Description**

Failed to apply a Hot Reload type patch.

**Possible Causes**

Hot Reload type patches do not support Release version applications.

Hot Reload is only applicable to Debug version applications. Release version applications can only use PATCH type patches.

**Procedure**

To patch a Release version application, use a PATCH type patch. Hot Reload is only applicable to Debug version applications.

## 8520736 IPC Process Failure

**Description**

A failure is returned during IPC communication.

**Possible Causes**

The SendRequest call fails during IPC communication.

1. The Remote object is a null pointer.
2. IPC SendRequest returns an error code.
3. The server process is abnormal or not started.

**Procedure**

Restart the device and try again. If the problem persists, check the Bundle Manager service status or <!--RP1-->[submit an issue](https://atomgit.com/openharmony/docs/issues) for help.<!--RP1End-->

## 8520738 Invalid Path

**Description**

The patch file path verification is invalid.

**Possible Causes**

The patch file path is invalid.

1. The file path contains a relative path identifier (such as "../").
2. The file path is not under the specified secure directory prefix.
3. When CopyHqfToSecurityDir is called, the path does not meet the security requirements.

**Procedure**

Ensure that the patch file path is valid:
- Use an absolute path instead of a relative path.
- Ensure that the path starts with the secure directory prefix.
- Avoid path traversal characters.

## 8520739 File Read Failure

**Description**

Failed to read the file while parsing the patch file during patch deployment.

**Possible Causes**

Failed to open the patch source file.

1. The patch file does not exist.
2. Insufficient file permissions to read the file.
3. The file system is abnormal.

**Procedure**

Check the patch source file:
- Confirm that the file exists.
- Confirm that the file has read permission.
- Check the file system status.

## 8520740 Failed to Create File Descriptor

**Description**

Failed to create a file descriptor while parsing the patch file during deployment.

**Possible Causes**

Failed to create a file descriptor.

1. The target directory does not exist.
2. The file system has insufficient permissions.
3. Failed to create the file.

**Procedure**

Check the target directory permissions and file system status, and ensure sufficient permissions to create the file.

## 8520741 Invalid Target Directory Path

**Description**

Failed to verify the target directory when deploying the patch file and operating on files.

**Possible Causes**

The target directory path is invalid.

1. CreateFd succeeds but the returned path is empty.
2. Failed to create the target directory.

**Procedure**

Check the target path configuration and ensure the path is valid and accessible.

## 8520742 Temporary File Creation Failure

**Description**

Failed to create the temporary directory during patch file deployment.

**Possible Causes**

Failed to create the temporary directory.

1. Insufficient file system permissions.
2. Insufficient disk space.
3. Directory creation exception.

**Procedure**

Check the file system permissions and disk space, and ensure sufficient space to create the temporary directory.

## 8520743 Permission Verification Failure

**Description**

Permission verification failed.

**Possible Causes**

The caller lacks the required permission to install or uninstall patches.
<!--Del-->
1. DeployQuickFix requires the `ohos.permission.INSTALL_BUNDLE` or `ohos.permission.INSTALL_QUICK_FIX_BUNDLE` permission.
2. DeleteQuickFix requires the `ohos.permission.INSTALL_BUNDLE` or `ohos.permission.UNINSTALL_QUICK_FIX_BUNDLE` permission.
3. CreateFd requires the `ohos.permission.INSTALL_BUNDLE` or `ohos.permission.INSTALL_QUICK_FIX_BUNDLE` permission.<!--DelEnd-->

**Procedure**

<!--Del-->1. Check the caller's permission configuration to ensure that the corresponding install/uninstall patch permission has been applied for and granted.

2.<!--DelEnd-->If the command operation fails, restart the device and retry. If the problem persists, an unknown issue has occurred in the system and the developer cannot handle it by themselves.<!--RP1--> Please [submit an issue](https://atomgit.com/openharmony/docs/issues) to get help.<!--RP1End-->

## 8520744 Write File Failure

**Description**

Failed to write the file while deploying the patch file.

**Possible Causes**

Failed to write the file.

1. An I/O error occurred while writing the target file.
2. The target directory has insufficient permissions.
3. Insufficient disk space.

**Procedure**

Check the target directory permissions and disk space to ensure that the file write operation succeeds.

## 8520745 Code Encryption Not Supported

**Description**

Patch repair does not support code encryption.

**Possible Causes**

Patches for modules with code encryption are not supported.

Patches do not support quick repair of code-encrypted modules.

**Procedure**

Confirm whether the target module has code encryption enabled. If it is enabled, repackage the application or use another repair method.

## 8520746 Insufficient Disk Space

**Description**

During patch repair, insufficient disk space causes the patch to fail during file operations.

**Possible Causes**

Insufficient disk space.

When installing the patch, the disk space is insufficient to store the patch file.

**Procedure**

Free up disk space and retry.

## 8520747 Failed to Decrypt the So File

**Description**

Failed to extract the so file from the patch file.

**Possible Causes**

Failed to decrypt the So file.

Failed to decrypt the so file of the encrypted module.

**Procedure**

Check the encrypted module configuration. If the problem persists, the system appears an unknown issue that the developer cannot handle by themselves. <!--RP1-->Please [submit an Issue](https://atomgit.com/openharmony/docs/issues) to get help.<!--RP1End-->

## 8520748 Patch File Resources Exceeded

**Description**

The patch of a non-Debug version application contains resources files.

**Possible Causes**

The patch of a Release version application contains resources files.

The patch of a non-Debug version application should not contain resources files. Only the Debug version is allowed to contain resources.

**Procedure**

For a Release version application, ensure that the patch does not contain resources files.

## 8520749 Decompression Mode Not Satisfied

**Description**

The replacement mode patch cannot be enabled on an application that does not decompress .so files.

**Possible Causes**

The replacement mode patch is applied to a module with uncompressed native libraries.

When isReplace=true, compressNativeLibs of the target module must be true.

**Procedure**

Check the compressNativeLibs configuration of the target module and ensure that it is true, or do not use the replacement mode.<!--Del-->

## 8521238 System Application Permission Verification Failed

**Description**

The caller is not a system application and is not authorized to perform this operation.

**Possible Causes**

1. The application that executes the command is not signed with a system signature.

2. An attempt was made to call a protected permission that is available only to system applications.

**Procedure**

1. Confirm whether the caller is a system application. To call this API, apply for the system application permission or use the corresponding public API.

2. The command operation failed. Restart the device and retry. If the problem persists, an unknown issue has occurred in the system permission verification logic and cannot be handled by the developer. <!--RP1-->Submit an [issue](https://atomgit.com/openharmony/docs/issues) to get help. <!--RP1End--><!--DelEnd-->
