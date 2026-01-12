# 关系型数据库单版本模式跨设备数据同步 (ArkTS)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @widecode; @htt1997-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

## 场景介绍

[场景介绍](data-sync-of-rdb-store.md#场景介绍)。

## 基本概念

[基本概念](data-sync-of-rdb-store.md#基本概念)。

## 运作机制

[运作机制](data-sync-of-rdb-store.md#运作机制)。

### 数据跨设备同步机制

[数据跨设备同步机制](data-sync-of-rdb-store.md#数据跨设备同步机制)。

### 数据变化通知机制

[数据变化通知机制](data-sync-of-rdb-store.md#数据变化通知机制)。

### 单版本表模式数据同步存储机制

从API version 23开始，支持单版本表模式进行数据存储。

[单版本表模式](data-sync-of-rdb-store.md#单版本表模式)。

## 约束限制

- 每个应用程序最多支持同时打开16个关系型分布式数据库。

- 单个数据库最多支持注册8个订阅数据变化的回调。

- 不支持将含有复合键的表设置为分布式表。

- 单版本表模式使用需要配置schema文件，用以指定同步列以及指定解冲突列，schema约束和格式见：[schema约束](#schema约束)，[schema格式](#schema格式)。

- 同一张表不能同时配置为端端分布式表和端云分布式表，且不支持切换。

- 同一数据库下所有端端分布式表必须为一种数据同步存储机制，且不支持切换。

## 接口说明

[接口说明](data-sync-of-rdb-store.md#接口说明)

## 开发步骤

[开发步骤](data-sync-of-rdb-store.md#开发步骤)。

## schema格式

### schema示例

可参考示例：[schema示例](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/DataSyncAndPersistence/entry/src/main/resources/rawfile/arkdata/schema/sync_schema.json)。

### schema文件路径

schema文件路径必须为：../entry/src/main/resources/rawfile/arkdata/schema/sync_schema.json，文件名必须为sync_schema.json，文件路径不支持自定义，否则将读取不到。单版本表模式跨端同步，若读取不到schema文件，设置分布表将会失败。

### schema层级目录：

schema文件为json格式，dbSchema下可以配置多个数据库。

- dbSchema：schema名称，array[db]，必填字段。
    - version：当前schema版本，int，必填字段。
    - bundleName：应用身份信息，string，必填字段。
    - dbName：数据库名，string，必填字段。eg. 如示例中数据库名为"RdbTest.db"，此处配置为："RdbTest"。
    - tables：数据库中表信息，array[table]。
        - tableName：表名，string，必填字段。
        - deviceSyncFields：指定端端同步列，array[string]，其中字段必须在fields中，且必须在数据库表中，否则不会同步；若使用单版本表模式跨端同步，该字段为必填字段，否则设置分布式表失败。
        - fields：数据库表字段详细信息，array[field]。
            - columnName：字段名，string，必填字段。
            - type：字段类型，string，必填字段，可选参数范围为：["Text", "Integer", "Long", "Float", "Double", "Blob" ]。
            - primaryKey：在使用单版本表模式跨端同步时，该字段表示是否为指定解冲突列，与表中是否为主键无关，bool。若是自增表，该字段为必填字段。其中：true表示为解冲突列，默认为false。
            - autoIncrement：是否自增属性，必须与表结构中对应，bool。RDB近端同步不支持同步自增主键。其中：true表示自增主键，默认为false。
            - notNull：是否非空，bool，非必填字段。其中：true表示非空字段，默认为false。        

## schema约束

- 不支持解冲突列变化。
  | 旧版本 |新版本 |
  |---|--|
  |``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["NAME", "AGE", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": true,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```
    |
    ``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["NAME", "AGE", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": true,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```
      |
  - 错误示例：schema版本升级后，指定解冲突列由"NAME"改为"AGE"。
    - 旧版本schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["NAME", "AGE", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": true,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```
    - 升级版本schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 1,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["NAME", "AGE", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": false,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": true,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```

- 解冲突列只能有一个。
  - 错误示例：schema中指定字段"NAME"和"AGE"两个解冲突列。
    - schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["NAME", "AGE", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": true,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": true,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```

- 同步列必须存在表中。
  - 错误示例：schema指定字段"NAMe"，与表中字段"NAME"大小写不一致。
    - 建表语句：'CREATE TABLE IF NOT EXISTS EMPLOYEE (ID INTEGER PRIMARY KEY AUTOINCREMENT, NAME TEXT NOT NULL, AGE INTEGER, SALARY REAL, CODES BLOB)'
    - schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["NAMe", "AGE", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": true,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```

- 同步列变化时，存量数据会重新同步。
    - 若schema中有新增指定同步列，已有指定同步列以及新增指定列数据会重新触发同步。

- schema有变化时，version需要增加。
  - 错误示例：schema中新增同步字段"AGE"，但是version未增加。
    - 旧版本schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["NAME", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": true,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```
    - 升级版本schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["NAME", "AGE", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": true,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```

- 单版本表模式下，表中所有UNIQUE列必须同步。
  - 错误示例："AGE"为UNIQUE列，但是未指定该字段同步
    - 建表语句：'CREATE TABLE IF NOT EXISTS EMPLOYEE (ID INTEGER PRIMARY KEY AUTOINCREMENT, NAME TEXT NOT NULL UNIQUE, AGE INTEGER UNIQUE, SALARY REAL, CODES BLOB)'。
    - schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["NAME", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": true,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```

- 自增表下，不支持指定非主键列解冲突又同步主键。
  - 错误示例：自增表下，指定"NAME"为解冲突列，但是又同步字段"ID"。
    - 建表语句：'CREATE TABLE IF NOT EXISTS EMPLOYEE (ID INTEGER PRIMARY KEY AUTOINCREMENT, NAME TEXT NOT NULL UNIQUE, AGE INTEGER, SALARY REAL, CODES BLOB)'。
    - schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["ID", "NAME", "AGE", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": true,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```

- schema版本升级时，指定同步列只能新增不能减少。
  - 错误示例：schema版本由0升级为1，指定同步列"SALARY"被删除。
    - 旧版本schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["NAME", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": true,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```
    - 升级版本schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 1,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["NAME", "AGE", "CODES"],
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": true,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```

- 同步列不能为空，deviceSyncFields长度至少为1，若schema中未配置字段deviceSyncFields，默认为空。
  - 错误示例：schema中没有配置deviceSyncFields，设置单版本模式分布式表失败。
    - schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": true,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```

- 表中not null字段必须有默认值，否则要指定同步。
  - 错误示例：字段"AGE"为not null值，没有默认值，同步schema中没有指定"AGE"同步。
    - 建表语句：'CREATE TABLE IF NOT EXISTS EMPLOYEE (ID INTEGER PRIMARY KEY AUTOINCREMENT, NAME TEXT NOT NULL UNIQUE, AGE INTEGER NOT NULL, SALARY REAL, CODES BLOB)'。
    - schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["NAME", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": true,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```

- 无主键表不支持指定列同步，不支持配置单版本表模式。
  - 错误示例："EMPLOYEE"是无主键表，设置单版本模式分布式表时会失败。
    - 建表语句：'CREATE TABLE IF NOT EXISTS EMPLOYEE (NAME TEXT NOT NULL UNIQUE, AGE INTEGER, SALARY REAL, CODES BLOB)'。
    - schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["NAME", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": true,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```

- 主键为非自增，主键必须同步，且解冲突列必须为主键。
  - 错误示例："NAME"为非自增主键，但是指定"AGE"为解冲突列。
    - 建表语句：'CREATE TABLE IF NOT EXISTS EMPLOYEE (NAME TEXT NOT NULL PRIMARY KEY, AGE INTEGER NOT NULL UNIQUE, SALARY REAL, CODES BLOB)'。
    - schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["AGE", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": false,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": true,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```

- 多设备协同表模式下不支持设置schema，默认不读取schema文件。

- 配置解冲突列必须为UNIQUE属性，且为类似uuid等全局唯一字段。
  - 错误示例：指定解冲突列"NAME"没有UNIQUE属性。
    - 建表语句：'CREATE TABLE IF NOT EXISTS EMPLOYEE (ID INTEGER PRIMARY KEY AUTOINCREMENT, NAME TEXT NOT NULL, AGE INTEGER, SALARY REAL, CODES BLOB)'。
    - schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["NAME", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": true,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```

- deviceSyncFields中字段必须在fields中，否则该字段将不会同步。
  - 错误示例：字段"AGE"未出现在fields中，该字段将不会同步。
    - 建表语句：'CREATE TABLE IF NOT EXISTS EMPLOYEE (ID INTEGER PRIMARY KEY AUTOINCREMENT, NAME TEXT NOT NULL UNIQUE, AGE INTEGER, SALARY REAL, CODES BLOB)'。
    - schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["NAME", "AGE", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": true,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```

- 必须同步uuid等全局唯一的主键，自增主键不允许同步，若主键为自增，必须配置一个非主键列解冲突。
  - 错误示例：schema中指定了"ID"同步，该字段为自增主键。
    - 建表语句：'CREATE TABLE IF NOT EXISTS EMPLOYEE (ID INTEGER PRIMARY KEY AUTOINCREMENT, NAME TEXT NOT NULL UNIQUE, AGE INTEGER, SALARY REAL, CODES BLOB)'。
    - schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["ID", "NAME", "AGE", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": true,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": false,
                    "notNull": true,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```

- 指定解冲突列中的值不能出现null值。若指定解冲突列存量数据有null值，设置分布式表会失败；若指定解冲突列增量数据为null值，写入会失败。
  - 错误示例：若先执行写入语句，执行设置分布式表语句会失败；若先执行设置分布式表语句，执行写入语句会失败。
    - 建表语句：'CREATE TABLE IF NOT EXISTS EMPLOYEE (ID INTEGER PRIMARY KEY AUTOINCREMENT, NAME TEXT UNIQUE, AGE INTEGER, SALARY REAL, CODES BLOB)'。
    - 写入语句：
      ``` TypeScript
      let valueBucket: ValueBucket = {};
      valueBucket["NAME"] = null;
      valueBucket["AGE"] = 25;
      valueBucket["SALARY"] = 23456.7;
      let value = new Uint8Array([1, 2, 3, 4, 5]);
      valueBucket["CODES"] = value;
      await rdbstore.insert("EMPLOYEE", valueBucket);
      ```
    - 设置分布式表语句：
      ``` TypeScript
      const DISTRIBUTED_CONFIG: relationalStore.DistributedConfig = {
        autoSync: false,
        asyncDownloadAsset: false,
        enableCloud: false,
        tableType: relationalStore.DistributedTableType.SINGLE_VERSION
      }
      await store.setDistributedTables(['EMPLOYEE', 'EMPLOYEE2'], relationalStore.DistributedType.DISTRIBUTED_DEVICE, DISTRIBUTED_CONFIG);
      ```
    - schema：
      ``` Json
      {
        "dbSchema": [
          {
            "version": 0,
            "bundleName": "com.example.rdbDataSync",
            "dbName": "RdbTest",
            "tables": [
              {
                "tableName": "EMPLOYEE",
                "deviceSyncFields": ["NAME", "AGE", "SALARY", "CODES"],
                "fields": [
                  {
                    "columnName": "ID",
                    "type": "Integer",
                    "primaryKey": true,
                    "notNull": false,
                    "autoIncrement": true
                  },
                  {
                    "columnName": "NAME",
                    "type": "Text",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "AGE",
                    "type": "Integer",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "SALARY",
                    "type": "Float",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  },
                  {
                    "columnName": "CODES",
                    "type": "Blob",
                    "primaryKey": false,
                    "notNull": false,
                    "autoIncrement": false
                  }
                ]
              }
            ]
          }
        ]
      }
      ```
