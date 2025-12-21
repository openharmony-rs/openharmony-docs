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

[单版本表模式](data-sync-of-rdb-store.md#数据同步存储机制#单版本表模式)。

## 约束限制

- 每个应用程序最多支持同时打开16个关系型分布式数据库。

- 单个数据库最多支持注册8个订阅数据变化的回调。

- 不支持将含有复合键的表设置为分布式表。

- 单版本表模式使用需要配置schema文件，用以指定同步列以及指定解冲突列，schema约束和格式见：[schema约束](#schema约束)，[schema格式](#schema格式)。。

- 同一张表不能同时配置为端端分布式表和端云分布式表，且不支持切换。

## 接口说明

以下是关系型设备协同分布式数据库跨设备数据同步功能的相关接口，大部分为异步接口。异步接口均有callback和Promise两种返回形式，下表均以callback形式为例，更多接口及使用方式请见[关系型数据库](../reference/apis-arkdata/arkts-apis-data-relationalStore.md)。

| 接口名称 | 描述 | 
| -------- | -------- |
| setDistributedTables(tables: Array&lt;string&gt;, type: DistributedType, config: DistributedConfig, callback: AsyncCallback&lt;void&gt;): void | 设置分布式同步表。 | 
| sync(mode: SyncMode, predicates: RdbPredicates, callback: AsyncCallback&lt;Array&lt;[string, number]&gt;&gt;): void | 分布式数据同步。 | 
| on(event: 'dataChange', type: SubscribeType, observer: Callback&lt;Array&lt;string&gt;&gt;): void | 订阅分布式数据变化。 | 
| off(event:'dataChange', type: SubscribeType, observer: Callback&lt;Array&lt;string&gt;&gt;): void | 取消订阅分布式数据变化。 |
| remoteQuery(device: string, table: string, predicates: RdbPredicates, columns: Array&lt;string&gt; , callback: AsyncCallback&lt;ResultSet&gt;): void | 根据指定条件查询远程设备数据库中的数据。 |

## 开发步骤

> **说明：**
>
> 数据只允许向数据安全标签不高于对端设备安全等级的设备同步数据，具体规则可见[跨设备同步访问控制机制](access-control-by-device-and-data-level.md#跨设备同步访问控制机制)。

1. 导入模块。
   <!--@[sync_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/DataSyncAndPersistence/entry/src/main/ets/pages/datasync/RdbDataSync.ets)-->

2. 请求权限。
   1. 需要申请ohos.permission.DISTRIBUTED_DATASYNC权限，配置方式请参见[声明权限](../security/AccessToken/declare-permissions.md)。
   2. 同时需要在应用首次启动时弹窗向用户申请授权，使用方式请参见[向用户申请授权](../security/AccessToken/request-user-authorization.md)。

3. 创建关系型数据库，创建数据表，并将需要进行跨设备同步的数据表设置为分布式表，单版本表模式。
   需要将[DistributedConfig](../reference/apis-arkdata/arkts-apis-data-relationalStore-i.md#distributedconfig10)中[DistributedTableType](../reference/apis-arkdata/arkts-apis-data-relationalStore-e.md#DistributedTableType)配置为SINGLE_VERSION。
   <!--@[setSingleDistributedTables](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/DataSyncAndPersistence/entry/src/main/ets/pages/datasync/RdbDataSync.ets)--> 

4. 订阅组网内其他设备的数据变化消息。
   1. 调用[on('dataChange')](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#ondatachange)接口监听其他设备的数据变化，当数据变化同步至当前设备时，将执行订阅的回调方法，入参为数据发生变化的设备ID列表。
   2. 通过设备ID获取与设备对应的分布式表表名，查询对应设备分布式表中的数据。
   <!--@[on_data_change](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/DataSyncAndPersistence/entry/src/main/ets/pages/datasync/RdbDataSync.ets)-->

5. 同步当前设备数据变化至组网内其他设备。
   1. 当前设备分布式表中的数据发生变化后，调用RdbStore的[sync](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#sync-1)接口传入[SYNC_MODE_PUSH](../reference/apis-arkdata/arkts-apis-data-relationalStore-e.md#syncmode)参数推送数据变化至其他设备。
   2. 通过谓词的[inDevices](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbPredicates.md#indevices)方法指定推送的目标设备。
   <!--@[data_sync_push](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/DataSyncAndPersistence/entry/src/main/ets/pages/datasync/RdbDataSync.ets)-->

6. 拉取组网内其他设备的数据变化。
   1. 当前设备可调用RdbStore的[sync](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#sync-1)接口传入[SYNC_MODE_PULL](../reference/apis-arkdata/arkts-apis-data-relationalStore-e.md#syncmode)参数拉取组网内其他设备的数据变化。
   2. 通过谓词的[inDevices](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbPredicates.md#indevices)方法指定拉取的目标设备。
   <!--@[data_sync_pull](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/DataSyncAndPersistence/entry/src/main/ets/pages/datasync/RdbDataSync.ets)-->

7. 当数据未完成同步，或未触发数据同步时，可使用RdbStore的[remoteQuery](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#remotequery-1)方法查询组网内指定设备上分布式表中的数据。
   <!--@[data_remote_query](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/DataSyncAndPersistence/entry/src/main/ets/pages/datasync/RdbDataSync.ets)-->

## schema格式

### shcema示例

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
        - cloudType：数据库表类型，array[string]，可选参数[ "Local", "Cloud DB", "Device DB"]，大小写不可错，必填字段。eg.如示例中配置为["Local", "Device DB"]。其中："Local"表示本地   表，"Device DB"表示端端表，"Cloud DB"表示端云表。
        - tableName：表名，string，必填字段。
        - deviceSyncFields：指定端端同步列，array[string]，其中字段必须在fields中，且必须在数据库表中，否则不会同步；若使用单版本表模式跨端同步，该字段为必填字段，否则设置分布式表失败。
        - fields：数据库表字段详细信息，array[field]。
            - columnName：字段名，string>，必填字段。
            - type：字段类型，string，必填字段。
            - primaryKey：在使用单版本表模式跨端同步时，该字段表示是否为指定解冲突列，与表中是否为主键无关，bool。若是自增表，该字段为必填字段。其中：true表示为解冲突列，默认为false。
            - autoIncrement：是否自增属性，必须与表结构中对应，bool。RDB近端同步不支持同步自增主键。其中：true表示自增主键，默认为false。
            - notNull：是否非空，bool，非必填字段。其中：true表示非空字段，默认为false。

## schema约束

- 不持支解冲突列变化。
  - 错误示例：
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
                "cloudType": ["Local", "Device DB"],
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
                "cloudType": ["Local", "Device DB"],
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
  - 错误示例;
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
                "cloudType": ["Local", "Device DB"],
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
  - 错误示例：大小写也必须保持一致。
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
                "cloudType": ["Local", "Device DB"],
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
    - 若schema中有新增指定同步列，已有指定同步列以及新增指定列数据会重新出发同步。

- schema有变化时，version需要增加。
  - 错误示例：
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
                "cloudType": ["Local", "Device DB"],
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
                "cloudType": ["Local", "Device DB"],
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

- 单版本表模式下，表中所有unique列必须同步。
  - 错误示例：
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
                "cloudType": ["Local", "Device DB"],
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
  - 错误示例：
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
                "cloudType": ["Local", "Device DB"],
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
  - 错误示例：
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
                "cloudType": ["Local", "Device DB"],
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
                "cloudType": ["Local", "Device DB"],
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

- 同步列不能为空，deviceSyncFields长度至少为1。
  - 错误示例：
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
                "cloudType": ["Local", "Device DB"],
                "tableName": "EMPLOYEE",
                "deviceSyncFields": [],
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
  - 错误示例：
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
                "cloudType": ["Local", "Device DB"],
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
  - 错误示例：
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
                "cloudType": ["Local", "Device DB"],
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
  - 错误示例：
    - 建表语句：'CREATE TABLE IF NOT EXISTS EMPLOYEE (NAME TEXT NOT NULL PRIMARY KEY, AGE INTEGER UNIQUE, SALARY REAL, CODES BLOB)'。
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
                "cloudType": ["Local", "Device DB"],
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

- 配置解冲突列必须为unique属性，且为类似uuid等全局唯一字段。
  - 错误示例：
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
                "cloudType": ["Local", "Device DB"],
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
                "cloudType": ["Local", "Device DB"],
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
  - 错误示例：
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
                "cloudType": ["Local", "Device DB"],
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
