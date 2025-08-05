# 编译工具链错误码
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @aftott-->
<!--SE: @hufeng20-->
<!--TSE: @kirl75; @zsw_zhushiwei-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 10311001 导入ArkTS文件错误

**错误信息**

Importing ArkTS files in JS and TS files is forbidden.

**错误描述**

禁止在JS和TS文件中导入ArkTS文件。

**可能原因**

在JS和TS文件中导入了ArkTS文件。

**处理步骤**

请移除JS和TS文件中的ArkTS文件导入语句。

## 10311002 解析OhmUrl错误

**错误信息**

Failed to resolve OhmUrl. Failed to get a resolved OhmUrl for `${filePath}` imported by `${importerFile}`.

**错误描述**

无法解析OhmUrl。无法为`${importerFile}`导入的`${filePath}`获取解析后的OhmUrl。

**可能原因**

`${filePath}`所属的`${pkgName}`模块配置错误。

**处理步骤**

1. 检查`${filePath}`所属的`${pkgName}`模块是否配置正确。
2. 检查对应的文件名是否正确（包括大小写敏感）。

## 10311003 获取Kit配置文件错误

**错误信息**

Kit `${moduleRequest}` has no corresponding config file in ArkTS SDK.

**错误描述**

Kit `${moduleRequest}` 在ArkTS SDK中没有对应的配置文件。

**可能原因**

1. Kit的API与SDK不一致。
2. Kit的API在本地被修改。

**处理步骤**

1. 请确保Kit的API与SDK一致，并且Kit的API没有被本地修改。
2. 有关Kit API的更多详细信息，请参考<!--RP1-->[开发说明](../development-intro-api.md)。<!--RP1End-->

## 10311005 导入Kit标识符错误

**错误信息**

Identifier `${this.importName}` comes from `${this.symbol.source}` which can not be imported in .ts file.

**错误描述**

标识符`${this.importName}`来自`${this.symbol.source}`，该标识符不能在.ts文件中导入。

**可能原因**

在TS文件中导入了ArkTS文件的Kit模块。

**处理步骤**

请移除导入语句或将文件扩展名更改为.ets。

## 10311006 导入名称未从Kit中导出错误

**错误信息**

`${importName}` is not exported from Kit `${KitInfo.getCurrentKitName()}`.

**错误描述**

`${importName}`没有从Kit `${KitInfo.getCurrentKitName()}` 中导出。

**可能原因**

1. Kit的API与SDK不一致。
2. Kit的API在本地被修改。

**处理步骤**

1. 请确保Kit的API与SDK一致，并且Kit的API没有被本地修改。
2. 有关Kit API的更多详细信息，请参考<!--RP1-->[开发说明](../development-intro-api.md)。<!--RP1End-->

## 10311007 Kit命名空间导入或导出错误

**错误信息**

Namespace import or export of Kit is not supported currently.

**错误描述**

当前不支持Kit的命名空间导入或导出。

**可能原因**

文件中使用了Kit的命名空间导入或导出。

**处理步骤**

请将Kit的命名空间导入或导出替换为命名导入或导出。例如，`import * as ArkTS from "@kit.ArkUI";` -> `import { AlertDialog } from "@kit.ArkUI";`。

## 10311008 Kit空导入错误

**错误信息**

Can not use empty import(side-effect import) statement with Kit `${(kitNode.moduleSpecifier as ts.StringLiteral).text.replace(/'|"/g, '')}`.

**错误描述**

无法在Kit `${(kitNode.moduleSpecifier as ts.StringLiteral).text.replace(/'|"/g, '')}` 中使用空导入（副作用导入）语句。

**可能原因**

文件中使用了Kit的空导入（副作用导入）语句。

**处理步骤**

请明确指定导入的符号。例如，`import "@kit.ArkUI";` -> `import { lang } from "@kit.ArkUI";`。

## 10311009 ES2ABC执行错误

**错误信息**

Failed to execute es2abc.

**错误描述**

无法执行es2abc。

**可能原因**

es2abc执行过程中出现错误。

**处理步骤**

请参考es2abc的错误码进行处理。

## 10311010 懒加载导入重新导出错误

**错误信息**

`${elementText}` of lazy-import is re-export.

**错误描述**

`${elementText}`的懒加载导入被重新导出。

**可能原因**

重新导出了经过懒加载导入的`${elementText}`。

**处理步骤**

1. 请确保懒加载导入的命名绑定没有被重新导出。
2. 请检查是否开启了autoLazyImport开关。
