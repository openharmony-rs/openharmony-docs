# Compilation Toolchain Error Codes
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @luchenxu; @calyx1111-->
<!--Designer: @luchenxu; @calyx1111-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=25644a1e2449a1798b2b4e0c64932a5d012faf9d translatedAt=2026-11-04T10:38:24.230Z pushedAt=2026-11-04T10:44:46.332Z nl=1 -->

> **NOTE**
>
> Compiler toolchain error codes are used to identify various errors during the ArkTS compilation process, covering scenarios such as file import restrictions, module resolution, Kit configuration and import, compilation execution, and lazy import, helping developers quickly locate and resolve compilation-related issues.<br>
> The following describes only the error codes specific to this module. For general error codes, see [General Error Code Description](../errorcode-universal.md).

## 10311001 Failed to Import ArkTS Files

**Error Message**

Importing ArkTS files in JS and TS files is forbidden.

**Description**

It is forbidden to import ArkTS files to JS or TS files.

**Possible Causes**

In mixed-language project development, a JS or TS file references a module or interface in an ArkTS file through an import statement.

**Solution**

Remove the import statements for ArkTS files from JS and TS files.

## 10311002 Failed to Parse OhmUrl

**Error Message**

Failed to resolve OhmUrl. Failed to get a resolved OhmUrl for `${filePath}` imported by `${importerFile}`.

**Description**

Failed to resolve OhmUrl. Failed to obtain the parsed OhmUrl for ${filePath} imported by ${importerFile}.

**Possible Causes**

The ${pkgName} module to which ${filePath} belongs is configured incorrectly.

**Solution**

1. Make sure the ${pkgName} module is correctly configured in the ${filePath} file.
2. Make sure the file name is correct, including its case sensitivity.

## 10311003 Failed to Obtain the Kit Configuration File

**Error Message**

Kit `${moduleRequest}` has no corresponding config file in ArkTS SDK.

**Description**

The ${moduleRequest} kit does not have the corresponding configuration file in the ArkTS SDK.

**Possible Causes**

1. The API version of the kit does not match the SDK version, or the interfaces provided by the kit do not exist in the SDK.
2. The APIs of the kit are modified locally.

**Solution**

1. Make sure the kit API you are importing is consistent with the SDK version you are using, and the kit APIs are not modified locally.
2. For details about the kit APIs, see <!--RP1-->[API Reference Document Description](../development-intro-api.md).<!--RP1End-->

## 10311005 Incorrect Kit Identifier

**Error Message**

Identifier `${importName}` comes from `${source}` which can not be imported in .ts file.

**Description**

The identifier `${importName}` comes from `${source}`, and this identifier cannot be imported in a .ts file.

**Possible Causes**

An ArkTS file of the kit is imported to the TS file.

**Solution**

Remove the import statement, or change the file extension to .ets. For example, rename the file `example.ts` to `example.ets`.

## 10311006 Failed to Export Imported Names from the Kit

**Error Message**

`${importName}` is not exported from Kit `${KitName}`.

**Description**

`${importName}` is not exported from Kit `${KitName}`.

**Possible Causes**

1. The APIs of the kit are inconsistent with those in the SDK.
2. The APIs of the kit are modified locally.

**Solution**

1. Make sure the kit APIs are consistent with the SDK.
2. Make sure the kit APIs are not modified locally.
3. For more details about the kit APIs, see <!--RP1-->[Development Guide](../development-intro-api.md).<!--RP1End-->

## 10311007 Failed to Import or Export Kit Namespaces

**Error Message**

Namespace import or export of Kit is not supported currently.

**Description**

Currently, the namespace of a kit cannot be imported or exported.

**Possible Causes**

The file uses the namespace of the kit for import or export.

**Solution**

Replace the namespace import or export of the kit with a named import or export. Example: import * as ArkTS from "@kit.ArkUI"; -> import { AlertDialog } from "@kit.ArkUI";

## 10311008 Kit Empty Import Error

**Error Message**

Can not use empty import(side-effect import) statement with Kit `${KitName}`.

**Description**

The empty import (side-effect import) statement cannot be used in the Kit `${KitName}`.

**Possible Causes**

The empty import (side-effect import) statement of the kit is used in the file.

**Solution**

Specify the symbol to be imported. Example: import "@kit.ArkUI"; -> import { lang } from "@kit.ArkUI";

## 10311009 es2abc Execution Error

**Error Message**

Failed to execute es2abc.

**Description**

es2abc fails to be executed.

**Possible Causes**

An error occurred during the execution of es2abc.

**Solution**

Refer to [es2abc Compiler Error Codes](errorcode-es2abc.md) for handling.

## 10311010 Lazy Import Re-export Error

**Error Message**

`${elementText}` of lazy-import is re-export.

**Description**

The lazy import of ${elementText} is re-exported.

**Possible Causes**

1. The lazily imported `${elementText}` is re-exported.
2. The autoLazyImport switch is enabled, and the re-exported static import may be automatically converted to a lazy import.

**Solution**

1. Make sure lazily loaded named bindings are not re-exported.
2. Check whether the autoLazyImport switch is enabled. After the autoLazyImport switch is enabled, some static imports may be automatically converted to lazy imports. If the named bindings of such an import are re-exported, this error is triggered. To disable this switch, set autoLazyImport to false in the project configuration file.
