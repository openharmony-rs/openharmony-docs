# gz_header_s

## Overview

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uLong time | true if compressed data believed to be text |
| int xflags | modification time |
| int os | extra flags (not used when writing a gzip file) |
| Bytef *extra | operating system |
| uInt extra_len | pointer to extra field or Z_NULL if none |
| uInt extra_max | extra field length (valid if extra != Z_NULL) |
| Bytef *name | space at extra (only when reading header) |
| uInt name_max | pointer to zero-terminated file name or Z_NULL |
| Bytef *comment | space at name (only when reading header) |
| uInt comm_max | pointer to zero-terminated comment or Z_NULL |
| int hcrc | space at comment (only when reading header) |
| int done | true if there was or will be a header crc |
| [](capi--z-stream-s.md) | true when done reading gzip header (not used when writing a gzip file) |


