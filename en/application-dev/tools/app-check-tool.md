# App Check Tool
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @jsjzju-->
<!--Designer: @jsjzju-->
<!--Tester: @lixueqing513-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

The app check tool is used to analyze and detect application installation packages. Based on the parameter settings, it scans the HAP, HSP, or APP file in the specified path and generates detection reports, providing data support for you to optimize the package structure or locate problems. The tool provides the following functions:
- Scans for duplicate files.
- Scans for large files (files that exceed the specified size).
- Collects statistics on the size and proportion of each type of file.<br>

By default, the tool generates detection reports in JSON and HTML format.<br>
The **app_check_tool.jar** package of the tool is stored in the **toolchains** directory of the SDK.

![App check tool architecture](figures/app-check-tool-construct.png)

## Constraints
- The app check tool must run in Java 8 or later.
- The directory where the app check tool is running must have the read and write permissions.

## Scanning for Duplicate Files

**Command example**

```
java -jar app_check_tool.jar --input ./test.app --out-path ./test --stat-duplicate true
```

**Table 1 Parameters of the command for scanning duplicate files**

| Parameter            | Mandatory| Description                                                              |
| ---------------- | ---------- | ------------------------------------------------------------------ |
| --input          | Yes        | Path of the HAP, HSP, or APP file.                               |
| --out-path       | Yes        | Path of the detection reports.                                          |
| --stat-duplicate | No        | Whether to scan for duplicate files. The default value is **false**.<br>**true**: Scanning is enabled.<br>**false**: Scanning is disabled. |

**Detection report in JSON format**

```
[{
    "taskType":1,
    "taskDesc":"find the duplicated files",
    "param":"--stat-duplicate",
    "startTime":"2023-11-17 14:48:01:265",
    "stopTime":"2023-11-17 14:48:01:434",
	"result":[{
        "md5":"975c41f5727b416b1ffefa5bb0f073b2",
        "size":1108880,
        "files":[
            "/application-entry-default.hap/libs/armeabi-v7a/example.so",
            "/entry-default.hap/libs/armeabi-v7a/example.so"
        ]
    }]
}]
```

**Table 2 Field information of scanned duplicate files**

| Field     | Type  | Description                       |
| --------- | ------ | --------------------------- |
| taskType  | int    | Type of the task. The value **1** means a task for scanning for duplicate files.|
| taskDesc  | String | Description of the task.           |
| param     | String | Parameter passed in by the scanning program.         |
| startTime | String | Start time of the task.             |
| stopTime  | String | End time of the task.             |
| result    | Struct | Fields in the duplicate file statistics result. For details, see Table 3.      |

**Table 3 Fields in the duplicate file statistics result**

| Field | Type           | Description                      |
| ----- | --------------- | -------------------------- |
| md5   | String          | MD5 value of the duplicate files.         |
| size  | int             | Size of the duplicate files, in bytes.|
| files | Vector\<String> | Paths of the duplicate files.    |

## Scanning for Large Files

**Command example**

```
java -jar app_check_tool.jar --input ./test.app --out-path ./test --stat-file-size 4
```

**The command parameters for scanning files that exceed the specified size are described as follows:**

| Parameter            | Mandatory| Description                                                       |
| ---------------- | ---------- | ----------------------------------------------------------- |
| --input          | Yes        | Path of the HAP, HSP, or APP file.                        |
| --out-path       | Yes        | Path of the detection reports.                                   |
| --stat-file-size | No        | Scans files that exceed the specified size, in KB.<br>The value ranges from 0 to 4294967295, in KB.|

**Detection report in JSON format**

```
[{
    "taskType":2,
    "taskDesc":"find files whose size exceed the limit size",
    "param":"--stat-file-size 4",
    "startTime":"2023-11-17 14:48:01:458",
    "stopTime":"2023-11-17 14:48:01:491",
    "result":[{
            "file":"/application-entry-default.hap/libs/x86_64/example.so",
            "size":1292840
    }]
}]
```


**Fields of the output**

| Field     | Type  | Description                               |
| --------- | ------ | ----------------------------------- |
| taskType  | int    | Type of the task. The value **2** means a task for scanning for large files.|
| taskDesc  | String | Description of the task.                   |
| param     | String | Parameter passed in by the scanning program.                 |
| startTime | String | Start time of the task.                     |
| stopTime  | String | End time of the task.                     |
| result    | Struct | Fields in the statistical result of the file whose size exceeds the specified size. For details, see Table 6.             |

**Column information about the statistical result of the file whose size exceeds the specified size**

| Field| Type  | Description                                |
| ---- | ------ | ------------------------------------ |
| file | String | Path of a file.            |
| size | int    | Size of the file, in bytes.|

## Collecting Statistics on the Size and Proportion by File Type

**Command example**

```
java -jar app_check_tool.jar --input ./test.app --out-path ./test --stat-suffix true
```

**The parameters of the command for collecting statistics on the proportion of each type of file size are as follows**

| Parameter         | Mandatory| Description                                                                     |
| ------------- | ---------- | ------------------------------------------------------------------------- |
| --input       | Yes        | Path of the HAP, HSP, or APP file.                                      |
| --out-path    | Yes        | Path of the detection reports.                                                 |
| --stat-suffix | No        | Whether to collect statistics on the size and proportion of each type of file. The default value is **false**.<br>**true**: Scanning is enabled.<br>**false**: Scanning is disabled.|

**Detection report in JSON format**

```
[{
    "taskType":3,
    "taskDesc":"show files group by file type[.suffix]",
    "param":"--stat-suffix",
    "startTime":"2023-11-17 14:48:01:497",
    "stopTime":"2023-11-17 14:48:01:537",
    "pathList":[
        "test.app/application-entry-default.hap",
        "test.app/entry-default.hap"
    ],
    "result":[{
        "suffix":"so",
        "totalSize":1292840,
        "files":[{
            "compress":"false",
            "file":"/application-entry-default.hap/libs/x86_64/example.so",
            "size":1292840
        }]
    },
    {
        "suffix":"abc",
        "totalSize":84852,
        "files":[{
            "file":"/application-entry-default.hap/ets/modules.abc",
            "size":76304
        },
        {
            "file":"/entry-default.hap/ets/modules.abc",
            "size":8548
        }]
    }]
}]
```



**Fields of the output**

| Field     | Type           | Description                                                                                  |
| --------- | --------------- | -------------------------------------------------------------------------------------- |
| taskType  | int             | Type of the task. The value **3** means a task for collecting statistics on the size and proportion of each type of file.                                                 |
| taskDesc  | String          | Description of the task.                                                                      |
| param     | String          | Parameter passed in by the scanning program.                                                                    |
| startTime | String          | Start time of the task.                                                                        |
| stopTime  | String          | End time of the task.                                                                        |
| pathList  | Vector\<String> | Paths of multiple HAP and HSP files.                                                                 |
| result    | Struct          | Fields in the statistical result of the proportion of each type of file size. For details, see Table 9.                                   |

**Column information about the proportion of each type of file size**

| Field     | Type  | Description                                      |
| --------- | ------ | ------------------------------------------ |
| suffix    | String | File name extension.                        |
| totalSize | int    | Total size of scanned files of the same type, in bytes.|
| files     | Struct  | Path and size field information of files of the same type. For details, see Table 10.                    |

**Column information about the path and size of files of the same type**
| Field    | Type  | Description                                                               |
| -------- | ------ | ------------------------------------------------------------------- |
| file     | String | Path of a file.                                                         |
| size     | int    | with the same file name extension, in bytes.                                                       |
| compress | bool   | Whether the file is a compressed file (displayed only for SO files).<br>**true**: The file is compressed.<br>**false**: The file is not compressed.|
