# aiocb

## Overview

<!--Device-struct aiocb {...}--><!--Device-struct aiocb {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int aio_fildes, aio_lio_opcode, aio_reqprio | <!--Device-int aio_fildes, aio_lio_opcode, aio_reqprio--><!--Device-int aio_fildes, aio_lio_opcode, aio_reqprio-End--> |
| volatile void *aio_buf | <!--Device-volatile void *aio_buf--><!--Device-volatile void *aio_buf-End--> |
| size_t aio_nbytes | <!--Device-size_t aio_nbytes--><!--Device-size_t aio_nbytes-End--> |
| struct sigevent aio_sigevent | <!--Device-struct sigevent aio_sigevent--><!--Device-struct sigevent aio_sigevent-End--> |
| void *\_\_td | <!--Device-void *\_\_td--><!--Device-void *\_\_td-End--> |
| int \_\_lock[2] | <!--Device-int \_\_lock[2]--><!--Device-int \_\_lock[2]-End--> |
| volatile int \_\_err | <!--Device-volatile int \_\_err--><!--Device-volatile int \_\_err-End--> |
| ssize_t \_\_ret | <!--Device-ssize_t \_\_ret--><!--Device-ssize_t \_\_ret-End--> |
| off_t aio_offset | <!--Device-off_t aio_offset--><!--Device-off_t aio_offset-End--> |
| void *\_\_next, *\_\_prev | <!--Device-void *\_\_next, *\_\_prev--><!--Device-void *\_\_next, *\_\_prev-End--> |
| char \_\_dummy4[32-2*sizeof(void *)] | <!--Device-char \_\_dummy4[32-2*sizeof(void *)]--><!--Device-char \_\_dummy4[32-2*sizeof(void *)]-End--> |


