# fileIo

本模块是Core File Kit的核心模块，提供基础文件操作API，用于对应用沙箱内的文件和目录进行创建、打开、读写、拷贝、移动、删除、查询属性等操作。 模块提供了多种文件访问模式，开发者可根据场景选择： 基于文件描述符（fd）：通过open获取File对象，再使用read/write进行读写，适用于通用文件读写场景。 基于流（Stream）：通过createStream/fdopenStream创建Stream，或通过createReadStream/createWriteStream创建ReadStream/WriteStream，适用于流式数据处理或大文件分块读写等场景。 基于RandomAccessFile：通过createRandomAccessFile创建RandomAccessFile对象，支持独立的偏移指针和随机读写，适用于需要频繁跳转读写位置的场景。 此外，模块还提供文件监听（Watcher）、内存映射（FileMapping）、安全原子写入（AtomicFile）等其他能力。 > **使用说明：** 使用该功能模块对文件/目录进行操作前，需要先获取其应用沙箱路径，获取沙箱路径的方式及其接口用法可参考： [应用上下文Context-获取应用文件路径](../../../application-models/application-context-stage.md#获取应用文件路径)。<br/> 指向资源的字符串称为URI。对于只支持沙箱路径作为入参的接口，可以使用构造fileUri对象并获取其沙箱路径的属性的方式将URI转换为沙箱路径，然后使用文件接口。 URI定义及其转换方式请参考：[文件URI](arkts-file-fileuri.md)。

**起始版本：** 9

<!--Device-unnamed-declare namespace fileIo--><!--Device-unnamed-declare namespace fileIo-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
import { fileIo } from '@kit.CoreFileKit'
import { ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, TaskSignal } from '@kit.CoreFileKit';
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [OpenMode](arkts-corefile-fileio-openmode-n.md) | open接口flags参数常量，用于指定文件打开模式（如只读、只写、读写、创建等）。 |

