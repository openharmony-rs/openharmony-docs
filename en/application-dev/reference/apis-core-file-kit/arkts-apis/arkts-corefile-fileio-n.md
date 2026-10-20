# fileIo(File Management)

```TypeScript
declare namespace fileIo
```

This module is the core module of Core File Kit. It provides APIs for basic file operations, such as creating, opening, reading, writing, copying, moving, deleting, and querying files and directories in the application sandbox.

This module provides multiple file access modes. You can select a mode based on your specific requirements:

Based on the file descriptor (FD): You can obtain a <b>File</b> object using the <b>open</b> API and then read data from the file or write data to the file using the <b>read</b> or <b>write</b> API. This mode is suitable for common file read/write scenarios. Based on the stream: You can create a <b>Stream</b> object using <b>createStream</b> or <b>fdopenStream</b>, or create a <b>ReadStream</b> or <b>WriteStream</b> object using <b>createReadStream</b> or <b>createWriteStream</b>. This mode is suitable for scenarios such as stream data processing or block-based read/write of large files. Based on <b>RandomAccessFile</b>: You can create a <b>RandomAccessFile</b> object using <b>createRandomAccessFile</b>. This mode supports independent offset pointers and random read/write operations, which is suitable for scenarios where frequent jumps between read/write positions are required. In addition, this module provides other capabilities such as <b>Watcher</b>, <b>FileMapping</b>, and <b>AtomicFile</b>.

> **How to Use**

Before using the APIs provided by this module to perform operations on a file or directory, obtain the application sandbox path of the file or directory as follows: [Obtain application file paths] (../../../application-models/application-context-stage.md#obtaining-application-file-paths). <br> A uniform resource identifier (URI) is a string pointing to a resource. For APIs that support only the sandbox path as the input parameter, you can construct a <b>fileUri</b> object and obtain the sandbox path property to convert the URI to the sandbox path, and then use the APIs. For details about the URI definition and how to convert a URI to a path, see [File URI](../../../reference/apis-core-file-kit/js-apis-file-fileuri.md).

**Since:** 9

<!--Device-unnamed-declare namespace fileIo--><!--Device-unnamed-declare namespace fileIo-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [OpenMode](arkts-corefile-fileio-openmode-n.md) | Enumerates the constants of the <b>mode</b> parameter used in <b>open()</b>, which specifies the file opening mode, such as <b>READ_ONLY</b>, <b>WRITE_ONLY</b>, <b>READ_WRITE</b>, or <b>CREATE</b>. |
