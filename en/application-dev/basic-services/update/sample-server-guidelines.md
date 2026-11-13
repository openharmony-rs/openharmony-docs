# Sample Server Development
<!--Kit: Basic Services Kit-->
<!--Subsystem: Update-->
<!--Owner: @RainyDay_005; @huangsiping3-->
<!--Designer: @zhangzhengxue; @jackd320-->
<!--Tester: @mamba-ting-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=79856d4a32c6c2cad3ed703a5e8afb443a4d2904 translatedAt=2026-11-06T12:07:46.545Z pushedAt=2026-11-09T12:34:03.236Z nl=1 -->

## Introduction

Sample Server: online upgrade of the local emulation environment

This tool is intended to simulate the package search server in a production environment and builds a secure communication channel based on the SSL protocol. It supports version detection and upgrade package metadata query, and can return key data such as the version details, file checksum, and size of an upgrade package, helping developers simulate the online upgrade process in a zero-dependency local environment.

Core application scenarios:

- Feature development and debugging: provide an independent test data source for the online upgrade module.

- Local process verification: verify the complete logic loop from update detection to upgrade package download without network access.

- Package format compatibility testing: quickly verify the correctness of parsing and processing upgrade packages in different formats.

## How to Develop

To develop the sample server, complete the following steps:

### Prepare the SSL certificate.

Generate the serverKey.pem and serverCert.cer files for SSL protocol communication of the sample server.

```shell
openssl req -newkey rsa:2048 -nodes -keyout serverKey.pem -x509 -days 365 -out serverCert.cer -subj "/C=CN/ST=GD/L=GZ/O=abc/OU=defg/CN=hijk/emailAddress=test.com"
```

> **Note**
>
> The SSL certificate is used to secure communication between the server and devices. It is recommended that the certificate validity period be set to more than 365 days.

### Modify bundle.json.

Add a sub_component to the build field.

```json
"sub_component": [
    "//base/update/updateservice/server_sample:testserver",
    ...
],
```

### Create the Code Directory

Go to the update_updateservice directory and run the following commands to create the code directory.

```shell
mkdir server_sample                            // Create the server_sample directory for the sample server.
touch server_sample/BUILD.gn                   // Create the BUILD.gn build file.
mkdir server_sample/include                    // Create the include directory for the sample server header files.
touch server_sample/include/server_process.h   // Create the server_process.h header file.
mkdir server_sample/src                        // Create the src directory for the sample server C/C++ files.
touch server_sample/src/server_process.c       // Create the server_process.c file.
touch server_sample/src/main.cpp               // Create the main.cpp file.
```

### Write the BUILD.gn build file.

The BUILD.gn file compiles two ohos components in total: one is the ohos_shared_library library file libserver_process.z.so, and the other is the ohos_executable executable file testserver.

```gn
import("//build/ohos.gni")

ohos_shared_library("server_process") {
    sources = [
        "//base/update/updateservice/server_sample/src/server_process.c",
    ]

    include_dirs = [
        "//base/update/updateservice/server_sample/include",
        "//third_party/openssl/include",
    ]

    deps = [
        "//base/update/updater/services/log:libupdaterlog",
        "//third_party/bounds_checking_function:libsec_static",
        "//third_party/openssl:crypto_source",
        "//third_party/openssl:ssl_source",
        "//utils/native/base:utils",
    ]

    part_name = "update_service"
}

ohos_executable("testserver") {
    sources = [
        "//base/update/updateservice/server_sample/src/main.cpp",
    ]

    include_dirs = [
        "//base/update/updateservice/server_sample/include",
    ]

    deps = [
        "//base/update/updateservice/server_sample:server_process",
    ]

    part_name = "update_service"
}
```

### Write the header file server_process.h.

The file server_process.h declares the interfaces of the Sample Service.

```c++
#ifndef __SERVER_PROCESS_H__
#define __SERVER_PROCESS_H__

/*
 Init function: used to create the socket environment and preset some properties
 */
int Init();

/*
 SetParam function: the unified interface for setting all plugin parameters
 */
int SetParam(const char *key, const char *value);

/*
 GetParam function: the unified interface for getting all plugin parameters
 */
int GetParam(const char *key, char *value);

/*
 ReverseSetParamCallback function: callback
 */
int ReverseSetParamCallback(int(*setParam)(const char *key, const char *value));

/*
 Open function: the interface used to open the service
 */
int Open();

/*
 MainLoop function: called every 100 ms
 */
int MainLoop();

/*
 Close function: used to close the service and release resources
 */
int Close();

#endif // __SERVER_PROCESS_H__
```

### Write server_process.c and main.cpp.

The file server_process.c mainly declares the server's response message format respondContent. main.cpp can be written by referring to a common SSL server, noting the inclusion of relevant header files and loading the two certificates serverKey.pem and serverCert.cer.

```c
#include "server_process.h"

#include <netinet/in.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <arpa/inet.h>
#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>

#include "openssl/err.h"
#include "openssl/ssl.h"

#define SERVER_PEM "/data/sdcard/serverKey.pem"  // Use the absolute path.
#define SERVER_CER "/data/sdcard/serverCert.cer" // Use the absolute path.

#define LOG_PRINT(fmt, ...) printf("[ServerProcess][%s:%d] " fmt "\n", __func__, __LINE__, ##__VA_ARGS__)
#define DO_CHECK(cond, log, ...) \
if (!(cond)) {\
    LOG_PRINT(log);\
    __VA_ARGS__;\
    return -1;\
}

// Implement it by referring to the interfaces in server_process.h. Note the format of the content returned by the server.
respondContent = "{"
    "\"searchStatus\": 0,"
    "\"errMsg\": \"success\","
    "\"checkResults\": [{"
        "\"versionName\": \"sampleVersionName\","
        "\"versionCode\": \"sampleVersionCode\","
        "\"verifyInfo\": \"sampleVerifyInfoSha256Value\","
        "\"size\": 1234567,"
        "\"packageType\": 1,"
        "\"descriptPackageId\": \"abcdefg1234567ABCDEFG\","
    "}],"
    "\"descriptInfo\": [{"
        "\"descriptionType\": 0,"
        "\"content\": \"This package message is used for sampleContent\""
    "}]"
"}";
```

### Compilation Output Artifacts.

The compilation output directory will contain two new files: testserver and libserver_process.z.so.

### Creating an Update Package.

Create an update package by referring to the [update_packaging_tools repository](https://gitcode.com/openharmony/update_packaging_tools).

### Start the Package Search Server

It is recommended to create a directory with a pure English path on the development board, place testserver, libserver_process.z.so, serverCert.cer, and serverKey.pem in the same directory, enter that directory, and run the following startup command to start the package search server.

```shell
./testserver ./libserver_process.z.so &
```

## Debugging Instructions

After the sample server starts, you can debug and verify it in the following ways:

1. **Confirm that the server starts successfully**: After running the startup command, the server process runs in the background. You can check the process status by running the `ps -ef | grep testserver` command.

2. **Verify SSL communication**: Ensure that the paths of the serverKey.pem and serverCert.cer certificate files are correct. The certificate files should be placed in the /data/sdcard directory.

3. **Check port listening**: The default listening port of the sample server must be consistent with the search interface configuration on the device side. You can confirm the port listening status by running `netstat -an | grep <port number>`.

4. **View logs**: Server runtime logs can be viewed through logcat or serial port logs. Key interface calls print log information with the `[ServerProcess]` prefix.

> **Note**
>
> The sample server is intended only for development and debugging and is not recommended for direct use in production environments. A production upgrade server needs to be customized based on actual business requirements, including complete features such as permission verification, package management, and version control.