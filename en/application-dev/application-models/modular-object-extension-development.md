# Using ModularObjectExtensionAbility to Implement Modular Objects (C/C++)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=7b06673b258deafa961ffd39d2e26b733c97c0b3 translatedAt=2026-08-25T13:02:49.579Z pushedAt=2026-08-26T03:42:09.615Z -->

Starting from API version 26.0.0, the system provides the ModularObjectExtensionAbility component (for the related C API definitions, see [modular_object_extension_ability.h](../reference/apis-ability-kit/capi-modular-object-extension-ability-h.md)), which allows an application to expose its capabilities to other applications in the form of modular objects. This document describes how to implement the ModularObjectExtensionAbility server and client.

> **NOTE**
>
> For an introduction to modular objects, their basic concepts, and operating mechanisms, refer to [Modular Object Model Overview (C/C++)](./modular-object-extension-overview.md).

## Constraints

### Device Restrictions

The ModularObjectExtensionAbility component currently only supports PC/2-in-1 devices.

### Specification Limits

- When a client connects to the server, the client process must be in the foreground, and the server application must have a running [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) or [UIExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md) instance.

- The number of ModularObjectExtensionAbility instances with the same Ability name running under the same server application cannot exceed 20.

- For the same client process, a maximum of 5 connections can be created for ModularObjectExtensionAbility instances with the same Ability name under the same server application.

- For the same client application, the frequency of calling the [OH_AbilityRuntime_ConnectModularObjectExtensionAbility](../reference/apis-ability-kit/capi-modular-object-extension-manager-h.md#oh_abilityruntime_connectmodularobjectextensionability) API cannot exceed 20 times per second.

## ModularObjectExtensionAbility Configuration

ModularObjectExtensionAbility supports flexible process and thread models and other attribute configurations, which are set through the metadata of the [extensionAbilities](../quick-start/module-configuration-file.md#extensionabilities). If metadata is not configured or is configured with an invalid value, the default value is used.

| Name | Description | Optional Value | Default Value |
| --- | --- | --- | --- |
| launchMode | Launch mode. Determines whether the ModularObjectExtensionAbility can be started across processes. | IN_PROCESS: indicates that the ModularObjectExtensionAbility will be started in the client process. In this mode, the client and the target ability must belong to the same application.<br/>CROSS_PROCESS: indicates that the ModularObjectExtensionAbility can be started across processes. | IN_PROCESS |
| processMode | Process mode. Determines the process sharing policy among multiple ModularObjectExtensionAbility instances. It takes effect only when launchMode is set to CROSS_PROCESS. | BUNDLE: indicates that all ModularObjectExtensionAbility instances under the same application share a process.<br/>TYPE: indicates that ModularObjectExtensionAbility instances with the same ability name share a process.<br/>INSTANCE: indicates that each ModularObjectExtensionAbility instance exclusively occupies a process. | BUNDLE |
| threadMode | Thread mode. Determines the thread on which IPC requests are executed.<br/>**Description:**<br/>You need to use the [OH_AbilityRuntime_ModObjExtensionContext_CreateIPCRemoteStub](../reference/apis-ability-kit/capi-modular-object-extension-context-h.md#oh_abilityruntime_modobjextensioncontext_createipcremotestub) API to create an [OHIPCRemoteStub](../reference/apis-ipc-kit/capi-ohipcparcel-ohipcremotestub.md) for threadMode to take effect. Otherwise, IPC requests will be executed in the IPC worker thread pool. For details, refer to the IPC Stub implementation section in [Implementing the ModularObjectExtensionAbility Server](#implementing-the-modularobjectextensionability-server). | BUNDLE: indicates that all ModularObjectExtensionAbility instances under the same application share a thread.<br/>TYPE: indicates that ModularObjectExtensionAbility instances with the same ability name share a thread.<br/>INSTANCE: indicates that each ModularObjectExtensionAbility instance exclusively occupies a thread. | BUNDLE |
| isDisabled | Whether to disable the ExtensionAbility. | true: disabled. Only the local application is allowed to connect to the ExtensionAbility.<br/>false: not disabled. Other applications are allowed to connect to the ExtensionAbility. | false |

## Implementing the ModularObjectExtensionAbility Server

Create a ModularObjectExtensionAbility component in a DevEco Studio project as follows:

1. In the main directory of the project Module, right-click and choose "New > Directory" to create a directory named cpp. The following files will be created in the cpp directory later:

    ```text
    ├── entry/src/main/cpp/
    │   ├── CMakeLists.txt
    │   ├── icalculator.h          # IPC interface definition
    │   ├── calculator_stub.h       # IPC Stub header file
    │   ├── calculator_stub.cpp     # IPC Stub implementation
    │   └── moe_ability.cpp         # ModularObjectExtensionAbility native implementation, lifecycle registration
    ```

2. Create a CMakeLists.txt file in the cpp directory to configure compilation options, source files, and dependent libraries.

    ```cmake
    cmake_minimum_required(VERSION 3.5.0)
    project(ModularObjectExtensionService)

    set(NATIVERENDER_ROOT_PATH ${CMAKE_CURRENT_SOURCE_DIR})

    if(DEFINED PACKAGE_FIND_FILE)
        include(${PACKAGE_FIND_FILE})
    endif()

    include_directories(${NATIVERENDER_ROOT_PATH}
                        ${NATIVERENDER_ROOT_PATH}/include)

    add_library(entry SHARED
        moe_ability.cpp
        calculator_stub.cpp
    )
    target_link_libraries(entry PUBLIC
        libhilog_ndk.z.so
        libability_runtime.so
        libability_base_want.so
        libipc_capi.so
    )
    ```

3. Register the ModularObjectExtensionAbility in the [module.json5 configuration file](../quick-start/module-configuration-file.md) of the project Module. Set the type tag to "modularObject" and the srcEntry tag to the name of the compiled .so library configured in CMakeLists.txt.

    ```json5
    {
      "module": {
        // ...
        "extensionAbilities": [
          {
            "name": "SampleModularObjectExtAbility",
            "srcEntry": "libentry.so",
            "type": "modularObject",
            "exported": true,
            "metadata": [
              {
                "name": "launchMode",
                "value": "CROSS_PROCESS"
              },
              {
                "name": "processMode",
                "value": "BUNDLE"
              },
              {
                "name": "threadMode",
                "value": "BUNDLE"
              },
              {
                "name": "isDisabled",
                "value": "false"
              }
            ]
          }
        ]
      }
    }
    ```

4. Implement the IPC Stub. Create the icalculator.h, calculator_stub.h, and calculator_stub.cpp files in the cpp directory. The following uses a calculator interface (the Add method) as an example. It is recommended to use the Taihe compiler tool to generate these files. For details, refer to [Using Taihe to Implement IPC Communication for ModularObjectExtensionAbility (C/C++)](./modular-object-extension-ability-taihe.md).

    icalculator.h defines the interface class ICalculator, which contains the interface descriptor, command codes, and method business declarations. Both the server and the client need to include this header file.

    <!-- @[modular_object_extension_icalculator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionService/entry/src/main/cpp/icalculator.h) -->

    ``` C
    class ICalculator {
    public:
        virtual ~ICalculator() = default;
        static const char* GetDescriptor() { return "com.samples.modularobjectextensionservice.ICalculator"; }
    
        enum class IpcCode : uint32_t {
            COMMAND_ADD = 1001,
        };
    
        virtual ErrCode Add(int32_t a, int32_t b, int32_t& result) = 0;
    };
    // ...
    ```

    calculator_stub.h and calculator_stub.cpp inherit the ICalculator interface, are responsible for creating OHIPCRemoteStub, and handle the IPC requests sent by the client.

    <!-- @[modular_object_extension_stub_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionService/entry/src/main/cpp/calculator_stub.h) -->

    ``` C
    class CalculatorStub : public ICalculator {
    public:
        explicit CalculatorStub(OH_AbilityRuntime_ModObjExtensionContextHandle context);
        ~CalculatorStub() override;
    
        OHIPCRemoteStub *GetRemoteStub() const { return remoteStub_; }
    
        static int32_t OnRemoteRequest(uint32_t code, const OHIPCParcel *data, OHIPCParcel *reply, void *userData);
    
        ErrCode Add(int32_t a, int32_t b, int32_t &result) override;
    
    private:
        int32_t HandleAdd(const OHIPCParcel *data, OHIPCParcel *reply);
    
    private:
        OHIPCRemoteStub *remoteStub_ = nullptr;
        OH_AbilityRuntime_ModObjExtensionContextHandle context_ = nullptr;
    };
    // ...
    ```

    <!-- @[modular_object_extension_stub_impl](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionService/entry/src/main/cpp/calculator_stub.cpp) -->

    ``` C++
    #include "calculator_stub.h"
    // ...
    
    CalculatorStub::CalculatorStub(OH_AbilityRuntime_ModObjExtensionContextHandle context)
        : context_(context), remoteStub_(OH_AbilityRuntime_ModObjExtensionContext_CreateIPCRemoteStub(
            context, ICalculator::GetDescriptor(), &CalculatorStub::OnRemoteRequest, nullptr, this)) {}
    
    CalculatorStub::~CalculatorStub()
    {
        if (remoteStub_ != nullptr) {
            OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub(context_, remoteStub_);
            remoteStub_ = nullptr;
        }
    }
    
    int32_t CalculatorStub::OnRemoteRequest(uint32_t code, const OHIPCParcel *data, OHIPCParcel *reply, void *userData)
    {
        // ...
    
        // Dispatch the request.
        switch (static_cast<ICalculator::IpcCode>(code)) {
            case ICalculator::IpcCode::COMMAND_ADD:
                return stub->HandleAdd(data, reply);
            default:
                return OH_IPC_CHECK_PARAM_ERROR;
        }
    }
    
    int32_t CalculatorStub::HandleAdd(const OHIPCParcel *data, OHIPCParcel *reply)
    {
        // Read the input parameters.
        int32_t a = 0;
        if (OH_IPCParcel_ReadInt32(data, &a) != OH_IPC_SUCCESS) {
            return OH_IPC_PARCEL_READ_ERROR;
        }
        int32_t b = 0;
        if (OH_IPCParcel_ReadInt32(data, &b) != OH_IPC_SUCCESS) {
            return OH_IPC_PARCEL_READ_ERROR;
        }
        int32_t result;
        // Call the business function.
        ErrCode errCode = Add(a, b, result);
        // Write errCode and result.
        if (OH_IPCParcel_WriteInt32(reply, errCode) != OH_IPC_SUCCESS) {
            return OH_IPC_PARCEL_WRITE_ERROR;
        }
        if (OH_IPCParcel_WriteInt32(reply, result) != OH_IPC_SUCCESS) {
            return OH_IPC_PARCEL_WRITE_ERROR;
        }
    
        return OH_IPC_SUCCESS;
    }
    
    ErrCode CalculatorStub::Add(int32_t a, int32_t b, int32_t &result)
    {
        // Implement the business logic.
        result = a + b;
        return OH_IPC_SUCCESS;
    }
    ```

5. Create the moe_ability.cpp file in the cpp directory, implement the [OH_AbilityRuntime_OnNativeExtensionCreate](../reference/apis-ability-kit/capi-extension-ability-h.md#oh_abilityruntime_onnativeextensioncreate) entry function, obtain the ModularObjectExtensionAbility instance in this function, and register the lifecycle callbacks. In the OnConnect callback, create CalculatorStub and return the [OHIPCRemoteStub](../reference/apis-ipc-kit/capi-ohipcparcel-ohipcremotestub.md) object.

    <!-- @[modular_object_extension_moe_ability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionService/entry/src/main/cpp/moe_ability.cpp) -->

    ``` C++
    // ...
    
    #include "calculator_stub.h"
    // ...
    
    static std::map<OH_AbilityRuntime_ModObjExtensionInstanceHandle, OH_AbilityRuntime_ModObjExtensionContextHandle>
        g_contextMap;
    static std::map<OH_AbilityRuntime_ModObjExtensionInstanceHandle, CalculatorStub *> g_stubMap;
    
    static void OnCreate(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, AbilityBase_Want *want)
    {
        OH_LOG_INFO(LOG_APP, "OnCreate");
        // Obtain the context and save it.
        OH_AbilityRuntime_ModObjExtensionContextHandle context = NULL;
        AbilityRuntime_ErrorCode err = OH_AbilityRuntime_ModObjExtensionAbility_GetContextFromInstance(instance, &context);
        if (context != NULL) {
            g_contextMap[instance] = context;
        }
    }
    
    static OHIPCRemoteStub *OnConnect(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, AbilityBase_Want *want)
    {
        OH_LOG_INFO(LOG_APP, "OnConnect");
        // Create the Stub and return it.
        OH_AbilityRuntime_ModObjExtensionContextHandle context = g_contextMap.at(instance);
        if (context == nullptr) {
            return nullptr;
        }
        CalculatorStub *stub = new CalculatorStub(context);
        g_stubMap[instance] = stub;
        return stub->GetRemoteStub();
    }
    
    static void OnDisconnect(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance)
    {
        OH_LOG_INFO(LOG_APP, "OnDisconnect");
        // Clean up the Stub when the connection is disconnected.
        CalculatorStub *stub = g_stubMap.at(instance);
        if (stub != nullptr) {
            delete stub;
            g_stubMap.erase(instance);
        }
    }
    
    static void OnDestroy(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance)
    {
        OH_LOG_INFO(LOG_APP, "OnDestroy");
        // Clean up the context when the instance is destroyed.
        g_contextMap.erase(instance);
    }
    
    EXTERN_C_START
    void OH_AbilityRuntime_OnNativeExtensionCreate(AbilityRuntime_ExtensionInstanceHandle handle, const char *abilityName)
    {
        // Obtain the instance.
        OH_AbilityRuntime_ModObjExtensionInstanceHandle instance = NULL;
        AbilityRuntime_ErrorCode err = OH_AbilityRuntime_ModObjExtensionAbility_GetInstanceFromBase(handle, &instance);
        if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
            OH_LOG_ERROR(LOG_APP, "GetInstanceFromBase err:%{public}d", err);
            return;
        }
        // Register the callback function.
        OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnCreateFunc(instance, OnCreate);
        OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnConnectFunc(instance, OnConnect);
        OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnDisconnectFunc(instance, OnDisconnect);
        OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnDestroyFunc(instance, OnDestroy);
    }
    EXTERN_C_END
    ```

## Implementing the ModularObjectExtensionAbility Client

Describes how a client application connects to ModularObjectExtensionAbility and performs communication with the server. The client can make static calls through a Proxy object or dynamic calls through ModularObjectDispatcher.

### Connecting to a ModularObjectExtensionAbility

<!-- @[modular_object_extension_connect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionClient/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static OHIPCRemoteProxy *g_remoteProxy = NULL;
static int64_t g_connectionId = -1;

static void OnConnectCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityBase_Element *element,
                              OHIPCRemoteProxy *proxy)
{
    OH_LOG_INFO(LOG_APP, "OnConnectCallback");
    g_remoteProxy = proxy;
}

static void OnDisconnectCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityBase_Element *element)
{
    OH_LOG_INFO(LOG_APP, "OnDisconnectCallback");
    g_remoteProxy = NULL;
}

static void OnFailedCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityRuntime_ErrorCode code)
{
    OH_LOG_ERROR(LOG_APP, "OnFailedCallback, code: %{public}d", code);
}

static napi_value TestConnect(napi_env env, napi_callback_info info)
{
    OH_LOG_INFO(LOG_APP, "TestConnect");
    // Create a Want.
    AbilityBase_Element element = {.bundleName = "com.samples.modularobjectextensionservice",
                                   .moduleName = "entry",
                                   .abilityName = "SampleModularObjectExtAbility"};
    AbilityBase_Want *want = OH_AbilityBase_CreateWant(element);
    if (want == NULL) {
        OH_LOG_ERROR(LOG_APP, "CreateWant failed");
        return nullptr;
    }

    // Create ConnectOptions and register the callback.
    OH_AbilityRuntime_ConnectOptions *options = OH_AbilityRuntime_CreateConnectOptions();
    OH_AbilityRuntime_ConnectOptions_SetOnConnectCallback(options, OnConnectCallback);
    OH_AbilityRuntime_ConnectOptions_SetOnDisconnectCallback(options, OnDisconnectCallback);
    OH_AbilityRuntime_ConnectOptions_SetOnFailedCallback(options, OnFailedCallback);

    // Initiate the connection.
    int64_t connectionId = -1;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_ConnectModularObjectExtensionAbility(want, options, &connectionId);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        OH_LOG_ERROR(LOG_APP, "ConnectModularObjectExtensionAbility err:%{public}d", err);
        return nullptr;
    }
    OH_LOG_INFO(LOG_APP, "ConnectModularObjectExtensionAbility id:%{public}ld", connectionId);
    // Save the connection ID for subsequent disconnection operations.
    g_connectionId = connectionId;
    OH_AbilityBase_DestroyWant(want);
    return nullptr;
}
```

### Communication with the Server Through Proxy

1. Create the calculator_proxy.h and calculator_proxy.cpp files to implement the CalculatorProxy class. CalculatorProxy inherits the ICalculator interface provided by the server and encapsulates OHIPCRemoteProxy. In the Add method, serialize the parameters and send them to the server through OHIPCRemoteProxy, then receive the result returned by the server and deserialize it. It is recommended to use the Taihe compiler tool for generation. For details, refer to [Implementing IPC Communication for ModularObjectExtensionAbility with Taihe (C/C++)](./modular-object-extension-ability-taihe.md).

    <!-- @[modular_object_extension_proxy_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionClient/entry/src/main/cpp/calculator_proxy.h) -->

    ``` C
    class CalculatorProxy : public ICalculator {
    public:
        explicit CalculatorProxy(OHIPCRemoteProxy* remote) : remote_(remote) {}
        ~CalculatorProxy() override = default;
    
        OHIPCRemoteProxy* GetRemoteProxy() const
        {
            return remote_;
        }
    
        ErrCode Add(int32_t a, int32_t b, int32_t& result) override;
    
    private:
        OHIPCRemoteProxy* remote_ = nullptr;
    };
    // ...
    ```

    <!-- @[modular_object_extension_proxy_impl](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionClient/entry/src/main/cpp/calculator_proxy.cpp) -->

    ``` C++
    #include "calculator_proxy.h"
    // ...
    
    ErrCode CalculatorProxy::Add(int32_t a, int32_t b, int32_t& result)
    {
        // ...
        // Write the parameters.
        if (OH_IPCParcel_WriteInt32(parcelData.get(), a) != OH_IPC_SUCCESS) {
            return OH_IPC_PARCEL_WRITE_ERROR;
        }
        if (OH_IPCParcel_WriteInt32(parcelData.get(), b) != OH_IPC_SUCCESS) {
            return OH_IPC_PARCEL_WRITE_ERROR;
        }
        // Send the request and wait for the result returned by the server.
        OH_IPC_MessageOption option = { OH_IPC_REQUEST_MODE_SYNC, 0 };
        int32_t transportErr = OH_IPCRemoteProxy_SendRequest(
            remote_,
            static_cast<uint32_t>(ICalculator::IpcCode::COMMAND_ADD),
            parcelData.get(),
            parcelReply.get(),
            &option);
        if (transportErr != OH_IPC_SUCCESS) {
            return transportErr;
        }
    
        // Read the result returned by the server.
        int32_t errCode = OH_IPC_SUCCESS;
        if (OH_IPCParcel_ReadInt32(parcelReply.get(), &errCode) != OH_IPC_SUCCESS) {
            return OH_IPC_PARCEL_READ_ERROR;
        }
    
        int32_t resultValue = 0;
        if (OH_IPCParcel_ReadInt32(parcelReply.get(), &resultValue) != OH_IPC_SUCCESS) {
            return OH_IPC_PARCEL_READ_ERROR;
        }
        result = resultValue;
    
        return errCode;
    }
    ```

2. Create a CalculatorProxy object through g_remoteProxy, and call the Add method to communicate with the server to obtain the result.

    <!-- @[modular_object_extension_test_add](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionClient/entry/src/main/cpp/napi_init.cpp) -->

    ``` C++
    static OHIPCRemoteProxy *g_remoteProxy = NULL;
    // ...
    
    static napi_value TestAdd(napi_env env, napi_callback_info info)
    {
        OH_LOG_INFO(LOG_APP, "TestAdd");
        if (g_remoteProxy == NULL) {
            OH_LOG_ERROR(LOG_APP, "Remote proxy is null, not connected");
            return nullptr;
        }
        CalculatorProxy proxy(g_remoteProxy);
        int32_t result = 0;
        ErrCode err = proxy.Add(10, 20, result);
        if (err != OH_IPC_SUCCESS) {
            OH_LOG_ERROR(LOG_APP, "CalculatorProxy::Add err:%{public}d", err);
            return nullptr;
        }
        OH_LOG_INFO(LOG_APP, "CalculatorProxy::Add(10, 20) result:%{public}d", result);
        return nullptr;
    }
    ```

### Communication with the Server Through ModularObjectDispatcher

In addition to the static call method based on Proxy described above, the client can also implement dynamic calls through ModularObjectDispatcher. The static call method requires depending on the server's interface definition at compile time, while the dynamic call method allows the client to query the server's type library metadata at runtime and initiate calls by method name, without compile-time binding.

Dynamic calls are suitable for scenarios where the interface can only be determined at runtime, such as general-purpose script engines, automated testing frameworks, and cross-version gateway services.

### Disconnecting from a ModularObjectExtensionAbility

The client disconnects through [OH_AbilityRuntime_DisconnectModularObjectExtensionAbility](../reference/apis-ability-kit/capi-modular-object-extension-manager-h.md#oh_abilityruntime_disconnectmodularobjectextensionability). After the disconnection succeeds, the system triggers the [OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback](../reference/apis-ability-kit/capi-connect-options-h.md#oh_abilityruntime_connectoptions_ondisconnectcallback) callback, in which the saved g_remoteProxy is cleared.

<!-- @[modular_object_extension_disconnect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionClient/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static OHIPCRemoteProxy *g_remoteProxy = NULL;
static int64_t g_connectionId = -1;

// ...

static void OnDisconnectCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityBase_Element *element)
{
    OH_LOG_INFO(LOG_APP, "OnDisconnectCallback");
    g_remoteProxy = NULL;
}

// ...

static napi_value TestDisconnect(napi_env env, napi_callback_info info)
{
    OH_LOG_INFO(LOG_APP, "TestDisconnect");
    if (g_connectionId == -1) {
        OH_LOG_ERROR(LOG_APP, "Not connected");
        return nullptr;
    }
    AbilityRuntime_ErrorCode err =
        OH_AbilityRuntime_DisconnectModularObjectExtensionAbility(g_connectionId);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        OH_LOG_ERROR(LOG_APP, "DisconnectModularObjectExtensionAbility err:%{public}d", err);
        return nullptr;
    }
    OH_LOG_INFO(LOG_APP, "DisconnectModularObjectExtensionAbility success");
    g_connectionId = -1;
    g_remoteProxy = NULL;
    return nullptr;
}
```