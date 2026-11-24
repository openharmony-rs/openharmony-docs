# es2abc Compiler Error Codes

<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @zmw1; @huyunhui1-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=a3060ae52da1175934620117ac290fde01050c23 translatedAt=2026-11-06T09:06:26.705Z pushedAt=2026-11-09T09:21:54.958Z nl=1 -->

> **NOTE**
>
> This section lists the error codes specific to the es2abc (ECMAScript to Ark Bytecode) compiler module. For general error codes, see [Universal Error Codes](../errorcode-universal.md).

## 10705000 Syntax Error

**Error Message**

Example
```txt
ERROR: 10705000 Syntax Error
SyntaxError: Concurrent function should only use import variable or local variable, 'a' is not one of them [/path/to/wrong/file.ts:9:4]
```

**Description**

A syntax error occurs when the compiler cannot parse a certain syntax structure in the source file. The error message includes the specific file name and location information (line number and column number).

**Possible Causes**

1. The code contains illegal or incomplete syntax, such as missing brackets or incorrect structure nesting.
2. The code uses language features that are not supported by the current version.
3. The keyword or syntax structure cannot be identified due to spelling errors.
4. Encryption software in the development environment may modify the file encoding format.

**Solution**

1. Locate the error based on the file name and line number in the error message.
2. Fix syntax errors, for example, add missing brackets or keywords.
3. Use the syntax check tool of DevEco Studio to detect syntax errors.
4. If the new syntax feature is used, ensure that the current compiler version supports the feature.
5. If encryption software is used, disable the encryption software and recompile.

## 10706001 Unsupported Change

**Error Message**

Example
```txt
ERROR: 10706001 Found unsupported change in file, failed to generate patch abc!
[Patch] Found lexical variable added or removed in ${functionName}, not supported!
[Patch] Found unsupported change in file, will not generate patch!
Error:  [base_mod.js:0:0]
```

**Description**

Patch mode is an incremental compilation mode. When a source file is modified, only the modified parts are compiled to generate patch bytecode, which works with the original bytecode to complete the functional update. The compiler detects that the source file contains changes that fall outside the scope supported by patch mode, and therefore terminates patch generation. Such changes typically involve code modifications that have a significant impact on semantics, such as scope, variable declarations, and import structures.

**Possible Causes**

1. During the patch build process, the lexical variables of a module (outer-scope variables referenced by inner functions) are modified, for example, declarations are added or deleted;
2. Key functions are deleted or existing variables are redeclared.
3. Destructive modifications are made to the import/export structure or module boundaries;
4. The file changes exceed the scope supported by es2abc incremental compilation (patch mode).

**Solution**

1. Check the file and code changes in the error message.
2. Avoid adding, deleting, or renaming variables or functions defined in the module;
3. If semantic changes are required, select full compilation instead of incremental compilation.
