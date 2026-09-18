# z_stream_s

## Overview

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uInt avail_in | next input byte |
| uLong total_in | number of bytes available at next_in |
| Bytef *next_out | total number of input bytes read so far |
| uInt avail_out | next output byte will go here |
| uLong total_out | remaining free space at next_out |
| z_const char *msg | total number of bytes output so far |
| struct internal_state FAR *state | last error message, NULL if no error |
| alloc_func zalloc | not visible by applications |
| free_func zfree | used to allocate the internal state |
| voidpf opaque | used to free the internal state |
| int data_type | private data object passed to zalloc and zfree |
| uLong adler | best guess about the data type: binary or text for deflate, or the decoding state for inflate |
| uLong reserved | Adler-32 or CRC-32 value of the uncompressed data |
| [](capi--z-stream-s.md) | reserved for future use |


