# @ohos.fastbuffer(FastBuffer)

The FastBuffer class is a container type for dealing with binary data directly. It can be constructed in a variety of ways.

@namespace fastbuffer

**Since:** 20

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { fastbuffer } from '@kit.ArkTS';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [alloc](arkts-arkts-fastbuffer-alloc-f.md) | Allocates a new FastBuffer for a fixed size bytes. If fill is undefined, the FastBuffer will be zero-filled. |
| [allocUninitialized](arkts-arkts-fastbuffer-allocuninitialized-f.md) | Allocates a new un-pooled FastBuffer for a fixed size bytes. The FastBuffer will not be initially filled. |
| [allocUninitializedFromPool](arkts-arkts-fastbuffer-allocuninitializedfrompool-f.md) | Allocates a new FastBuffer for a fixed size bytes. The FastBuffer will not be initially filled. |
| [byteLength](arkts-arkts-fastbuffer-bytelength-f.md) | Returns the byte length of a string when encoded using `encoding`. This is not the same as [`String.prototype.length`], which does not account for the encoding that is used to convert the string into bytes. |
| [compare](arkts-arkts-fastbuffer-compare-f.md) | Compares buf1 to buf2 |
| [concat](arkts-arkts-fastbuffer-concat-f.md) | Returns a new `FastBuffer` which is the result of concatenating all the `FastBuffer`instances in the `list` together. |
| [from](arkts-arkts-fastbuffer-from-f.md) | Allocates a new FastBuffer using an array of bytes in the range 0 – 255. Array entries outside that range will be truncated to fit into it. |
| [from](arkts-arkts-fastbuffer-from-f.md) | This creates a view of the ArrayBuffer without copying the underlying memory. |
| [from](arkts-arkts-fastbuffer-from-f.md) | Copies the passed buffer data onto a new FastBuffer instance. |
| [from](arkts-arkts-fastbuffer-from-f.md) | Creates a new FastBuffer containing string. The encoding parameter identifies the character encoding to be used when converting string into bytes. |
| [isBuffer](arkts-arkts-fastbuffer-isbuffer-f.md) | Returns true if obj is a FastBuffer, false otherwise |
| [isEncoding](arkts-arkts-fastbuffer-isencoding-f.md) | Returns true if encoding is the name of a supported character encoding, or false otherwise. |
| [transcode](arkts-arkts-fastbuffer-transcode-f.md) | Re-encodes the given FastBuffer or Uint8Array instance from one character encoding to another. |

### Classes

| Name | Description |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | The FastBuffer object is a method of handling buffers dedicated to binary data. |

### Interfaces

| Name | Description |
| --- | --- |
| [TypedArray](arkts-arkts-fastbuffer-typedarray-i.md) | TypedArray inherits the features and methods of Int8Array |

### Types

| Name | Description |
| --- | --- |
| [BufferEncoding](arkts-arkts-fastbuffer-bufferencoding-t.md) | This parameter specifies the type of a common encoding format. |
