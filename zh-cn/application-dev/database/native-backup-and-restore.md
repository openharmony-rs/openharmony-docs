# 数据库备份与恢复 (C/C++)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @widecode; @htt1997-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

## 场景介绍

如果操作或存储的过程中出现问题，开发者可以使用恢复功能，将数据库恢复到之前的状态，重新对数据库进行操作。

在数据库被篡改、删除、或者设备断电场景下，数据库可能会因为数据丢失、数据损坏、脏数据等而不可用，可以通过数据库的备份恢复能力将数据库恢复至可用状态。

当前仅支持使用关系型数据库（C/C++）进行备份与恢复。

## 开发步骤

数据库操作或者存储过程中，有可能会因为各种原因发生非预期的数据库异常的情况，可以根据需要使用关系型数据库的备份能力，以便在数据库异常时，可靠高效地恢复数据保证业务数据正常使用。

1. CMakeLists.txt中添加以下lib。

    ```txt
    libnative_rdb_ndk.z.so
    ```

2. 导入头文件。

    ```c
    #include "database/rdb/relational_store.h"
    ```

3. 调用OH_Rdb_Backup接口实现数据库备份。

    ```c
    OH_Rdb_ConfigV2* config = OH_Rdb_CreateConfig();
    OH_Rdb_SetDatabaseDir(config, "/data/storage/el2/database");
    OH_Rdb_SetArea(config, RDB_SECURITY_AREA_EL2);
    OH_Rdb_SetStoreName(config, "RdbTest.db");
    OH_Rdb_SetSecurityLevel(config, OH_Rdb_SecurityLevel::S3);
    OH_Rdb_SetBundleName(config, "com.example.nativedemo");
    
    int errCode = 0;
    OH_Rdb_Store *store = OH_Rdb_CreateOrOpen(config, &errCode);
    
    // 备份数据库
    int result = OH_Rdb_Backup(store, "/data/storage/el2/database/RdbTest_bak.db");
    OH_Rdb_CloseStore(store);
    ```

4. 调用OH_Rdb_Restore接口实现数据库恢复。

    ```c
    OH_Rdb_ConfigV2* config2 = OH_Rdb_CreateConfig();
    OH_Rdb_SetDatabaseDir(config2, "/data/storage/el2/database");
    OH_Rdb_SetArea(config2, RDB_SECURITY_AREA_EL2);
    OH_Rdb_SetStoreName(config2, "RdbRestoreTest.db");
    OH_Rdb_SetSecurityLevel(config2, OH_Rdb_SecurityLevel::S3);
    OH_Rdb_SetBundleName(config2, "com.example.nativedemo");
    int errCode2 = 0;
    OH_Rdb_Store *store2 = OH_Rdb_CreateOrOpen(config2, &errCode2);
    
    // 恢复数据库
    int result2 = OH_Rdb_Restore(store2, "/data/storage/el2/database/RdbTest_bak.db");
    OH_Rdb_CloseStore(store2);
    ```

5. 调用OH_Rdb_RegisterCorruptedHandler接口注册数据库异常处理。

    ```c
    // 数据库异常后处理的回调函数
    void CorruptedHandler(void *context, OH_Rdb_ConfigV2 *config, OH_Rdb_Store *store)
    {
        const char* restorePath = "/data/storage/el2/database/RdbTest_bak.db";
        if (store == nullptr) {
            OH_Rdb_DeleteStoreV2(config);
        } else {
            // 用备份的数据库恢复数据库
            OH_Rdb_Restore(store, restorePath);
        }
    }
    OH_Rdb_ConfigV2* config3 = OH_Rdb_CreateConfig();
    OH_Rdb_SetDatabaseDir(config3, "/data/storage/el2/database");
    OH_Rdb_SetArea(config3, RDB_SECURITY_AREA_EL2);
    OH_Rdb_SetStoreName(config3, "RdbRestoreTest.db");
    OH_Rdb_SetSecurityLevel(config3, OH_Rdb_SecurityLevel::S3);
    OH_Rdb_SetBundleName(config3, "com.example.nativedemo");
    int errCode3 = 0;
    OH_Rdb_Store *store3 = OH_Rdb_CreateOrOpen(config3, &errCode3);

    // 备份数据库
    int result = OH_Rdb_Backup(store3, "/data/storage/el2/database/RdbTest_bak.db");

    void *context = nullptr;
    Rdb_CorruptedHandler handler = CorruptedHandler;
    // 注册数据库异常处理
    OH_Rdb_RegisterCorruptedHandler(config3, context, handler);
    ```

6. 调用OH_Rdb_UnregisterCorruptedHandler接口取消注册数据库异常处理。

    ```c
    // 数据库异常后处理的回调函数
    void CorruptedHandler(void *context, OH_Rdb_ConfigV2 *config, OH_Rdb_Store *store)
    {
        const char* restorePath = "/data/storage/el2/database/RdbTest_bak.db";
        if (store == nullptr) {
            OH_Rdb_DeleteStoreV2(config);
        } else {
            // 用备份的数据库恢复数据库
            OH_Rdb_Restore(store, restorePath);
        }
    }
    OH_Rdb_ConfigV2* config4 = OH_Rdb_CreateConfig();
    OH_Rdb_SetDatabaseDir(config4, "/data/storage/el2/database");
    OH_Rdb_SetArea(config4, RDB_SECURITY_AREA_EL2);
    OH_Rdb_SetStoreName(config4, "RdbRestoreTest.db");
    OH_Rdb_SetSecurityLevel(config4, OH_Rdb_SecurityLevel::S3);
    OH_Rdb_SetBundleName(config4, "com.example.nativedemo");
    int errCode4 = 0;
    OH_Rdb_Store *store4 = OH_Rdb_CreateOrOpen(config4, &errCode4);

    void *context = nullptr;
    Rdb_CorruptedHandler handler = CorruptedHandler;
    // 取消注册数据库异常处理
    OH_Rdb_UnregisterCorruptedHandler(config4, context, handler);
    ```