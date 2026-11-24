# gz_header_s

## Overview

<!--Device-struct gz_header_s {...}--><!--Device-struct gz_header_s {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uLong time | true if compressed data believed to be text<br><!--Device-uLong time--><!--Device-uLong time-End--> |
| int xflags | modification time<br><!--Device-int xflags--><!--Device-int xflags-End--> |
| int os | extra flags (not used when writing a gzip file)<br><!--Device-int os--><!--Device-int os-End--> |
| Bytef *extra | operating system<br><!--Device-Bytef *extra--><!--Device-Bytef *extra-End--> |
| uInt extra_len | pointer to extra field or Z_NULL if none<br><!--Device-uInt extra_len--><!--Device-uInt extra_len-End--> |
| uInt extra_max | extra field length (valid if extra != Z_NULL)<br><!--Device-uInt extra_max--><!--Device-uInt extra_max-End--> |
| Bytef *name | space at extra (only when reading header)<br><!--Device-Bytef *name--><!--Device-Bytef *name-End--> |
| uInt name_max | pointer to zero-terminated file name or Z_NULL<br><!--Device-uInt name_max--><!--Device-uInt name_max-End--> |
| Bytef *comment | space at name (only when reading header)<br><!--Device-Bytef *comment--><!--Device-Bytef *comment-End--> |
| uInt comm_max | pointer to zero-terminated comment or Z_NULL<br><!--Device-uInt comm_max--><!--Device-uInt comm_max-End--> |
| int hcrc | space at comment (only when reading header)<br><!--Device-int hcrc--><!--Device-int hcrc-End--> |
| int done | true if there was or will be a header crc<br><!--Device-int done--><!--Device-int done-End--> |
| [](capi--gzfile-s.md) | true when done reading gzip header (not used when writing a gzip file)<br><!--Device---><!--Device--End--> |
| int text | <!--Device-int text--><!--Device-int text-End--> |


