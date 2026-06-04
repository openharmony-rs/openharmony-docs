# Gewu Development

<!--Kit: Kernel Enhance Kit-->
<!--Subsystem: Kernel-->
<!--Owner: @gatieme-->
<!--Designer: @tanyihua-->
<!--Tester: @panny060-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T06:18:44.414Z pushedAt=2026-06-03T09:36:44.301Z -->

## When to Use

Supported from API version 20. On-device inference scenarios offer advantages such as ensuring user data privacy, low deployment costs, low latency, and high availability unaffected by network conditions. However, compared to cloud-side inference, on-device inference also faces greater challenges because on-device devices have limited memory resources, limited computing power, are sensitive to power consumption, and must ensure a smooth user experience without lag when running on-device inference services. To address these challenges of on-device inference, the Gewu service provides QoS-aware inference acceleration and resource management optimization capabilities. This document will guide developers on using the Gewu interface.

## Available APIs

### Error Codes

The `OH_QoS_GewuErrorCode` enumeration serves as the error code type for Gewu. The meaning of error codes returned by each function interface is described in the interface description.

### Session Handle

The session handle is used for session management. When a session is successfully created via `OH_QoS_GewuSession`, a session handle is obtained, which can be used to submit/abort requests and destroy the session.

```C
typedef unsigned int OH_QoS_GewuSession;
```

### Request Handle

The request handle is used for request management. When a request is successfully submitted via `OH_QoS_GewuSubmitRequest`, a request handle is obtained, which can be used to abort the request.

```C
typedef unsigned int OH_QoS_GewuRequest;
```

### Functions

| Function Name              | Description                |
| --------------------------- | -------------------------- |
| `OH_QoS_GewuCreateSession`  | Create session             |
| `OH_QoS_GewuDestroySession` | Destroy session            |
| `OH_QoS_GewuSubmitRequest`  | Submit request             |
| `OH_QoS_GewuAbortRequest`   | Abort request              |

**`OH_QoS_GewuCreateSession`**

**Description**

The `OH_QoS_GewuCreateSession` interface is used to create a session.

This interface processes requests asynchronously, meaning it only initiates session creation and does not wait for session resource allocation or model loading to complete before returning. Gewu optimizes on-device inference resource management, enabling dynamic on-demand resource loading.

The lifecycle of a session object begins when the `OH_QoS_GewuCreateSession` function returns and ends when `OH_QoS_GewuDestroySession` is called.

**Declaration**

```C
typedef struct {
    OH_QoS_GewuSession session;
    OH_QoS_GewuErrorCode error;
} OH_QoS_GewuCreateSessionResult;

OH_QoS_GewuCreateSessionResult OH_QoS_GewuCreateSession(const char* attributes);
```

**Parameters**

* The `const char* attributes` parameter represents a JSON string of session attributes. This JSON string supports the following fields:

    * "model": string representing the path of the model used by the session.

Example of `attributes` json string:

```json
{
    "model": "/data/storage/el2/base/files/qwen2/"
}
```

**Return Value**

If the session is created successfully, the `error` in the return value `OH_QoS_GewuCreateSessionResult` is `OH_QOS_GEWU_OK`, and `session` is the created session handle.

If the session creation fails, the `error` in the return value `OH_QoS_GewuCreateSessionResult` indicates the cause of the error, where `OH_QOS_GEWU_NOMEM` means there is insufficient memory to create the session.

**`OH_QoS_GewuDestroySession`**

**Description**

The `OH_QoS_GewuDestroySession` interface is used to destroy a session.

It is recommended that users wait until all requests have been completed or aborted before calling this interface to destroy the session. If there are still ongoing requests when this interface is called, those requests will be aborted and the user will no longer receive replies. Note that after calling this interface, the session object can no longer be used.

**Declaration**

```C
OH_QoS_GewuErrorCode OH_QoS_GewuDestroySession(OH_QoS_GewuSession session);
```

**Parameters**

* The `OH_QoS_GewuSession session` parameter is the handle of the session to be destroyed.

**Return Value**

If the session is destroyed successfully, the return value is `OH_QOS_GEWU_OK`.

If the session destruction fails, the return value indicates the error cause, where `OH_QOS_GEWU_NOENT` means the session cannot be found.

**`OH_QoS_GewuSubmitRequest`**

**Description**

The `OH_QoS_GewuSubmitRequest` interface is used to submit a request. This interface executes the request asynchronously, meaning it only initiates the request and does not directly return the result. When this interface returns, the request may not have started execution yet. The result of the request is returned to the user via a user-provided callback.

**Declaration**

```C
typedef struct {
    OH_QoS_GewuRequest request;
    OH_QoS_GewuErrorCode error;
} OH_QoS_GewuSubmitRequestResult;

typedef void (*OH_QoS_GewuOnResponse)(void* context, const char* response);

OH_QoS_GewuSubmitRequestResult OH_QoS_GewuSubmitRequest(OH_QoS_GewuSession session, const char* request,
    OH_QoS_GewuOnResponse callback, void* context);
```

**Parameters**

The parameters of the `OH_QoS_GewuSubmitRequest` function are as follows:

* `OH_QoS_GewuSession session` parameter is the session handle, indicating which session the request is to be submitted to.

* `const char* request` parameter is the JSON string of the request, supporting the following fields:

    * "messages": array. An array representing messages, where each element supports the following fields:

        * "role": string. The role type of the message. "developer" indicates instructions provided by the developer or system, "user" indicates user input, and "assistant" indicates the model-generated result.

        * "content": string. Message content.

    * "stream": boolean or null. Whether to enable streaming inference. Defaults to non-streaming.

* The `OH_QoS_GewuOnResponse callback` parameter is the callback function for the request.

* The `void* context` parameter is a user-provided context pointer used to pass to the callback function. In typical usage, user code can use this parameter to find the request corresponding to the received response, thereby performing appropriate processing.

In addition, the parameters of the `OH_QoS_GewuOnResponse` callback function are as follows:

* The `void* context` parameter is the `context` pointer passed in when calling `OH_QoS_GewuSubmitRequest`.

* The `const char* response` parameter is the response JSON string, which contains the following fields:

    * "message": The response message, which contains the following fields:

        * "role": string. The role type of the message, which should be "assistant".

        * "content": string. The message content.

    * "finish_reason": string or null. The reason for stopping. Possible values are as follows:

        * null: Indicates no stop. In streaming inference, there will be multiple responses, and only the last response has a non-null "finish_reason". In non-streaming inference, there is only one response, and "finish_reason" is non-null.

        * "stop": Normal stop.

        * "abort": The user actively aborted early.

        * "length": The number of tokens exceeded the limit.

**Return Value**

If the request is submitted successfully, `error` in the return value `OH_QoS_GewuSubmitRequestResult` is `OH_QOS_GEWU_OK`, and `request` is the request handle.

If the request submission fails, `error` in the return value `OH_QoS_GewuSubmitRequestResult` indicates the cause of the error, where `OH_QOS_GEWU_NOMEM` means there is insufficient memory to process the request.

**`OH_QoS_GewuAbortRequest`**

**Description**

The `OH_QoS_GewuAbortRequest` interface is used to abort a request prematurely.

Under normal circumstances, after calling the `OH_QoS_GewuSubmitRequest` interface to submit a request, the user waits until the inference is complete (i.e., a reply with a non-empty `"finish_reason"` is received) and does not need to call the `OH_QoS_GewuAbortRequest` interface.

The `OH_QoS_GewuAbortRequest` interface only needs to be called when the user wishes to abort an inference request prematurely.

After this function is successfully called, the user will no longer receive replies for this request, and the request handle can no longer be used.

**Declaration**

```C
OH_QoS_GewuErrorCode OH_QoS_GewuAbortRequest(OH_QoS_GewuSession session, OH_QoS_GewuRequest request);
```

**Parameters**

* `OH_QoS_GewuSession session` parameter is the handle of the session to which the request belongs.

* `OH_QoS_GewuRequest request` parameter is the handle of the request to be aborted.

**Return Value**

If the request is aborted successfully, the return value is `OH_QOS_GEWU_OK`.

If the request abort fails, the return value indicates the error cause, where `OH_QOS_GEWU_NOENT` indicates that the request was not found.

## Example

The example is as follows:

```CPP
#include <future>
#define LOG_TAG "DEMO"
#include <hilog/log.h>
#include <nlohmann/json.hpp>
#include <qos/qos.h>
#include <string>

#define DEMO_LOGD(fmt, ...) OH_LOG_DEBUG(LOG_APP, fmt, ##__VA_ARGS__)
#define DEMO_LOGI(fmt, ...) OH_LOG_INFO(LOG_APP, fmt, ##__VA_ARGS__)
#define DEMO_LOGW(fmt, ...) OH_LOG_WARN(LOG_APP, fmt, ##__VA_ARGS__)
#define DEMO_LOGE(fmt, ...) OH_LOG_ERROR(LOG_APP, fmt, ##__VA_ARGS__)

using json = nlohmann::json;

/* Used to save the chat state */
struct ChatContext {
public:
    ChatContext()
    {
        future = promise.get_future();
    }

    void Join()
    {
        assert(future.valid());
        std::string stopReasonStr = future.get();
        DEMO_LOGI("stopReasonStr=%s", stopReasonStr.c_str());
    }

    std::promise<std::string> promise;
    std::future<std::string> future;
    std::string responseContent;
    bool earlyAbort = false;
};

/* Callback function when an inference result is received */
void OnChatResponse(void *context, const char *response)
{
    ChatContext *chatContext = static_cast<ChatContext *>(context);
    if (chatContext->earlyAbort) {
        DEMO_LOGD("ignore response after early abort");
        return;
    }
    try {
        json responseJson = json::parse(response);
        chatContext->responseContent += responseJson.at("message").at("content").get<std::string>();
        json finishReasonJson = responseJson.at("finish_reason");
        if (!finishReasonJson.is_null()) {
            /* finish */
            std::string finishReasonStr = finishReasonJson.get<std::string>();
            chatContext->promise.set_value(finishReasonStr);
        } else if (chatContext->responseContent.find("\n") != std::string::npos) {
            /* customized stop */
            chatContext->promise.set_value("customized");
            chatContext->earlyAbort = true;
        } else {
            /* continue */
            ;
        }
    } catch (json::exception &e) {
        DEMO_LOGE("failed to parse response: %s", e.what());
    }
}

int Demo(void)
{
    DEMO_LOGI("Demo starts");
    json attrJson = {
        /* Model file location, modify according to actual situation */
        {"model", "/data/storage/el2/base/files/qwen2-awq"},
    };
    std::string attrStr = attrJson.dump(4);

    /* Create session */
    OH_QoS_GewuCreateSessionResult createResult = OH_QoS_GewuCreateSession(attrStr.c_str());
    if (createResult.error != OH_QOS_GEWU_OK) {
        DEMO_LOGE("failed to create session, error=%d", (int)createResult.error);
        return -1;
    }
    OH_QoS_GewuSession session = createResult.session;

    /* Create and submit request */
    ChatContext context;
    json requestJson = {
        {"messages", json::array({
            {{"role", "developer"}, {"content", "You are a helpful assistant"}},
            {{"role", "user"}, {"content", "What is LLM?"}},
        })},
        {"stream", true},
    };
    std::string requestStr = requestJson.dump(4);
    OH_QoS_GewuSubmitRequestResult submitResult = OH_QoS_GewuSubmitRequest(session, requestStr.c_str(),
                                                                           OnChatResponse, &context);
    if (submitResult.error != OH_QOS_GEWU_OK) {
        DEMO_LOGE("failed to submit request, error=%d", (int)submitResult.error);
        return -1;
    }
    OH_QoS_GewuRequest request = submitResult.request;
    context.Join();

    /* Abort request early */
    if (context.earlyAbort) {
        OH_QoS_GewuErrorCode error = OH_QoS_GewuAbortRequest(session, request);
        if (error != OH_QOS_GEWU_OK) {
            DEMO_LOGE("failed to abort request, error=%d", (int)error);
            return -1;
        }
    }

    /* Print result */
    DEMO_LOGI("response: %s", context.responseContent.c_str());

    /* Destroy Session */
    OH_QoS_GewuErrorCode error = OH_QoS_GewuDestroySession(session);
    if (error != OH_QOS_GEWU_OK) {
        DEMO_LOGE("failed to destroy session, error=%d", (int)error);
        return -1;
    }
    return 0;
}
```

> **NOTE**
> 
> In the demo code, the third-party library nlohmann/json is used to simplify the parsing and construction of JSON data. nlohmann/json is a modern C++ JSON library that provides an intuitive and concise way to handle JSON data.
> Its design philosophy is to make JSON operations as natural as using STL containers.
> Developers can download the json.hpp file and place it in the project's include directory to use it, without the need for additional library file linking.