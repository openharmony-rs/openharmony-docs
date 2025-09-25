# Checking a Key (C/C++)

HUKS provides APIs for applications to query whether a specified key exists.

## Add the dynamic library in the CMake script.
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so)
```
## How to Develop

1. Construct the parameters.
   - Specify the key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).
   - Set the [tag](../../reference/apis-universal-keystore-kit/_huks_type_api.md#oh_huks_tag) of the key to check. By default, this parameter is left empty.

2. Use [OH_Huks_IsKeyItemExist](../../reference/apis-universal-keystore-kit/_huks_key_api.md#oh_huks_iskeyitemexist) to check whether the key exists.

```c++
#include "huks/native_huks_api.h"
#include "huks/native_huks_param.h"
#include "napi/native_api.h"
#include <string.h>
static napi_value IsKeyExist(napi_env env, napi_callback_info info)
{
    /* 1. Obtain the key alias. */
    struct OH_Huks_Blob keyAlias = {
        (uint32_t)strlen("test_key"),
        (uint8_t *)"test_key"
    };
    
    /* 2. Call OH_Huks_IsKeyItemExist to check whether the key exists. */
    struct OH_Huks_Result ohResult = OH_Huks_IsKeyItemExist(&keyAlias, nullptr);
    // OH_HUKS_SUCCESS means the key exists, and OH_HUKS_ERR_CODE_ITEM_NOT_EXIST means the opposite.

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```
