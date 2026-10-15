# z_stream_s

## Overview

## Summary

### Member variables

| Name | Description |
| -- | -- |
| z_const Bytef *next_in |  |
| /* next input byte */
    uInt     avail_in |  |
| /* number of bytes available at next_in */
    uLong    total_in |  |
| /* total number of input bytes read so far */

    Bytef    *next_out |  |
| /* next output byte will go here */
    uInt     avail_out |  |
| /* remaining free space at next_out */
    uLong    total_out |  |
| /* total number of bytes output so far */

    z_const char *msg |  |
| /* last error message, NULL if no error */
    struct internal_state FAR *state |  |
| /* not visible by applications */

    alloc_func zalloc |  |
| /* used to allocate the internal state */
    free_func  zfree |  |
| /* used to free the internal state */
    voidpf     opaque |  |
| /* private data object passed to zalloc and zfree */

    int     data_type |  |
| /* best guess about the data type: binary or text
                           for deflate, or the decoding state for inflate */
    uLong   adler |  |
| /* Adler-32 or CRC-32 value of the uncompressed data */
    uLong   reserved |  |
| /* reserved for future use */ |  |


