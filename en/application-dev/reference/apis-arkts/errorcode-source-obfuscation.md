# Source Code Obfuscation Error Codes
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @zju-wyx-->
<!--Designer: @xiao-peiyang; @dengxinyu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @foryourself-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 10804001 Missing Obfuscation Rule Configuration File

**Error Message**

Failed to open obfuscation config file from {path}.

**Description**

The obfuscation rule configuration file cannot be read from {path}.

**Possible Causes**

The obfuscation rule configuration file specified in the `arkOptions.obfuscation.ruleOptions` field of the module's `build-profile.json5` file does not exist or the file path is incorrect.

**Solution**

Check whether the {path} exists and whether the path is correct. For details, see the [example of the obfuscation configuration file](../../arkts-utils//source-obfuscation-guide.md#how-to-use).

## 10804002 Incorrect nameCache.json File Format

**Error Message**

Failed to open namecache file from {nameCachePath}, Error message: SyntaxError: Unexpected string in JSON at position 733 At {nameCachePath}.

**Description**

The **nameCache.json** file cannot be read from the specified name cache file path {nameCachePath}.

**Possible Causes**

The content of the JSON file at the given path is malformed and does not comply with the standard JSON syntax specifications.

**Solution**

Locate the file at {nameCachePath}, check the character position indicated in the error message, and fix the JSON format errors in accordance with the error details provided.

## 10804003 Failed to Generate the keptNames.json File

**Error Message**

Failed to open keptNames.json from {defaultUnobfuscationPath}.

**Description**

The **keptNames.json** file cannot be read from {defaultUnobfuscationPath}.

**Possible Causes**

The **keptNames.json** file was not generated in {defaultUnobfuscationPath}.

**Solution**

Check whether the **keptNames.json** file has been generated in {defaultUnobfuscationPath}. If not, clean the cache and recompile the project.

## 10804004 nameCache.json File Not Found

**Error Message**

The applied namecache file {nameCachePath} configured by {configPath} does not exist.

**Description**

The JSON file configured with the **-apply-namecache** rule cannot be read from {nameCachePath}.

**Possible Causes**

The JSON file configured with the **-apply-namecache** rule does not exist in the obfuscation rule configuration file **obfuscation-rules.txt**.

**Solution**

Verify the JSON file path configured with the **-apply-namecache** rule in the **obfuscation-rules.txt** file to ensure it is correct.

## 10810001 File Obfuscation Failure Due to ArkGuard Error

**Error Message**

ArkTS:INTERNAL ERROR: Failed to obfuscate file 'entry/src/main/ets/entryability/EntryAbility.ets' with arkguard. Error: Obfuscation failed At entry/src/main/ets/entryability/EntryAbility.ets.

**Description**

The obfuscation process fails, and file obfuscation cannot be completed.

**Possible Causes**

The internal source code of ArkGuard has been modified without authorization.

**Solution**

In DevEco Studio, navigate to the path `\DevEco-Studio\sdk\default\openharmony\ets\build-tools\ets-loader\node_modules\arkguard`. Compare the last modification date of the **arkguard** directory with that of its sibling files. If discrepancies exist, download and reinstall the DevEco Studio of this version.
