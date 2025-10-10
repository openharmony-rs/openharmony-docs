# 应用文件访问(ArkTS)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @liuhonggang123; @yue-ye2; @juxiaopang-->
<!--Adviser: @foryourself-->

应用需要对应用文件目录下的应用文件进行查看、创建、读写、删除、移动、复制、获取属性等访问操作，下文介绍具体方法。

## 接口说明

开发者通过基础文件操作接口（[ohos.file.fs](../reference/apis-core-file-kit/js-apis-file-fs.md)）实现应用文件访问能力，主要功能如下表所示。

**表1** 基础文件操作接口功能，其中“√”表示支持，“-”表示不区分同步和异步。

| 接口名 | 功能 | 接口类型 | 支持同步 | 支持异步 |
| -------- | -------- | -------- | -------- | -------- |
| access | 检查文件是否存在 | 方法 | √ | √ |
| close | 关闭文件 | 方法 | √ | √ |
| copyFile | 复制文件 | 方法 | √ | √ |
| createStream | 基于文件路径打开文件流 | 方法 | √ | √ |
| listFile | 列出文件夹下所有文件名 | 方法 | √ | √ |
| mkdir | 创建目录 | 方法 | √ | √ |
| moveFile | 移动文件 | 方法 | √ | √ |
| open | 打开文件 | 方法 | √ | √ |
| read | 从文件读取数据 | 方法 | √ | √ |
| rename | 重命名文件或文件夹 | 方法 | √ | √ |
| rmdir | 删除整个目录 | 方法 | √ | √ |
| stat | 获取文件详细属性信息 | 方法 | √ | √ |
| unlink | 删除单个文件 | 方法 | √ | √ |
| write | 将数据写入文件 | 方法 | √ | √ |
| Stream.close | 关闭文件流 | 方法 | √ | √ |
| Stream.flush | 刷新文件流 | 方法 | √ | √ |
| Stream.write | 将数据写入流文件 | 方法 | √ | √ |
| Stream.read | 从流文件读取数据 | 方法 | √ | √ |
| File.fd | 获取文件描述符 | 属性 | - | - |
| OpenMode | 设置文件打开标签 | 属性 | - | - |
| Filter | 设置文件过滤配置项 | 类型 | - | - |

> **注意：**
>
> 使用基础文件操作接口时，耗时较长的操作，例如：read、write等，建议使用异步接口，避免应用崩溃。

## 开发示例

在对应用文件开始访问前，开发者需要[获取应用文件路径](../application-models/application-context-stage.md#获取应用文件路径)。以从UIAbilityContext获取HAP级别的文件路径为例进行说明，UIAbilityContext的获取方式请参见[获取UIAbility的上下文信息](../application-models/uiability-usage.md#获取uiability的上下文信息)。

下面介绍几种常用操作示例。

### 新建并读写一个文件

以下示例代码演示了如何新建一个文件并对其读写。

```ts
// pages/xxx.ets
import { fileIo as fs, ReadOptions } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';
import { buffer } from '@kit.ArkTS';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

```
<!--@[create_and_read_File](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/FileApiFileSample/entry/src/main/ets/pages/Index.ets)-->

### 读取文件内容并写入到另一个文件

以下示例代码演示了如何从一个文件读写内容到另一个文件。

```ts
// pages/xxx.ets
import { fileIo as fs, ReadOptions, WriteOptions } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

```
<!--@[read_write_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/FileApiFileSample/entry/src/main/ets/pages/Index.ets)-->

> **说明：**
>
> 使用读写接口时，需注意可选项参数offset的设置。对于已存在且读写过的文件，文件偏移指针默认在上次读写操作的终止位置。

### 以流的形式读写文件

以下示例代码演示了如何使用流接口读取test.txt的文件内容并写入到destFile.txt文件中。

```ts
// pages/xxx.ets
import { fileIo as fs, ReadOptions } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

```
<!--@[read_write_file_with_stream](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/FileApiFileSample/entry/src/main/ets/pages/Index.ets)-->


> **说明：**
>
> 使用流接口时，需注意流的及时关闭。同时流的异步接口应严格遵循异步接口使用规范，避免同步、异步接口混用。流接口不支持并发读写。

### 查看文件列表

以下示例代码演示了如何查看文件列表。

```ts
import { fileIo as fs, Filter, ListFileOptions } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

```
<!--@[get_list_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/FileApiFileSample/entry/src/main/ets/pages/Index.ets)-->

### 使用文件流

以下示例代码演示了如何使用文件可读流，文件可写流。

```ts
// pages/xxx.ets
import { fileIo as fs } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

```
<!--@[copy_file_with_readable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/FileApiFileSample/entry/src/main/ets/pages/Index.ets)-->

<!--@[copy_file_with_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/FileApiFileSample/entry/src/main/ets/pages/Index.ets)-->

### 使用文件哈希流

哈希流是一种数据传输和存储技术，可以将任意长度的数据转换为固定长度的哈希值来验证数据的完整性和一致性。以下代码演示了如何使用文件哈希处理接口（[ohos.file.hash](../reference/apis-core-file-kit/js-apis-file-hash.md)）来处理文件哈希流。

```ts
// pages/xxx.ets
import { fileIo as fs } from '@kit.CoreFileKit';
import { hash } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

// 获取应用文件路径，请在组件内获取context
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;


```
<!--@[hash_file_with_stream](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/FileApiFileSample/entry/src/main/ets/pages/Index.ets)-->