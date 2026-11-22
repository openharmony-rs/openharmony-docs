# Persisting RDB Store Data (C/C++)

<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=3fdb5d59ccfc0067d0c7ca669f16002bdef865d2 translatedAt=2026-11-03T04:30:46.252Z pushedAt=2026-11-03T04:30:46.252Z nl=2 -->

## When to Use

The **RelationalStore** module provides a complete mechanism for local database management. You can use the APIs to add, delete, modify, and query data, and execute SQL statements in complex scenarios.

## Basic Concepts

- **Predicates**: a representation of the property or feature of a data entity, or the relationship between data entities, used to define operation conditions.

- **ResultSet**: a set of query results, which allows access to the required data in flexible modes.

## Constraints

- By default, the Write Ahead Log (WAL) and the **FULL** flushing mode are used.

- A maximum of four connection pools are used for read operations.

- To ensure data accuracy, only one write operation is allowed at a time.

- Once an application is uninstalled, related database files and temporary files are automatically deleted from the device.

## How to Develop

For details about the APIs, see [RDB](../reference/apis-arkdata/capi-rdb.md).

**Adding the Dynamic Link Library**

Add the following libraries to **CMakeLists.txt**:

```txt
libnative_rdb_ndk.z.so, libhilog_ndk.z.so
```

**Including Header Files**

<!--@[rdb_include](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)--> 

``` C++
#include <cstdlib>
#include <database/data/data_asset.h>
#include <database/rdb/oh_cursor.h>
#include <database/rdb/oh_predicates.h>
#include <database/rdb/oh_value_object.h>
#include <database/rdb/oh_values_bucket.h>
#include <database/rdb/relational_store.h>
#include <database/rdb/relational_store_error_code.h>
#include <hilog/log.h>
```

1. Obtain an **OH_Rdb_Store** instance and create a database file. <br>The **dataBaseDir** variable specifies the application sandbox path. In the stage model, you are advised to use the database directory. For details, see the **databaseDir** attribute of [Context](../reference/apis-ability-kit/js-apis-inner-application-context.md). The FA model does not provide any API for obtaining the database sandbox path. Use the application directory instead. For details, see **getFilesDir** of [Context](../reference/apis-ability-kit/js-apis-inner-app-context.md). <br>**area** indicates the security level of the directory for database files. For details, see [contextConstant](../reference/apis-ability-kit/js-apis-app-ability-contextConstant.md). During development, you need to implement the conversion from **AreaMode** to **Rdb_SecurityArea**. <br>Example:

    <!--@[rdb_OH_Rdb_CreateOrOpen](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    // Create an OH_Rdb_ConfigV2 object.
    OH_Rdb_ConfigV2 *config = OH_Rdb_CreateConfig();
    // The path is the application sandbox path.
    // The database file will be created in the sandbox path: /data/storage/el3/database/rdb/RdbTest.db.
    OH_Rdb_SetDatabaseDir(config, "/data/storage/el3/database");
    // Secure path where database files are stored, which corresponds to the el path in the databaseDir parameter.
    OH_Rdb_SetArea(config, RDB_SECURITY_AREA_EL3);
    // Database file name.
    OH_Rdb_SetStoreName(config, "RdbTest.db");
    // Application bundle name.
    OH_Rdb_SetBundleName(config, "com.samples.rdbstore");
    // Module name. 
    OH_Rdb_SetModuleName(config, "entry");
    // Security level of the database file.
    OH_Rdb_SetSecurityLevel(config, OH_Rdb_SecurityLevel::S3);
    // Whether the database is encrypted.
    OH_Rdb_SetEncrypted(config, false);
    // ···

    int errCode = 0;
    // Obtain an OH_Rdb_Store instance.
    OH_Rdb_Store *store_ = OH_Rdb_CreateOrOpen(config, &errCode);
    if (store_ == NULL) {
        OH_LOG_ERROR(LOG_APP, "Create store failed, errCode: %{public}d", errCode);
        OH_Rdb_DestroyConfig(config);
        return;
    }
    if (errCode != OH_Rdb_ErrCode::RDB_OK) {
        OH_LOG_ERROR(LOG_APP, "Create attachStore failed, errCode: %{public}d", errCode);
        OH_Rdb_DestroyConfig(config);
        OH_Rdb_CloseStore(store_);
        return;
    }
    ```

    To set a custom database path, call [OH_Rdb_SetCustomDir()](../reference/apis-arkdata/capi-relational-store-h.md#oh_rdb_setcustomdir) where **// ...** appears in the preceding code. To open the database in read-only mode, call [OH_Rdb_SetReadOnly()](../reference/apis-arkdata/capi-relational-store-h.md#oh_rdb_setreadonly) at the same location. <br>Example:

    <!--@[rdb_OH_Rdb_SetCustomDir_and_SetReadOnly](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    // You can set a custom database path.
    // The database file will be created in the sandbox path /data/storage/el3/database/a/b/RdbTest.db.
    OH_Rdb_SetCustomDir(config, "../a/b");
    // Set the database to the read-only mode.
    OH_Rdb_SetReadOnly(config, true);
    ```

2. Call [OH_Rdb_Execute()](../reference/apis-arkdata/capi-relational-store-h.md#oh_rdb_execute) to create a table, and [OH_Rdb_Insert()](../reference/apis-arkdata/capi-relational-store-h.md#oh_rdb_insert) to insert data. <br>Example:

    <!--@[rdb_OH_Rdb_Execute_create_table](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    char createTableSql[] = "CREATE TABLE IF NOT EXISTS EMPLOYEE (ID INTEGER PRIMARY KEY AUTOINCREMENT, "
        "NAME TEXT NOT NULL, AGE INTEGER, SALARY REAL, CODES BLOB)";
    // Create a table.
    OH_Rdb_Execute(store_, createTableSql);
    ```

    <!--@[rdb_OH_Rdb_Insert_and_InsertWithConflictResolution](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    // Create a key-value (KV) pair instance.
    OH_VBucket *valueBucket = OH_Rdb_CreateValuesBucket();
    valueBucket->putText(valueBucket, "NAME", "Lisa");
    valueBucket->putInt64(valueBucket, "AGE", 18); // The value of AGE is 18
    valueBucket->putReal(valueBucket, "SALARY", 100.5); // The value of SALARY is 100.5
    uint8_t arr[] = {1, 2, 3, 4, 5};
    int len = sizeof(arr) / sizeof(arr[0]);
    valueBucket->putBlob(valueBucket, "CODES", arr, len);
    // Insert data.
    int rowId = OH_Rdb_Insert(store_, "EMPLOYEE", valueBucket);
    
    OH_VBucket *valueBucket2 = OH_Rdb_CreateValuesBucket();
    valueBucket2->putInt64(valueBucket2, "ID", 2); // The value of ID is 2
    valueBucket2->putText(valueBucket2, "NAME", "zhangsan");
    valueBucket2->putInt64(valueBucket2, "AGE", 24); // The value of AGE is 24
    valueBucket2->putReal(valueBucket2, "SALARY", 120.4); // The value of SALARY is 120.4
    int64_t rowId2 = -1;
    // Configure conflict resolutions when data is inserted.
    int result = OH_Rdb_InsertWithConflictResolution(store_, "EMPLOYEE", valueBucket2,
        Rdb_ConflictResolution::RDB_CONFLICT_REPLACE, &rowId2);
    // Destroy the KV pair instance.
    valueBucket->destroy(valueBucket);
    valueBucket2->destroy(valueBucket2);
    ```

   > **NOTE**
   >
   > **RelationalStore** does not provide explicit flush operations for data persistence. The **insert()** API stores data persistently.

3. Modify or delete data based on the conditions specified by **OH_Predicates**.

   Call [OH_Rdb_Update()](../reference/apis-arkdata/capi-relational-store-h.md#oh_rdb_update) to modify data, and [OH_Rdb_Delete()](../reference/apis-arkdata/capi-relational-store-h.md#oh_rdb_delete) to delete data. <br>Example:

    <!--@[rdb_OH_Rdb_Update_and_UpdateWithConflictResolution](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    // Create a valueBucket object to store the new data to be updated.
    OH_VBucket *valueBucket = OH_Rdb_CreateValuesBucket();
    valueBucket->putText(valueBucket, "NAME", "Rose");
    valueBucket->putInt64(valueBucket, "AGE", 22); // The value of AGE is 22
    valueBucket->putReal(valueBucket, "SALARY", 200.5); // The value of SALARY is 200.5
    uint8_t arr[] = {1, 2, 3, 4, 5};
    int len = sizeof(arr) / sizeof(arr[0]);
    valueBucket->putBlob(valueBucket, "CODES", arr, len);
    // Create a predicate object and specify the update condition: NAME is Lisa and SALARY is 100.5.
    OH_Predicates *predicates = OH_Rdb_CreatePredicates("EMPLOYEE");
    if (predicates == NULL) {
        OH_LOG_ERROR(LOG_APP, "CreatePredicates failed.");
        valueBucket->destroy(valueBucket);
        return;
    }
    OH_VObject *valueObject = OH_Rdb_CreateValueObject();
    const char *name = "Lisa";
    valueObject->putText(valueObject, name);
    predicates->equalTo(predicates, "NAME", valueObject)->andOperate(predicates);
    uint32_t count = 1;
    double salary = 100.5;
    valueObject->putDouble(valueObject, &salary, count);
    predicates->equalTo(predicates, "SALARY", valueObject);
    // Update the data that meets the condition to the value in valueBucket.
    int changeRows = OH_Rdb_Update(store_, valueBucket, predicates);
    OH_Predicates *predicates2 = OH_Rdb_CreatePredicates("EMPLOYEE");
    if (predicates2 == NULL) {
        OH_LOG_ERROR(LOG_APP, "CreatePredicates failed.");
        valueObject->destroy(valueObject);
        valueBucket->destroy(valueBucket);
        return;
    }
    OH_VObject *valueObject2 = OH_Rdb_CreateValueObject();
    valueObject2->putText(valueObject2, "Rose");
    predicates2->equalTo(predicates2, "NAME", valueObject2);
    valueBucket->putInt64(valueBucket, "ID", 1); // The value of ID is 1
    valueBucket->putText(valueBucket, "NAME", "zhangsan");
    int64_t changeRows2 = -1;
    
    // Configure conflict resolutions when data is updated.
    int result = OH_Rdb_UpdateWithConflictResolution(store_, valueBucket, predicates2,
        Rdb_ConflictResolution::RDB_CONFLICT_REPLACE, &changeRows2);
    valueObject->destroy(valueObject);
    valueObject2->destroy(valueObject2);
    valueBucket->destroy(valueBucket);
    predicates->destroy(predicates);
    predicates2->destroy(predicates2);
    ```

    <!--@[rdb_OH_Rdb_Delete](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->    

    ``` C++
    // Delete data.
    OH_Predicates *predicates = OH_Rdb_CreatePredicates("EMPLOYEE");
    if (predicates == NULL) {
        OH_LOG_ERROR(LOG_APP, "CreatePredicates failed.");
        return;
    }
    OH_VObject *valueObject = OH_Rdb_CreateValueObject();
    const char *name = "Lisa";
    valueObject->putText(valueObject, name);
    predicates->equalTo(predicates, "NAME", valueObject);
    int deleteRows = OH_Rdb_Delete(store_, predicates);
    valueObject->destroy(valueObject);
    predicates->destroy(predicates);
    ```

4. Query data based on the conditions specified by **OH_Predicates**.

   Call [OH_Rdb_Query()](../reference/apis-arkdata/capi-relational-store-h.md#oh_rdb_query) to query data. An **OH_Cursor** result set is returned. <br>Example:

    <!--@[rdb_OH_Rdb_Query](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    OH_Predicates *predicates = OH_Rdb_CreatePredicates("EMPLOYEE");
    if (predicates == NULL) {
        OH_LOG_ERROR(LOG_APP, "CreatePredicates failed.");
        return;
    }
    const char *columnNames[] = {"NAME", "AGE"};
    int len = sizeof(columnNames) / sizeof(columnNames[0]);
    OH_Cursor *cursor = OH_Rdb_Query(store_, predicates, columnNames, len);
    if (cursor == NULL) {
        OH_LOG_ERROR(LOG_APP, "Query failed.");
        predicates->destroy(predicates);
        return;
    }
    int columnCount = 0;
    cursor->getColumnCount(cursor, &columnCount);
    
    // OH_Cursor is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
    int64_t age;
    while (cursor->goToNextRow(cursor) == OH_Rdb_ErrCode::RDB_OK) {
        int32_t ageColumnIndex = -1;
        cursor->getColumnIndex(cursor, "AGE", &ageColumnIndex);
        if (ageColumnIndex != -1) {
            cursor->getInt64(cursor, ageColumnIndex, &age);
        }
    }
    
    // Destroy the OH_Predicates instance.
    predicates->destroy(predicates);
    // Destroy the result set.
    cursor->destroy(cursor);
    ```

   Configure predicates to match data in LIKE or NOT LIKE mode. <br>Example:

    <!--@[rdb_OH_Rdb_Query_by_like_and_notLike](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)--> 

    ``` C++
    OH_Predicates *likePredicates = OH_Rdb_CreatePredicates("EMPLOYEE");
    if (likePredicates == NULL) {
        return;
    }
    OH_VObject *likePattern = OH_Rdb_CreateValueObject();
    likePattern->putText(likePattern, "zh%");
    // Configure predicates to match data in LIKE mode.
    likePredicates->like(likePredicates, "NAME", likePattern);
    
    char *colName[] = { "NAME", "AGE" };
    auto *likeQueryCursor = OH_Rdb_Query(store_, likePredicates, colName, 2); // the length of columnNames is 2
    if (likeQueryCursor == NULL) {
        likePredicates->destroy(likePredicates);
        likePattern->destroy(likePattern);
        return;
    }
    size_t dataLength = 0;
    int colIndex = -1;
    while (likeQueryCursor->goToNextRow(likeQueryCursor) == OH_Rdb_ErrCode::RDB_OK) {
        likeQueryCursor->getColumnIndex(likeQueryCursor, "NAME", &colIndex);
        likeQueryCursor->getSize(likeQueryCursor, colIndex, &dataLength);
        char *name = (char *)malloc((dataLength + 1) * sizeof(char));
        likeQueryCursor->getText(likeQueryCursor, colIndex, name, dataLength + 1);
        free(name);
    }
    
    likeQueryCursor->destroy(likeQueryCursor);
    likePredicates->destroy(likePredicates);
    likePattern->destroy(likePattern);
    
    OH_Predicates *notLikePredicates = OH_Rdb_CreatePredicates("EMPLOYEE");
    if (notLikePredicates == NULL) {
        OH_LOG_ERROR(LOG_APP, "CreatePredicates failed.");
        return;
    }
    // Configure predicates to match data in NOT LIKE mode.
    OH_Predicates_NotLike(notLikePredicates, "NAME", "zh%");
    auto *notLikeQueryCursor = OH_Rdb_Query(store_, notLikePredicates, colName, 2); // the length of columnNames is 2
    if (notLikeQueryCursor == NULL) {
        notLikePredicates->destroy(notLikePredicates);
        return;
    }
    dataLength = 0;
    colIndex = -1;
    while (notLikeQueryCursor->goToNextRow(notLikeQueryCursor) == OH_Rdb_ErrCode::RDB_OK) {
        notLikeQueryCursor->getColumnIndex(notLikeQueryCursor, "NAME", &colIndex);
        notLikeQueryCursor->getSize(notLikeQueryCursor, colIndex, &dataLength);
        char *name2 = (char *)malloc((dataLength + 1) * sizeof(char));
        notLikeQueryCursor->getText(notLikeQueryCursor, colIndex, name2, dataLength + 1);
        free(name2);
    }
    
    notLikePredicates->destroy(notLikePredicates);
    notLikeQueryCursor->destroy(notLikeQueryCursor);
    ```

   Configure predicates to match data in **GLOB** or **NOT GLOB** mode. <br>Example:

    <!--@[rdb_OH_Rdb_Query_by_glob_and_notGlob](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    OH_Predicates *globPredicates = OH_Rdb_CreatePredicates("EMPLOYEE");
    if (globPredicates == NULL) {
        OH_LOG_ERROR(LOG_APP, "CreatePredicates failed.");
        return;
    }
    // Configure predicates to match in GLOB mode.
    OH_Predicates_Glob(globPredicates, "NAME", "zh*");
    
    char *colName[] = { "NAME", "AGE" };
    auto *globQueryCursor = OH_Rdb_Query(store_, globPredicates, colName, 2); // the length of columnNames is 2
    if (globQueryCursor == NULL) {
        OH_LOG_ERROR(LOG_APP, "Query failed.");
        globPredicates->destroy(globPredicates);
        return;
    }
    size_t dataLength = 0;
    int colIndex = -1;
    while (globQueryCursor->goToNextRow(globQueryCursor) == OH_Rdb_ErrCode::RDB_OK) {
        globQueryCursor->getColumnIndex(globQueryCursor, "NAME", &colIndex);
        globQueryCursor->getSize(globQueryCursor, colIndex, &dataLength);
        char *name = (char *)malloc((dataLength + 1) * sizeof(char));
        globQueryCursor->getText(globQueryCursor, colIndex, name, dataLength + 1);
        free(name);
    }
    globQueryCursor->destroy(globQueryCursor);
    globPredicates->destroy(globPredicates);
    
    OH_Predicates *notGlobPredicates = OH_Rdb_CreatePredicates("EMPLOYEE");
    if (notGlobPredicates == NULL) {
        OH_LOG_ERROR(LOG_APP, "CreatePredicates failed.");
        return;
    }
    // Configure predicates to match in NOT GLOB mode.
    OH_Predicates_NotGlob(notGlobPredicates, "NAME", "zh*");
    auto *notGlobQueryCursor = OH_Rdb_Query(store_, notGlobPredicates, colName, 2); // the length of columnNames is 2
    if (notGlobQueryCursor == NULL) {
        OH_LOG_ERROR(LOG_APP, "Query failed.");
        notGlobPredicates->destroy(notGlobPredicates);
        return;
    }
    dataLength = 0;
    colIndex = -1;
    while (notGlobQueryCursor->goToNextRow(notGlobQueryCursor) == OH_Rdb_ErrCode::RDB_OK) {
        notGlobQueryCursor->getColumnIndex(notGlobQueryCursor, "NAME", &colIndex);
        notGlobQueryCursor->getSize(notGlobQueryCursor, colIndex, &dataLength);
        char *name2 = (char *)malloc((dataLength + 1) * sizeof(char));
        notGlobQueryCursor->getText(notGlobQueryCursor, colIndex, name2, dataLength + 1);
        free(name2);
    }
    notGlobQueryCursor->destroy(notGlobQueryCursor);
    notGlobPredicates->destroy(notGlobPredicates);
    ```

   To specify a locale for sorting, such as **zh_CN** for Chinese or **tr_TR** for Turkish, call [OH_Rdb_SetLocale()](../reference/apis-arkdata/capi-relational-store-h.md#oh_rdb_setlocale).

    <!--@[rdb_OH_Rdb_SetLocale](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    OH_Rdb_SetLocale(store_, "zh_CN");
    ```

    To configure the full-text search (FTS) dynamic library, call [OH_Rdb_SetPlugins()](../reference/apis-arkdata/capi-relational-store-h.md#oh_rdb_setplugins).

    For details about the constraints, see the **pluginLibs** configuration item in [StoreConfig](../reference/apis-arkdata/arkts-apis-data-relationalStore-i.md#storeconfig).

    <!--@[rdb_OH_Rdb_SetPlugins](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    const char *plugins[] = {
        "/data/storage/el1/bundle/libs/arm64/libtokenizer.so"
    };
    
    int32_t count = sizeof(plugins) / sizeof(plugins[0]);
    auto setResult = OH_Rdb_SetPlugins(config, plugins, count);
    ```

5. Insert, delete, or update data using a transaction object.

   Call [OH_RdbTransOption_SetType()](../reference/apis-arkdata/capi-oh-rdb-transaction-h.md#oh_rdbtransoption_settype) to configure the transaction type. The supported types are **DEFERRED** (default), **IMMEDIATE**, and **EXCLUSIVE**.

   Call [OH_Rdb_CreateTransaction()](../reference/apis-arkdata/capi-relational-store-h.md#oh_rdb_createtransaction) to create a transaction object and use it to perform transaction operations.

    <!--@[rdb_OH_Rdb_CreateTransaction](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->    

    ``` C++
    OH_RDB_TransOptions *options = OH_RdbTrans_CreateOptions();
    // Configure the transaction type.
    OH_RdbTransOption_SetType(options, RDB_TRANS_DEFERRED);
    OH_Rdb_Transaction *trans = nullptr;
    // Create a transaction object.
    int res = OH_Rdb_CreateTransaction(store_, options, &trans);
    OH_RdbTrans_DestroyOptions(options);
    ```

    <!--@[rdb_trans_insert](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)--> 

    ``` C++
    char transCreateTableSql[] =
        "CREATE TABLE IF NOT EXISTS transaction_table (id INTEGER PRIMARY KEY AUTOINCREMENT, data1 INTEGER, "
        "data2 INTEGER, data3 FLOAT, data4 TEXT, data5 BLOB, data6 ASSET, data7 ASSETS, data8 UNLIMITED INT, "
        "data9 FLOATVECTOR);";
    
    auto *execResult = OH_Value_Create();
    
    // Execute SQL statements to create a database table through the transaction object.
    int ret = OH_RdbTrans_Execute(trans, transCreateTableSql, nullptr, &execResult);
    
    // Create an OH_Data_Values instance.
    OH_Data_Values *values = OH_Values_Create();
    ret = OH_Values_PutInt(values, 1); // The value of id is 1
    ret = OH_Values_PutInt(values, 2); // The value of data2 is 2
    ret = OH_Values_PutReal(values, 1.1); // The value of data3 is 1.1
    ret = OH_Values_PutText(values, "1"); // The value of data4 is 1
    unsigned char val[] = {1, 2};
    ret = OH_Values_PutBlob(values, val, sizeof(val) / sizeof(val[0]));
    
    Data_Asset *asset = OH_Data_Asset_CreateOne();
    ret = OH_Data_Asset_SetName(asset, "name");
    ret = OH_Values_PutAsset(values, asset);
    OH_Data_Asset_DestroyOne(asset);
    
    Data_Asset **assets = OH_Data_Asset_CreateMultiple(2); // The number of created Data_Assets is 2
    ret = OH_Data_Asset_SetName(assets[0], "name1");
    ret = OH_Data_Asset_SetName(assets[1], "name2");
    ret = OH_Values_PutAssets(values, assets, 2); // The number of Data_Assets is 2
    ret = OH_Data_Asset_DestroyMultiple(assets, 2); // The number of destroyed Data_Assets is 2
    
    uint64_t bigInt[] = {1, 2, 3, 4, 5};
    ret = OH_Values_PutUnlimitedInt(values, 0, bigInt, sizeof(bigInt) / sizeof(bigInt[0]));
    
    const char *insertSql = "INSERT INTO transaction_table "
                            "(data1, data2, data3, data4, data5, data6, data7, data8) VALUES (?, ?, ?, ?, ?, ?, ?, ?)";
    OH_Data_Value *outValue = nullptr;
    
    // Execute SQL statements to insert data through the transaction object.
    ret = OH_RdbTrans_Execute(trans, insertSql, values, &outValue);
    OH_Value_Destroy(outValue);
    OH_Values_Destroy(values);
    
    OH_VBucket *transValueBucket = OH_Rdb_CreateValuesBucket();
    transValueBucket->putInt64(transValueBucket, "data1", 1); // The value of data1 is 1
    transValueBucket->putInt64(transValueBucket, "data2", 2); // The value of data2 is 2
    transValueBucket->putReal(transValueBucket, "data3", 1.1); // The value of data3 is 1.1
    transValueBucket->putText(transValueBucket, "data4", "1"); // The value of data4 is 1
    transValueBucket->putBlob(transValueBucket, "data5", val, sizeof(val) / sizeof(val[0]));
    int64_t insertRowId = -1;
    // Insert the OH_VBucket data through the transaction object.
    int insertRet = OH_RdbTrans_Insert(trans, "transaction_table", transValueBucket, &insertRowId);
    transValueBucket->destroy(transValueBucket);
    
    OH_VBucket *transValueBucket2 = OH_Rdb_CreateValuesBucket();
    transValueBucket2->putInt64(transValueBucket2, "id", 1); // The value of id is 1
    transValueBucket2->putInt64(transValueBucket2, "data2", 2); // The value of data2 is 2
    transValueBucket2->putReal(transValueBucket2, "data3", 1.2); // The value of data3 is 1.2
    
    int64_t transInsertRow = -1;
    // Configure conflict resolutions when data is inserted.
    int result = OH_RdbTrans_InsertWithConflictResolution(
        trans, "transaction_table", transValueBucket2, Rdb_ConflictResolution::RDB_CONFLICT_REPLACE, &transInsertRow);
    
    transValueBucket2->destroy(transValueBucket2);
    ```

    <!--@[rdb_trans_update](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    OH_VBucket *transValueBucket3 = OH_Rdb_CreateValuesBucket();
    transValueBucket3->putInt64(transValueBucket3, "id", 1); // The value of id is 1
    transValueBucket3->putInt64(transValueBucket3, "data2", 3); // The value of data2 is 3
    transValueBucket3->putReal(transValueBucket3, "data3", 1.2); // The value of data3 is 1.2
    
    OH_Predicates *transUpdatePredicates = OH_Rdb_CreatePredicates("transaction_table");
    if (transUpdatePredicates == NULL) {
        OH_LOG_ERROR(LOG_APP, "CreatePredicates failed.");
        transValueBucket3->destroy(transValueBucket3);
        return;
    }
    auto targetValue = OH_Rdb_CreateValueObject();
    int64_t two = 2;
    targetValue->putInt64(targetValue, &two, 1); // The value of id is 1
    transUpdatePredicates->equalTo(transUpdatePredicates, "data2", targetValue);
    
    int64_t updateRows = -1;
    // Configure conflict resolutions when data is updated.
    OH_RdbTrans_UpdateWithConflictResolution(trans, transValueBucket3, transUpdatePredicates,
                                             Rdb_ConflictResolution::RDB_CONFLICT_REPLACE, &updateRows);
    targetValue->destroy(targetValue);
    transValueBucket3->destroy(transValueBucket3);
    transUpdatePredicates->destroy(transUpdatePredicates);
    ```

    <!--@[rdb_trans_query](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    OH_Predicates *predicates = OH_Rdb_CreatePredicates("transaction_table");
    if (predicates == NULL) {
        OH_LOG_ERROR(LOG_APP, "CreatePredicates failed.");
        return;
    }
    const char *columns[] = {"data1", "data2", "data3"};
    // Query data through the transaction object.
    OH_Cursor *cursor = OH_RdbTrans_Query(trans, predicates, columns, sizeof(columns) / sizeof(columns[0]));
    if (cursor == NULL) {
        OH_LOG_ERROR(LOG_APP, "Query failed.");
        predicates->destroy(predicates);
        return;
    }
    int columnCount = 0;
    cursor->getColumnCount(cursor, &columnCount);
    
    predicates->destroy(predicates);
    cursor->destroy(cursor);
    ```

    <!--@[rdb_trans_delete](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    OH_Predicates *predicates2 = OH_Rdb_CreatePredicates("transaction_table");
    if (predicates2 == NULL) {
       OH_LOG_ERROR(LOG_APP, "CreatePredicates failed.");
       return;
    }
    OH_VObject *valueObject = OH_Rdb_CreateValueObject();
    if (valueObject == NULL) {
       OH_LOG_ERROR(LOG_APP, "CreateValueObject failed.");
       predicates2->destroy(predicates2);
       return;
    }
    valueObject->putText(valueObject, "1"); // Change the text value of the object to 1
    predicates2->equalTo(predicates2, "data4", valueObject);
    int64_t changes = -1;
    // Delete data through the transaction object.
    int deleteRet = OH_RdbTrans_Delete(trans, predicates2, &changes);
    predicates2->destroy(predicates2);
    valueObject->destroy(valueObject);
    ```

    <!--@[rdb_OH_RdbTrans_Commit](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    // Commit a transaction.
    OH_RdbTrans_Commit(trans);
    // Destroy the transaction.
    OH_RdbTrans_Destroy(trans);
    ```

    <!--@[rdb_OH_RdbTrans_Rollback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    OH_RDB_TransOptions *options2 = OH_RdbTrans_CreateOptions();
    OH_RdbTransOption_SetType(options2, RDB_TRANS_DEFERRED);
    OH_Rdb_Transaction *trans2 = nullptr;
    int transCreateRet = OH_Rdb_CreateTransaction(store_, options2, &trans2);
    OH_RdbTrans_DestroyOptions(options2);

    // Roll back the transaction.
    OH_RdbTrans_Rollback(trans2);
    OH_RdbTrans_Destroy(trans2);
    ```

6. Attach a database.

    Call [OH_Rdb_Attach()](../reference/apis-arkdata/capi-relational-store-h.md#oh_rdb_attach) to attach a database file to the current database so that SQL statements can access its data directly.

    This API does not support encrypted databases.

    After the **attach** API is called, the RDB store is switched to the non-WAL mode, which may undermine the performance. Before switching the mode, ensure that all **OH_Cursor** objects have been destroyed and all write operations have been completed. Otherwise, error 14800015 is reported.

    The **attach** API cannot be called concurrently. Concurrent calls may cause the system to become unresponsive and trigger 14800015. If this occurs, try to call **attach()** again later.

    When the attached database is no longer needed, call [OH_Rdb_Detach()](../reference/apis-arkdata/capi-relational-store-h.md#oh_rdb_detach) to detach it.

    <!--@[rdb_OH_Rdb_Attach_and_Detach](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)--> 

    ``` C++
    char attachStoreTableCreateSql[] = "CREATE TABLE IF NOT EXISTS EMPLOYEE (ID INTEGER PRIMARY KEY AUTOINCREMENT, "
        "NAME TEXT NOT NULL, AGE INTEGER, SALARY REAL, CODES BLOB)";
    OH_Rdb_ConfigV2 *attachDbConfig = OH_Rdb_CreateConfig();
    if (attachDbConfig == NULL) {
        OH_LOG_ERROR(LOG_APP, "Create store config failed.");
        return;
    }
    OH_Rdb_SetModuleName(attachDbConfig, "entry");
    OH_Rdb_SetDatabaseDir(attachDbConfig, "/data/storage/el3/database");
    OH_Rdb_SetArea(attachDbConfig, RDB_SECURITY_AREA_EL3);
    OH_Rdb_SetStoreName(attachDbConfig, "RdbAttach.db");
    OH_Rdb_SetSecurityLevel(attachDbConfig, OH_Rdb_SecurityLevel::S3);
    OH_Rdb_SetBundleName(attachDbConfig, "com.example.nativedemo");

    int errCode1 = 0;
    // Create the additional sample database RdbAttach.db.
    OH_Rdb_Store *attachStore = OH_Rdb_CreateOrOpen(attachDbConfig, &errCode1);
    
    if (attachStore == NULL) {
        OH_LOG_ERROR(LOG_APP, "Create attachStore failed, errCode: %{public}d", errCode1);
        OH_Rdb_DestroyConfig(attachDbConfig);
        return;
    }
    
    if (errCode1 != OH_Rdb_ErrCode::RDB_OK) {
        OH_LOG_ERROR(LOG_APP, "Create attachStore failed, errCode: %{public}d", errCode1);
        OH_Rdb_DestroyConfig(attachDbConfig);
        OH_Rdb_CloseStore(attachStore);
        return;
    }
    errCode1 = OH_Rdb_Execute(attachStore, attachStoreTableCreateSql);
    if (errCode1 != OH_Rdb_ErrCode::RDB_OK) {
        OH_LOG_ERROR(LOG_APP, "Create table failed, errCode: %{public}d", errCode1);
        OH_Rdb_DestroyConfig(attachDbConfig);
        OH_Rdb_CloseStore(attachStore);
        return;
    }
    OH_VBucket *valueBucket = OH_Rdb_CreateValuesBucket();
    valueBucket->putText(valueBucket, "NAME", "Lisa");
    valueBucket->putInt64(valueBucket, "AGE", 18); // The value of AGE is 18
    valueBucket->putReal(valueBucket, "SALARY", 100.5); // The value of SALARY is 100.5
    uint8_t arr[] = {1, 2, 3, 4, 5};
    int len = sizeof(arr) / sizeof(arr[0]);
    valueBucket->putBlob(valueBucket, "CODES", arr, len);
    int rowId = OH_Rdb_Insert(attachStore, "EMPLOYEE", valueBucket);
    OH_LOG_INFO(LOG_APP, "Insert data result: %{public}d", rowId);
    valueBucket->destroy(valueBucket);
    OH_Rdb_CloseStore(attachStore);
    // ...
    // Attach databases.
    size_t attachedNumber = 0;
    // The maximum waiting time allowed for attaching databases is 10
    errCode = OH_Rdb_Attach(store_, attachDbConfig, "attach", 10, &attachedNumber);
    OH_Rdb_DestroyConfig(attachDbConfig);
    if (errCode != OH_Rdb_ErrCode::RDB_OK) {
        OH_LOG_ERROR(LOG_APP, "Attach store failed, errCode: %{public}d", errCode);
        return;
    }
    OH_Predicates *predicates = OH_Rdb_CreatePredicates("attach.EMPLOYEE");
    if (predicates == NULL) {
        OH_LOG_ERROR(LOG_APP, "CreatePredicates failed.");
        // The maximum waiting time allowed for detaching databases is 10
        errCode = OH_Rdb_Detach(store_, "attach", 10, &attachedNumber);
        OH_LOG_INFO(LOG_APP, "Detach result: %{public}d", errCode);
        return;
    }
    char *colName[] = {};
    int len = sizeof(colName) / sizeof(colName[0]);
    OH_Cursor *cursor = OH_Rdb_Query(store_, predicates, colName, len);
    if (cursor == NULL) {
        OH_LOG_ERROR(LOG_APP, "Query failed.");
        // The maximum waiting time allowed for detaching databases is 10
        errCode = OH_Rdb_Detach(store_, "attach", 10, &attachedNumber);
        OH_LOG_INFO(LOG_APP, "Detach result: %{public}d", errCode);
        predicates->destroy(predicates);
        return;
    }
    int rowCount = -1;
    errCode = cursor->getRowCount(cursor, &rowCount);
    if (errCode != OH_Rdb_ErrCode::RDB_OK) {
        OH_LOG_ERROR(LOG_APP, "Get row count failed, errCode: %{public}d", errCode);
    } else {
        OH_LOG_INFO(LOG_APP, "Query success, row count: %{public}d", rowCount);
    }
    cursor->destroy(cursor);
    predicates->destroy(predicates);
    // Detach databases.
    // The maximum waiting time allowed for detaching databases is 10
    errCode = OH_Rdb_Detach(store_, "attach", 10, &attachedNumber);
    OH_LOG_INFO(LOG_APP, "Detach result: %{public}d", errCode);
    ```

7. Insert data assets into a table.

    <!--@[rdb_asset_insert](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    // If the column attribute is a single asset, use asset in the SQL statements. If the column attribute is multiple assets, use assets in the SQL statements.
    char createAssetTableSql[] = "CREATE TABLE IF NOT EXISTS asset_table (id INTEGER PRIMARY KEY AUTOINCREMENT,"
        "data1 ASSET, data2 ASSETS );";
    const char *table = "asset_table";
    int errCode = OH_Rdb_Execute(store_, createAssetTableSql);
    OH_VBucket *valueBucket = OH_Rdb_CreateValuesBucket();
    Data_Asset *asset = OH_Data_Asset_CreateOne();
    OH_Data_Asset_SetName(asset, "name0");
    OH_Data_Asset_SetUri(asset, "uri0");
    OH_Data_Asset_SetPath(asset, "path0");
    OH_Data_Asset_SetCreateTime(asset, 1); // Set the creation time of Data_Asset to 1
    OH_Data_Asset_SetModifyTime(asset, 1); // Set the modify time of Data_Asset to 1
    OH_Data_Asset_SetSize(asset, 1); // Set the size of the Data_Asset to 1
    OH_Data_Asset_SetStatus(asset, Data_AssetStatus::ASSET_NORMAL);
    errCode = OH_VBucket_PutAsset(valueBucket, "data1", asset);
    
    Data_Asset **assets = OH_Data_Asset_CreateMultiple(2);
    
    OH_Data_Asset_SetName(assets[0], "name0");
    OH_Data_Asset_SetUri(assets[0], "uri0");
    OH_Data_Asset_SetPath(assets[0], "path0");
    OH_Data_Asset_SetCreateTime(assets[0], 1); // Set the creation time of Data_Asset to 1
    OH_Data_Asset_SetModifyTime(assets[0], 1); // Set the modify time of Data_Asset to 1
    OH_Data_Asset_SetSize(assets[0], 1); // Set the size of the Data_Asset to 1
    OH_Data_Asset_SetStatus(assets[0], Data_AssetStatus::ASSET_NORMAL);
    
    OH_Data_Asset_SetName(assets[1], "name1");
    OH_Data_Asset_SetUri(assets[1], "uri1");
    OH_Data_Asset_SetPath(assets[1], "path1");
    OH_Data_Asset_SetCreateTime(assets[1], 1); // Set the creation time of Data_Asset to 1
    OH_Data_Asset_SetModifyTime(assets[1], 1); // Set the modify time of Data_Asset to 1
    OH_Data_Asset_SetSize(assets[1], 1); // Set the size of the Data_Asset to 1
    OH_Data_Asset_SetStatus(assets[1], Data_AssetStatus::ASSET_NORMAL);
    
    uint32_t assetsCount = 2;
    errCode = OH_VBucket_PutAssets(valueBucket, "data2", assets, assetsCount);
    int rowID = OH_Rdb_Insert(store_, table, valueBucket);
    // Destroy Data_Asset* and Data_Asset**.
    OH_Data_Asset_DestroyMultiple(assets, assetsCount);
    OH_Data_Asset_DestroyOne(asset);
    valueBucket->destroy(valueBucket);
    ```

8. Read data assets from the result set.

    <!--@[rdb_asset_query](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    OH_Predicates *predicates = OH_Rdb_CreatePredicates("asset_table");
    if (predicates == NULL) {
        OH_LOG_ERROR(LOG_APP, "CreatePredicates failed.");
        return;
    }
    OH_Cursor *cursor = OH_Rdb_Query(store_, predicates, NULL, 0);
    if (cursor == NULL) {
        predicates->destroy(predicates);
    } else {
        cursor->goToNextRow(cursor);
        
        uint32_t assetCount = 0;
        // assetCount is an output parameter that indicates the number of assets in this column.
        int errCode = cursor->getAssets(cursor, 2, nullptr, &assetCount); // Column index is 2
        Data_Asset **assets = OH_Data_Asset_CreateMultiple(assetCount);
        errCode = cursor->getAssets(cursor, 2, assets, &assetCount); // Column index is 2
        // The number of Data_Assets is 2
        if (assetCount < 2) {
            predicates->destroy(predicates);
            cursor->destroy(cursor);
        } else {
            Data_Asset *asset = assets[1];
            char name[10] = "";
            size_t nameLength = 10;
            errCode = OH_Data_Asset_GetName(asset, name, &nameLength);
            
            char uri[10] = "";
            size_t uriLength = 10;
            errCode = OH_Data_Asset_GetUri(asset, uri, &uriLength);
            
            char path[10] = "";
            size_t pathLength = 10;
            errCode = OH_Data_Asset_GetPath(asset, path, &pathLength);
            
            int64_t createTime = 0;
            errCode = OH_Data_Asset_GetCreateTime(asset, &createTime);
            
            int64_t modifyTime = 0;
            errCode = OH_Data_Asset_GetModifyTime(asset, &modifyTime);
            
            size_t size = 0;
            errCode = OH_Data_Asset_GetSize(asset, &size);
            
            Data_AssetStatus status = Data_AssetStatus::ASSET_NULL;
            errCode = OH_Data_Asset_GetStatus(asset, &status);
            
            predicates->destroy(predicates);
            OH_Data_Asset_DestroyMultiple(assets, assetCount);
            cursor->destroy(cursor);
        }
    }
    ```

9. Obtain the last modification time of data. Call [OH_Rdb_FindModifyTime()](../reference/apis-arkdata/capi-relational-store-h.md#oh_rdb_findmodifytime) to query the last modification time of data in the specified column of a table. This API returns an **OH_Cursor** object with two columns: the input primary key or row ID, and the last modification time. <br>Example:

    <!--@[rdb_OH_Rdb_FindModifyTime](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    constexpr uint32_t  tableCount = 1;
    const char *table[tableCount];
    table[0] = "EMPLOYEE";
    Rdb_DistributedConfig distributedConfig{ .version = 1, .isAutoSync = true };
    // Set a distributed table.
    OH_Rdb_SetDistributedTables(store_, table, tableCount, RDB_DISTRIBUTED_CLOUD, &distributedConfig);
    // Obtain the last modification time of data.
    OH_VObject *values = OH_Rdb_CreateValueObject();
    int64_t keys[] = { 1 };
    values->putInt64(values, keys, 1); // The value of keys is 1
    OH_Cursor *cursor = OH_Rdb_FindModifyTime(store_, "EMPLOYEE", "ROWID", values);
    if (cursor == NULL) {
        return;
    }
    while (cursor->goToNextRow(cursor) == OH_Rdb_ErrCode::RDB_OK) {
        int64_t rowId;
        cursor->getInt64(cursor, 1, &rowId); // 1 is the column index
    }
    ```

10. Delete the database. Call [OH_Rdb_DeleteStoreV2()](../reference/apis-arkdata/capi-relational-store-h.md#oh_rdb_deletestorev2) to delete the RDB store and related files. <br>Example:

    <!--@[rdb_OH_Rdb_CloseStore_and_DeleteStore](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelationalStore/RdbStore/entry/src/main/cpp/napi_init.cpp)-->

    ``` C++
    // Close the database instance.
    OH_Rdb_CloseStore(store_);
    // Delete the database file.
    OH_Rdb_DeleteStoreV2(config);
    ```
