# Obtaining Device Location Information (C/C++)
<!--Kit: Location Kit-->
<!--Subsystem: Location-->
<!--Owner: @xxthadsl-->
<!--Designer: @liu-binjun-->
<!--Tester: @gcw_MslijYkf-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=56b2c15d187acc864bf14dd89f9c4aae5d899ee7 translatedAt=2026-11-03T07:13:41.907Z pushedAt=2026-11-03T07:13:41.907Z nl=1 -->


## When to Use

You can call location-related APIs to listen for device location changes.

## Function Description

| Name                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| OH_Location_IsLocatingEnabled(bool* enabled)     | Checks whether the location switch is enabled.                                |
| OH_Location_StartLocating(const Location_RequestConfig* requestConfig) | Starts locating and subscribes to location changes.|
| Location_ResultCode OH_Location_StopLocating(const Location_RequestConfig* requestConfig) | Stops locating and unsubscribes from location changes.|
| OH_LocationInfo_GetBasicInfo(Location_Info* location)   | Obtains basic information from the location result, such as the longitude, latitude, altitude, and speed.|
| OH_LocationInfo_GetAdditionalInfo(Location_Info* location, char* additionalInfo, uint32_t length) | Obtains additional information from the location result. The additional information is a string in JSON format.|
| OH_Location_CreateRequestConfig(void) | Creates a **Location_RequestConfig** instance.   |
| OH_Location_DestroyRequestConfig(Location_RequestConfig* requestConfig) | Destroys the **Location_RequestConfig** instance and reclaims the memory. |
| OH_LocationRequestConfig_SetUseScene(Location_RequestConfig* requestConfig, Location_UseScene useScene) | Sets the user activity scenario in a location request.<br>If **useScene** is set, **powerConsumptionScene** is invalid.<br>Otherwise, **powerConsumptionScene** takes effect.<br>If neither of the two parameters is set, **useScene** is defaulted to **LOCATION_USE_SCENE_DAILY_LIFE_SERVICE**, and **powerConsumptionScene** is invalid.    |
| OH_LocationRequestConfig_SetPowerConsumptionScene(Location_RequestConfig* requestConfig, Location_PowerConsumptionScene powerConsumptionScene) | Sets the power consumption scenario in a location request.     |
| OH_LocationRequestConfig_SetInterval(Location_RequestConfig* requestConfig, int interval) | Sets the interval for reporting location results.                              |
| OH_LocationRequestConfig_SetCallback(Location_RequestConfig* requestConfig, Location_InfoCallback callback, void* userData) | Sets the callback for receiving reported location information.    |


## How to Develop
1. Create a native C++ project.

   ![](figures/001.png)

2. Before using system basic location capabilities, check whether your application has been granted the permission to access the device location information. If not, your application first needs to apply for the required permission. For details, see [Applying for Location Permissions](location-permission-guidelines.md).


3. Add the dynamic dependency libraries into the **CMakeLists.txt** file.

   ```c
   target_link_libraries(entry PUBLIC libace_napi.z.so)
   target_link_libraries(entry PUBLIC libhilog_ndk.z.so)
   target_link_libraries(entry PUBLIC liblocation_ndk.so)
   ```

4. Write the **napi_init.cpp** file to import related modules.

   ```c
   #include "napi/native_api.h"
   #include "LocationKit/oh_location.h"
   #include "LocationKit/oh_location_type.h"
   #include "hilog/log.h"
   #include <stdlib.h>
   #include <string>
   ```

5. Check whether the location switch is enabled before calling the API to obtain device location information.

   The return result is a Boolean value. The value **true** indicates that the location switch is enabled, and the value **false** indicates the opposite.

   ```c
    std::string GetErrorMsgFromErrorCode(int errorCode)
    {
        switch(errorCode) {
           case LOCATION_PERMISSION_DENIED:
              return "Permission verification failed. The application does not have the permission required to call the API.";
           case LOCATION_INVALID_PARAM:
              return "Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.";
           case LOCATION_NOT_SUPPORTED:
              return "Capability not supported. Failed to call this API due to limited device capabilities.";
           case LOCATION_SERVICE_UNAVAILABLE:
              return "The location service is unavailable.";
           case LOCATION_SWITCH_OFF:
              return "The location switch is off.";
           default:
              return "Unknown error. error code: " + std::to_string(errorCode);
        }
    }

    static napi_value OhLocationIsEnabled(napi_env env, napi_callback_info info)
    {
        bool isEnabled = false;
        int resultCode = OH_Location_IsLocatingEnabled(&isEnabled);
        napi_value result = NULL;
        if (resultCode != LOCATION_SUCCESS) {
           std::string errorMsg = GetErrorMsgFromErrorCode(resultCode);
           napi_throw_error(env, std::to_string(resultCode).c_str(), errorMsg.c_str());
           napi_get_undefined(env, &result);
           return result;
        }
        napi_get_boolean(env, isEnabled, &result);
        return result;
    }
    // Add related APIs to the Init function.
    EXTERN_C_START
    static napi_value Init(napi_env env, napi_value exports)
    {
        napi_property_descriptor desc[] = {
            {"ohLocationIsEnabled", NULL, OhLocationIsEnabled, NULL, NULL, NULL, napi_default, NULL},
        };
        napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
        return exports;
    }
    EXTERN_C_END
   ```

6. Start positioning and subscribe to location changes.

   ```c
   // Define a location request.
   struct Location_RequestConfig *g_requestConfig = NULL;
   void *mydata = NULL;
   
   // Define a callback to receive location information.
   void reportLocation(Location_Info* location, void* userData)
   {
       Location_BasicInfo baseInfo = OH_LocationInfo_GetBasicInfo(location);
       char additionalInfo[1024] = "";
       Location_ResultCode result = OH_LocationInfo_GetAdditionalInfo(location, additionalInfo, sizeof(additionalInfo));
       // Compare the returned userData with mydata to identify callbacks for this location request.
       if (mydata == userData) {
           OH_LOG_INFO(LOG_APP, "userData is mydata");
       }
       return;
   }

   // Subscribe to location information.
   static napi_value OhLocationStartLocating(napi_env env, napi_callback_info info)
   {
       if (g_requestConfig == NULL) {
          g_requestConfig = OH_Location_CreateRequestConfig();
       }
       OH_LocationRequestConfig_SetUseScene(g_requestConfig, LOCATION_USE_SCENE_NAVIGATION);
       OH_LocationRequestConfig_SetInterval(g_requestConfig, 1);
       // mydata can be any user-defined type. It is returned to reportLocation to identify this request's callback.
       mydata = (void *)malloc(sizeof("mydata"));
       napi_value result = NULL;
       if (mydata == NULL) {
          int errCode = LOCATION_INVALID_PARAM;
          std::string errorMsg = GetErrorMsgFromErrorCode(errCode);
          napi_throw_error(env, std::to_string(errCode).c_str(), errorMsg.c_str());
          napi_get_undefined(env, &result);
          return result;
       }

       OH_LocationRequestConfig_SetCallback(g_requestConfig, reportLocation, mydata);
       int resultCode = OH_Location_StartLocating(g_requestConfig);
       if (resultCode != LOCATION_SUCCESS) {
           std::string errorMsg = GetErrorMsgFromErrorCode(resultCode);
           napi_throw_error(env, std::to_string(resultCode).c_str(), errorMsg.c_str());
           napi_get_undefined(env, &result);
           return result;
       }
       napi_create_int32(env, resultCode, &result);
       return result;
   }

   // Unsubscribe from location information. The value of g_requestConfig must be the same as the object passed during subscription.
   static napi_value OhLocationStopLocating(napi_env env, napi_callback_info info)
   {
       int32_t resultCode = OH_Location_StopLocating(g_requestConfig);
       if (g_requestConfig != NULL) {
           OH_Location_DestroyRequestConfig(g_requestConfig);
           g_requestConfig = NULL;
       }
       if (mydata != NULL) {
           free(mydata);
           mydata = NULL;
       }
       napi_value result = NULL;
       if (resultCode != LOCATION_SUCCESS) {
           std::string errorMsg = GetErrorMsgFromErrorCode(resultCode);
           napi_throw_error(env, std::to_string(resultCode).c_str(), errorMsg.c_str());
           napi_get_undefined(env, &result);
           return result;
       }
       napi_create_int32(env, resultCode, &result);
       return result;
   }

   // Add related APIs to the Init function.
   EXTERN_C_START
   static napi_value Init(napi_env env, napi_value exports)
   {
       napi_property_descriptor desc[] = {
           {"ohLocationStartLocating", NULL, OhLocationStartLocating, NULL, NULL, NULL, napi_default, NULL},
           {"ohLocationStopLocating", NULL, OhLocationStopLocating, NULL, NULL, NULL, napi_default, NULL},
       };
       napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
       return exports;
   }
   EXTERN_C_END
   ```

7. Introduce the NAPI APIs to the **index.d.ts** file in **types/libentry**.

   ```c
   export const ohLocationIsEnabled: () => boolean;
   export const ohLocationStartLocating: () => number;
   export const ohLocationStopLocating: () => number;
   ```

8. Delete deprecated functions from the **Index.ets** file.

   ```js
   .onClick(() => {
       hilog.info(0x0000, 'testTag', 'Test NAPI 2 + 3 = %{public}d', testNapi.add(2, 3));
   })
   ```
