# Database Backup and Restore (C/C++)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @widecode; @htt1997-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

## When to Use

If an error occurs during the operation or storage, you can restore the database to the previous state and continue the operation.

If a database is tampered with, deleted, or powered off, the database may be unavailable due to data loss, data corruption, or dirty data. In this case, you can use the backup and restore capability to restore the database to the available state.

Currently, only RDB stores (C/C++) supports database backup and restore.

## How to Develop

A database backup can be used to quickly restore an RDB store in abnormal state.

1. Add the following library to **CMakeLists.txt**.

    ```txt
    libnative_rdb_ndk.z.so
    ```

2. Include header files.

    ```c
    #include "database/rdb/relational_store.h"
    ```

3. Call **OH_Rdb_Backup** to back up the database.

    ```c
    OH_Rdb_ConfigV2* config = OH_Rdb_CreateConfig();
    OH_Rdb_SetDatabaseDir(config, "/data/storage/el2/database");
    OH_Rdb_SetArea(config, RDB_SECURITY_AREA_EL2);
    OH_Rdb_SetStoreName(config, "RdbTest.db");
    OH_Rdb_SetSecurityLevel(config, OH_Rdb_SecurityLevel::S3);
    OH_Rdb_SetBundleName(config, "com.example.nativedemo");
    
    int errCode = 0;
    OH_Rdb_Store *store = OH_Rdb_CreateOrOpen(config, &errCode);
    
    // Back up a database.
    int result = OH_Rdb_Backup(store, "/data/storage/el2/database/RdbTest_bak.db");
    OH_Rdb_CloseStore(store);
    ```

4. Call **OH_Rdb_Restore** to restore the database.

    ```c
    OH_Rdb_ConfigV2* config2 = OH_Rdb_CreateConfig();
    OH_Rdb_SetDatabaseDir(config2, "/data/storage/el2/database");
    OH_Rdb_SetArea(config2, RDB_SECURITY_AREA_EL2);
    OH_Rdb_SetStoreName(config2, "RdbRestoreTest.db");
    OH_Rdb_SetSecurityLevel(config2, OH_Rdb_SecurityLevel::S3);
    OH_Rdb_SetBundleName(config2, "com.example.nativedemo");
    int errCode2 = 0;
    OH_Rdb_Store *store2 = OH_Rdb_CreateOrOpen(config2, &errCode2);
    
    // Restore the database.
    int result2 = OH_Rdb_Restore(store2, "/data/storage/el2/database/RdbTest_bak.db");
    OH_Rdb_CloseStore(store2);
    ```
