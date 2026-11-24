# v_barrier_t

## Overview

<!--Device-struct v_barrier_t {...}--><!--Device-struct v_barrier_t {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| unsigned int n | <!--Device-unsigned int n--><!--Device-unsigned int n-End--> |
| unsigned int count | <!--Device-unsigned int count--><!--Device-unsigned int count-End--> |
| uv_mutex_t mutex | <!--Device-uv_mutex_t mutex--><!--Device-uv_mutex_t mutex-End--> |
| uv_sem_t turnstile1 | <!--Device-uv_sem_t turnstile1--><!--Device-uv_sem_t turnstile1-End--> |
| uv_sem_t turnstile2 | <!--Device-uv_sem_t turnstile2--><!--Device-uv_sem_t turnstile2-End--> |


