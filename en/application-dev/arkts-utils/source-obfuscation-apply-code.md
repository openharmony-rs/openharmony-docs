# ArkGuard Obfuscation Practice Guide

<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @doubleGuan-->
<!--Designer: @wangwenbo551-->
<!--Tester: @yan_panda-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=62613a5ceda2a4127227a789205c9c3cb4ba79a4 translatedAt=2026-08-31T12:40:26.350Z pushedAt=2026-08-31T15:01:50.898Z -->

## Overview

Source code obfuscation technology can increase the complexity and ambiguity of code, thereby raising the difficulty for attackers to analyze the code. Source code obfuscation serves the following purposes:

1.  Protect intellectual property: Source code obfuscation prevents others from easily copying and stealing software code, increasing the difficulty of reverse engineering.

2.  Prevent reverse engineering: Reverse engineering is the process of analyzing software to understand how it works and its implementation details. Source code obfuscation can increase the difficulty of reverse engineering and protect applications from malicious modification or damage.

3.  Improve security: Source code obfuscation reduces vulnerabilities and security risks, increasing the difficulty for attackers to exploit vulnerabilities.

4.  Reduce anti-piracy and fraud risks: Source code obfuscation can increase the difficulty for attackers to crack the software license verification system or modify code to bypass payment mechanisms, thereby reducing piracy and fraud.

Source code obfuscation obfuscates the project source code, increases the difficulty of cracking, shortens class and member names, and reduces the application size.

## Enabling Obfuscation

Starting from API version 10, source code obfuscation is supported. Enabling obfuscation requires the following conditions: the project uses the Stage model, is in Release build mode, and obfuscation configuration is enabled in the module's `build-profile.json5` file. For detailed enabling steps and configuration methods, refer to [ArkGuard Obfuscation Enabling Guide](source-obfuscation-guide.md).

> **Note:**  
> `enable` defaults to false, meaning source code obfuscation is disabled by default (before DevEco Studio 5.0.3.600, newly created projects had source code obfuscation enabled by default).

If the project or module is a Static Library, then the project or module is a HAR.

The obfuscation behavior when building a [bytecode HAR](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-har#section16598338112415) is as follows:

1.  When building a HAR in Debug mode, the source code is packaged directly without source code obfuscation.

2.  When building a HAR in Release mode, the code is compiled, obfuscated, and compressed.

3.  When building a HAR in bytecode format, if obfuscation is enabled, the compiler first obfuscates the intermediate source code files and then generates abc bytecode.

For obfuscation recommendations for different package types, refer to [Source Code Obfuscation Recommendations for Different Package Types](source-obfuscation-practice.md).

### Build Operation Steps

After the conditions for enabling obfuscation are met, select the target module and click Build -\> Make Module to start the build.

The steps to build a HAR in Release mode are as follows:  
**Figure 1**  Selecting the release build mode in DevEco Studio  


**Figure 2**  Building a specified module in DevEco Studio  


## Obfuscation Configuration Capabilities

### Build Options

If source code obfuscation is enabled by following the build process described above, versions before API 12 obfuscate only parameter names and local variable names by default. Starting from API 12, four recommended obfuscation options are enabled by default: `-enable-property-obfuscation`, `-enable-toplevel-obfuscation`, `-enable-filename-obfuscation`, and `-enable-export-obfuscation`. Developers can further modify the obfuscation configuration as needed.

If obfuscation is enabled in the pipeline and the release build mode is used, add `-p buildMode=release` and `-p debuggable=false` to the build parameters.

### Obfuscation Configuration

As shown in the following figure, you can configure whether to enable obfuscation and the corresponding obfuscation configuration file in the `build-profile.json5` file under each module.

**Figure 3** Build configuration file


When creating a project, each module has an `obfuscation-rules.txt` file for configuring obfuscation.

**Figure 4** Obfuscation configuration file


In the preceding figure, the `-enable-property-obfuscation` and `-enable-toplevel-obfuscation` switches are added to the `obfuscation-rules.txt` file, indicating that property obfuscation and top-level scope name obfuscation are enabled.

The DevEco Studio obfuscation options and their functions are described as follows:

**Table 1** Obfuscation options

| Option | Function |
| --- | --- |
| -disable-obfuscation | Disables obfuscation |
| -enable-property-obfuscation | Enables property name obfuscation |
| -enable-string-property-obfuscation | Enables string property name obfuscation |
| -enable-toplevel-obfuscation | Enables top-level scope name obfuscation |
| -enable-export-obfuscation | Enables import/export name obfuscation |
| -enable-filename-obfuscation | Enables file name obfuscation |
| -compact | Compresses code |
| -remove-comments | Removes comments from declaration files |
| -remove-log | Removes console.* statements |
| -print-namecache | Outputs the name cache |
| -apply-namecache | Reuses the name cache |
| -print-kept-names | Outputs the list of unobfuscated names |
| -extra-options strip-language-default | Reduces the language preset trustlist |
| -extra-options strip-system-api-args | Reduces the system preset trustlist |
| -extra-options strip-not-compiled-module-name | Does not keep names of modules not involved in compilation |
| -keep-parameter-names | Keeps declaration file parameters |
| -enable-lib-obfuscation-options | Merges dependency module options |
| -use-keep-in-source | Marks the trustlist in source code through comments |
| -keep-object-props | Keeps object literal property names |
| -remove-nosideeffects-calls | Deletes specified method call statements |

**Table 2** Keep options

| Option | Function |
| --- | --- |
| -keep-property-name | Specifies property names to keep |
| -keep-global-name | Specifies top-level scope or import/export element names to keep |
| -keep-file-name | Specifies file/folder names to keep |
| -keep-comments | Specifies comments to keep |
| -keep-dts | Specifies all names in declaration files to keep |
| -keep | Specifies all names in source code files to keep |
| -keep-uncompact | Excludes files at specified paths from code compression |

> **Note:**
> Name-type and path-type keep options support wildcards. For detailed usage, refer to Wildcards supported by keep options.

For detailed usage and code examples of obfuscation options, refer to Obfuscation configuration options and Obfuscation keep options.

**Obfuscation optimization suggestions**

When developers obfuscate a project, they may find a large number of unobfuscated source code names in cache files or files in the SDK. The reasons include the following two categories:

* Too few obfuscation options are enabled; enable the `-enable-property-obfuscation`, `-enable-toplevel-obfuscation`, `-enable-export-obfuscation`, and `-enable-filename-obfuscation` options.

* Source code names duplicate names in the system trustlist or language trustlist; add a suffix to avoid the trustlist.

### Obfuscation Rule Merge Strategy

When building a module, the effective obfuscation rules are the merged result of the current module's obfuscation rules and the dependency modules' obfuscation rules. For details, refer to [Obfuscation Rule Merge Strategy](source-obfuscation.md).

## Viewing Obfuscation Results

Developers can find the cache files, name mapping table, and system API trustlist file generated during compilation and obfuscation in the build directory of the compiled module.

* Source code compilation and obfuscation cache file directory: build/\[…\]/release/module name

* Obfuscation name mapping table and system API trustlist directory: build/\[…\]/release/obfuscation

  * Name mapping table file: `nameCache.json`, which records the source code name mapping.

  * System API trustlist file: `systemApiCache.json`, which records the SDK interface and property names.

    **Figure 5**  DevEco Studio build artifacts and cache files  

## Debugging

After the code is processed by the obfuscation tool, names are changed, which may make runtime crash stack logs difficult to understand because the stack does not fully match the source code. If debugging information is not retained, line number and name changes will make it impossible to accurately locate the problem. In addition, after enabling options such as `-enable-property-obfuscation` and `-enable-toplevel-obfuscation`, source code obfuscation may cause runtime crashes or functional errors. Developers need to restore the error stack, troubleshoot, and configure a trustlist to ensure normal functionality.

### Function Call Stack Restoration

In an obfuscated application, code names are changed, so the error stack is not fully consistent with the source code, and the error stack printed during a crash is difficult to understand. For how to handle this, refer to [Error Stack Restoration](source-obfuscation-guide.md).

### Deobfuscation Tool hstack

hstack requires Node.js to be configured in the environment variables. For detailed usage instructions, refer to [Stack Parsing Tool (hstack)](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-command-line-hstack).

### Common Error Cases

Refer to [ArkGuard Obfuscation FAQ](source-obfuscation-questions.md).

## Using Third-Party Hardening

In addition to the source code obfuscation capability provided by HarmonyOS, developers can also use advanced obfuscation and hardening capabilities provided by third-party security vendors. Multiple security hardening vendors have started HarmonyOS development, and developers can choose the services of these security vendors based on their needs. Developers need to communicate with third-party security vendors about the cooperation method and scope on their own, and this document does not provide detailed instructions. The specific relationship between the official and third-party source code obfuscation capabilities is as follows:

Due to the restrictions of HarmonyOS security mechanisms such as code signing and application encryption, as well as the purity and security requirements for application market listing review, the security hardening content provided by third-party hardening vendors must meet the following six requirements:

1. Hiding calls to sensitive system APIs is not allowed. Reviewers must be able to clearly see the features of the application.

2. Obfuscating SDKs that are not self-developed is not allowed. SDKs should be protected by obfuscation by the SDK vendors themselves. If a non-self-developed SDK is obfuscated, it will affect the fingerprint information of the relevant SDK during application market review.

3. Applications hardened by third-party security hardening must ensure that they do not contain malicious behavior, so as to avoid affecting the ecosystem. This requirement is a binding clause, and non-compliance may result in the application being removed from the market.

4. Using third-party virtual machines is not allowed. The HarmonyOS system restricts dynamic code loading through mechanisms such as code signing, which may cause the application to fail to run properly.

5. Tampering with Ark bytecode files is not allowed. This method may cause the application to fail to run properly and affect the application market's review of the application's purity and security.

6. Using hook technology on system libraries is not allowed. This method affects the application market's review of the application's purity and security.

## Sample Code

-   [Application Security Sample Code](https://gitcode.com/HarmonyOS_Samples/BestPracticeSnippets/tree/master/Privacy)
<!--no_check-->