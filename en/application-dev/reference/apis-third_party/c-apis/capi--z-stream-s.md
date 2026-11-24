# z_stream_s

## Overview

<!--Device-struct z_stream_s {...}--><!--Device-struct z_stream_s {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| z_const Bytef *next_in | <!--Device-z_const Bytef *next_in--><!--Device-z_const Bytef *next_in-End--> |
| /* next input byte */
    uInt     avail_in | <!--Device-/* next input byte */ uInt avail_in--><!--Device-/* next input byte */ uInt avail_in-End--> |
| /* number of bytes available at next_in */
    uLong    total_in | <!--Device-/* number of bytes available at next_in */ uLong total_in--><!--Device-/* number of bytes available at next_in */ uLong total_in-End--> |
| /* total number of input bytes read so far */

    Bytef    *next_out | <!--Device-/* total number of input bytes read so far */ Bytef *next_out--><!--Device-/* total number of input bytes read so far */ Bytef *next_out-End--> |
| /* next output byte will go here */
    uInt     avail_out | <!--Device-/* next output byte will go here */ uInt avail_out--><!--Device-/* next output byte will go here */ uInt avail_out-End--> |
| /* remaining free space at next_out */
    uLong    total_out | <!--Device-/* remaining free space at next_out */ uLong total_out--><!--Device-/* remaining free space at next_out */ uLong total_out-End--> |
| /* total number of bytes output so far */

    z_const char *msg | <!--Device-/* total number of bytes output so far */ z_const char *msg--><!--Device-/* total number of bytes output so far */ z_const char *msg-End--> |
| /* last error message, NULL if no error */
    struct internal_state FAR *state | <!--Device-/* last error message, NULL if no error */ struct internal_state FAR *state--><!--Device-/* last error message, NULL if no error */ struct internal_state FAR *state-End--> |
| /* not visible by applications */

    alloc_func zalloc | <!--Device-/* not visible by applications */ alloc_func zalloc--><!--Device-/* not visible by applications */ alloc_func zalloc-End--> |
| /* used to allocate the internal state */
    free_func  zfree | <!--Device-/* used to allocate the internal state */ free_func zfree--><!--Device-/* used to allocate the internal state */ free_func zfree-End--> |
| /* used to free the internal state */
    voidpf     opaque | <!--Device-/* used to free the internal state */ voidpf opaque--><!--Device-/* used to free the internal state */ voidpf opaque-End--> |
| /* private data object passed to zalloc and zfree */

    int     data_type | <!--Device-/* private data object passed to zalloc and zfree */ int data_type--><!--Device-/* private data object passed to zalloc and zfree */ int data_type-End--> |
| /* best guess about the data type: binary or text
                           for deflate, or the decoding state for inflate */
    uLong   adler | <!--Device-/* best guess about the data type: binary or text for deflate, or the decoding state for inflate */ uLong adler--><!--Device-/* best guess about the data type: binary or text for deflate, or the decoding state for inflate */ uLong adler-End--> |
| /* Adler-32 or CRC-32 value of the uncompressed data */
    uLong   reserved | <!--Device-/* Adler-32 or CRC-32 value of the uncompressed data */ uLong reserved--><!--Device-/* Adler-32 or CRC-32 value of the uncompressed data */ uLong reserved-End--> |
| /* reserved for future use */ | <!--Device-/* reserved for future use */--><!--Device-/* reserved for future use */-End--> |


