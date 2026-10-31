# Distributed File System Overview
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @yangwei_814916-->
<!--Designer: @hwzhangchuang; @Dyylll-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=23fd3050bf417376fb6020b82cd43307338e4432 translatedAt=2026-10-29T10:30:53.786Z pushedAt=2026-10-29T10:30:53.786Z nl=1 -->

OpenHarmony distributed file system (hmdfs) provides cross-device file access capabilities in the following scenarios:

- The user uses the editing software on one device to edit the files on another device.

- Music stored on a tablet can be directly viewed and played by an in-car infotainment system.

- The user uses a tablet to view the photos taken by another device.

The hmdfs provides a globally consistent access view across devices dynamically connected to a network via DSoftBus and allows you to implement high-performance read and write operations on files with low latency by using basic file system APIs.

## Distributed File System Architecture

![Distributed File System Architecture](figures/distributed-file-system-architecture.png)

- distributedfile_daemon: listens for device online status, establishes links over DSoftBus, and applies data transfer policies based on the security level of the device.

- hmdfs: implements a network file system in the kernel and provides cache management, file access, metadata management, and conflict resolution.
  > **NOTE**
  >
  > Files in the directory [/data/storage/el2/distributedfiles/](app-sandbox-directory.md#mappings-between-application-sandbox-paths-and-physical-paths) must not be deleted arbitrarily. For details, see [Accessing Files Across Devices](file-access-across-devices.md).

  - Cache management
    - After devices join a distributed network, hmdfs allows access to files on other devices but does not proactively transfer or copy file data. Applications must explicitly copy data that needs to be saved locally.
    - The hmdfs ensures close-to-open cache consistency, which allows data to be flushed when a client closes a file. Then, the latest data can be read when the file is opened on any other client. The hmdfs does not ensure real-time consistency of the file content.
    - If data written remotely cannot be flushed back locally in time because of network issues, the file system flushes it back when the network reconnects. However, it cannot do so if the remote data has already changed.
  - File access
    - OpenHarmony provides the unified [ohos.file.fs](../reference/apis-core-file-kit/js-apis-file-fs.md) APIs for accessing the local and distributed file systems.
    - The files in the local file system are accessed in overlay mode.
    - Files on other devices are accessed through synchronous network requests.
        > **NOTE**
        >
        > symlink is not supported.
  - Metadata management
    - In distributed networking, file creation, deletion, and modification on a device are synced to another device, at a speed subject to the network condition.
    - When a remote device goes offline, its data is no longer displayed locally. However, detecting that a device is offline takes time, and some messages may time out after 4 seconds. Account for API network timeouts and cases where files remain visible even though their device is already offline.
  - Conflict resolution
    - If a local file has the same name as a remote file, a conflict occurs. The file synced from the remote device to the local device is automatically renamed, while the local file name remains unchanged.
    - If a file name conflict occurs between multiple remote devices, the name of the file with the smallest device access ID is retained and the files on other devices are renamed.
    - If the directory tree already has remote files in networking scenario, a file with a duplicate file name cannot be created successfully.
    - Conflicting files are renamed by appending **_conflict_dev** followed by an ID that increments automatically from 1.
    - Directories with the same name are merged without a conflict. If a file has the same name as a remote directory, **_remote_directory** is appended to the remote directory name.
