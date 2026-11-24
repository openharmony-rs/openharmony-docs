# v__io_s

## Overview

<!--Device-struct v__io_s {...}--><!--Device-struct v__io_s {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| unsigned int events | Pending event mask i.e. mask at next tick.<br><!--Device-unsigned int events--><!--Device-unsigned int events-End--> |
| int fd;
 UV_IO_PRIVATE_PLATFORM_FIELDS | Current event mask.<br><!--Device-int fd; UV_IO_PRIVATE_PLATFORM_FIELDS--><!--Device-int fd; UV_IO_PRIVATE_PLATFORM_FIELDS-End--> |
| uv\_\_io_cb cb | <!--Device-uv\_\_io_cb cb--><!--Device-uv\_\_io_cb cb-End--> |
| void* pending_queue[2] | <!--Device-void* pending_queue[2]--><!--Device-void* pending_queue[2]-End--> |
| void* watcher_queue[2] | <!--Device-void* watcher_queue[2]--><!--Device-void* watcher_queue[2]-End--> |
| unsigned int pevents | <!--Device-unsigned int pevents--><!--Device-unsigned int pevents-End--> |
| /* Current event mask. */
 int fd | <!--Device-/* Current event mask. */ int fd--><!--Device-/* Current event mask. */ int fd-End--> |


