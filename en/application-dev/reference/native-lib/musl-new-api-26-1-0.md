# New APIs in musl 26.1.0

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @da_wei_li11-->
<!--Designer: @liyiming13-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=eaf834c0e8a7b1d52ab7109799c81fa57c16f64e translatedAt=2026-11-03T13:44:22.775Z pushedAt=2026-11-04T07:11:15.438Z nl=1 -->

## Overview

OpenHarmony uses musl as its C standard library. The musl library is a lightweight, fast, simple, and free open-source libc library. For a detailed description, see the [musl official reference manual](https://musl.libc.org/manual.html).

This document describes the interfaces newly added to musl in API version 26.1.0.

**Related module:** [libc standard library](musl.md)

## group_sem_open

`group_sem_open` is an OpenHarmony extended interface used to create or open a named semaphore under the specified `gid`. For a detailed description, see [group_ipc.h](capi-group-ipc-h.md).

## group_sem_unlink

`group_sem_unlink` is an OpenHarmony extended interface used to remove the name of a named semaphore under a specified `gid`. For a detailed description, see [group_ipc.h](capi-group-ipc-h.md).

## group_shm_open

`group_shm_open` is an OpenHarmony extended interface used to create or open a shared memory object under a specified `gid`. For a detailed description, see [group_ipc.h](capi-group-ipc-h.md).

## group_shm_unlink

`group_shm_unlink` is an OpenHarmony extended interface used to remove the name of a shared memory object under a specified `gid`. For a detailed description, see [group_ipc.h](capi-group-ipc-h.md).
