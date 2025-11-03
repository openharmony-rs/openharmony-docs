# 数据库加密 (C/C++)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @widecode; @htt1997-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

## 场景介绍

为了增强数据库的安全性，数据库提供了安全的加密功能，以有效保护存储的内容。
通过数据库加密，实现了数据库数据存储的保密性和完整性要求，使得数据库以密文方式存储并在密态方式下工作，确保了数据安全。

加密后的数据库只能通过接口进行访问，无法通过其它方式打开数据库文件。数据库的加密属性在创建数据库时确认，无法变更。

当前仅支持使用关系型数据库（C/C++）进行数据库加密。

## 开发步骤

关系型数据库通过调用OH_Rdb_SetEncrypted方法来设置是否加密。isEncrypted参数为true时表示加密，为false时表示不加密，默认不加密。

当isEncrypted为true时，可调用OH_Rdb_SetCryptoParam方法设置自定义的加密/解密密钥和算法等参数。





1. CMakeLists.txt中添加以下lib。

    ```txt
    libnative_rdb_ndk.z.so
    ```

2. 导入头文件。

    <!-- @[encryption_include](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelatetionalStore/NativeDataEncryption/entry/src/main/cpp/napi_init.cpp) -->



3. 针对是否配置自定义加密/解密参数，有如下两种场景：

    * 场景1：不配置自定义加密/解密参数，此时会使用默认的配置进行数据库的加密/解密。

    <!-- @[DefaultConfigRdbStore](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelatetionalStore/NativeDataEncryption/entry/src/main/cpp/napi_init.cpp) -->



    * 场景2：使用OH_Rdb_SetCryptoParam接口配置加密参数，此时会使用开发者自定义的密钥和算法参数进行数据库的加密/解密。
    
      如果开发者不关心加密算法及参数，使用默认加密配置即可，无需创建和配置自定义加密参数。

    <!-- @[CustomizedConfigRdbStore](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/RelatetionalStore/NativeDataEncryption/entry/src/main/cpp/napi_init.cpp) -->


