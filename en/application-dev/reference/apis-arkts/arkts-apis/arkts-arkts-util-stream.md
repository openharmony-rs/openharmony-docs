# @ohos.util.stream(Stream)

The stream module provides APIs to process basic types of streams. With streams, data is read or written by chunk, instead of being loaded to the memory at a time. There are four fundamental stream types: writable streams ([Writable](arkts-arkts-stream-writable-c.md)), readable streams ([Readable](arkts-arkts-stream-readable-c.md)), duplex streams ([Duplex](arkts-arkts-stream-duplex-c.md)), and transform streams ([Transform](arkts-arkts-stream-transform-c.md)).

**Since:** 12

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { stream } from '@kit.ArkTS';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [Duplex](arkts-arkts-stream-duplex-c.md) | A stream that is both readable and writable. A duplex stream allows data to be transmitted in two directions, that is, data can be read and written. The **Duplex** class inherits from [Readable](arkts-arkts-stream-readable-c.md) and supports all the APIs in **Readable**. |
| [Readable](arkts-arkts-stream-readable-c.md) | Stream from which data can be read. A readable stream is used to read data from a source, such as a file or a network socket. |
| [Transform](arkts-arkts-stream-transform-c.md) | A special duplex stream that supports data conversion and result output. The **Transform** class inherits from [Duplex](arkts-arkts-stream-duplex-c.md) and supports all the APIs in **Duplex**. |
| [Writable](arkts-arkts-stream-writable-c.md) | Stream to which data can be written. A writable stream allows data to be written to a target, which can be a file, an HTTP response, a standard output, another stream, or the like. |

### Interfaces

| Name | Description |
| --- | --- |
| [ReadableOptions](arkts-arkts-stream-readableoptions-i.md) | Describes the options used in the **Readable** constructor. |
