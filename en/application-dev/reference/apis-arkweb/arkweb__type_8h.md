# arkweb_type.h


## Overview

Defines the native common types of ArkWeb.

**Library**: libohweb.so

**File to include**: <web/arkweb_type.h>

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Related module**: [Web](_web.md)


## Summary


### Structs

| Name| Description| 
| -------- | -------- |
| struct&nbsp;&nbsp;[ArkWeb_JavaScriptBridgeData](_ark_web___java_script_bridge_data.md) | Defines the JavaScript Bridge data. | 
| struct&nbsp;&nbsp;[ArkWeb_JavaScriptObject](_ark_web___java_script_object.md) | Defines a JavaScript object to be injected. | 
| struct&nbsp;&nbsp;[ArkWeb_ProxyMethod](_ark_web___proxy_method.md) | Defines a proxy method to be injected. | 
| struct&nbsp;&nbsp;[ArkWeb_ProxyMethodWithResult](_ark_web___proxy_method_with_result.md) | Defines a proxy method with the result to be injected. | 
| struct&nbsp;&nbsp;[ArkWeb_ProxyObject](_ark_web___proxy_object.md) | Defines a proxy object to be injected. | 
| struct&nbsp;&nbsp;[ArkWeb_ProxyObjectWithResult](_ark_web___proxy_object_with_result.md) | Defines a proxy object with the result to be injected. | 
| struct&nbsp;&nbsp;[ArkWeb_ControllerAPI](_ark_web___controller_a_p_i.md) | Defines a controller API. Before calling the API, you are advised to use **ARKWEB_MEMBER_MISSING** to check whether the function struct has the corresponding pointer to avoid crash caused by mismatch between the SDK and the device ROM. | 
| struct&nbsp;&nbsp;[ArkWeb_ComponentAPI](_ark_web___component_a_p_i.md) | Defines a component API. | 
| struct&nbsp;&nbsp;[ArkWeb_WebMessagePortAPI](_ark_web___web_message_port_a_p_i.md) | Defines a native API struct of the post message. Before calling the API, you are advised to use **ARKWEB_MEMBER_MISSING** to check whether the function struct has the corresponding pointer to avoid crash caused by mismatch between the SDK and the device ROM. | 
| struct&nbsp;&nbsp;[ArkWeb_WebMessageAPI](_ark_web___web_message_a_p_i.md) | Defines a native API struct of the post message data. Before calling the API, you are advised to use **ARKWEB_MEMBER_MISSING** to check whether the function struct has the corresponding pointer to avoid crash caused by mismatch between the SDK and the device ROM. | 
| struct&nbsp;&nbsp;[ArkWeb_CookieManagerAPI](_ark_web___cookie_manager_a_p_i.md) | Defines the CookieManager API of ArkWeb. Before calling the API, you are advised to use **ARKWEB_MEMBER_MISSING** to check whether the function struct has the corresponding pointer to avoid crash caused by mismatch between the SDK and the device ROM. | 
| struct&nbsp;&nbsp;[ArkWeb_JavaScriptValueAPI](_ark_web___java_script_value_a_p_i.md) | Defines the JavaScriptValue API of ArkWeb. Before calling the API, you are advised to use **ARKWEB_MEMBER_MISSING** to check whether the function struct has the corresponding pointer to avoid crash caused by mismatch between the SDK and the device ROM. | 


### Macros

| Name| Description| 
| -------- | -------- |
| [ARKWEB_MEMBER_EXISTS](_web.md#arkweb_member_exists)(s, f)&nbsp;&nbsp;&nbsp;&nbsp;((intptr_t) &amp; ((s)-&gt;f) - (intptr_t)(s) + sizeof((s)-&gt;f) &lt;= \*reinterpret_cast&lt;size_t\*&gt;(s)) | Whether a member variable exists in the struct. | 
| [ARKWEB_MEMBER_MISSING](_web.md#arkweb_member_missing)(s, f)&nbsp;&nbsp;&nbsp;(\![ARKWEB_MEMBER_EXISTS](_web.md#arkweb_member_exists)(s, f) \|\| !((s)-&gt;f)) | If the member variable exists in the struct, **false** is returned. Otherwise, **true** is returned. | 


### Types

| Name| Description| 
| -------- | -------- |
| typedef enum [ArkWeb_WebMessageType](_web.md#arkweb_webmessagetype) [ArkWeb_WebMessageType](_web.md#arkweb_webmessagetype) | Defines an enum for the data types of post message. | 
| typedef enum [ArkWeb_JavaScriptValueType](_web.md#arkweb_javascriptvaluetype) [ArkWeb_JavaScriptValueType](_web.md#arkweb_javascriptvaluetype) | Defines an enum for the JavaScript data types. | 
| typedef struct ArkWeb_WebMessage \* [ArkWeb_WebMessagePtr](_web.md#arkweb_webmessageptr) | Defines a struct for the pointer to the struct of post message data. | 
| typedef struct ArkWeb_JavaScriptValue \* [ArkWeb_JavaScriptValuePtr](_web.md#arkweb_javascriptvalueptr) | Defines a struct for the pointer to the JavaScript data struct. | 
| typedef void(\* [ArkWeb_OnJavaScriptCallback](_web.md#arkweb_onjavascriptcallback)) (const char \*webTag, const [ArkWeb_JavaScriptBridgeData](_ark_web___java_script_bridge_data.md) \*data, void \*userData) | Defines a callback used when the injected JavaScript is executed. | 
| typedef void(\* [ArkWeb_OnJavaScriptProxyCallback](_web.md#arkweb_onjavascriptproxycallback)) (const char \*webTag, const [ArkWeb_JavaScriptBridgeData](_ark_web___java_script_bridge_data.md) \*dataArray, size_t arraySize, void \*userData) | Defines a callback used when the proxy method is executed. | 
| typedef [ArkWeb_JavaScriptValuePtr](_web.md#arkweb_javascriptvalueptr)(\* [ArkWeb_OnJavaScriptProxyCallbackWithResult](_web.md#arkweb_onjavascriptproxycallbackwithresult)) (const char \*webTag, const [ArkWeb_JavaScriptBridgeData](_ark_web___java_script_bridge_data.md) \*dataArray, size_t arraySize, void \*userData) | Defines a callback used when the proxy method is executed. | 
| typedef void(\* [ArkWeb_OnComponentCallback](_web.md#arkweb_oncomponentcallback)) (const char \*webTag, void \*userData) | Defines a callback used to return component event notification. | 
| typedef struct ArkWeb_WebMessagePort \* [ArkWeb_WebMessagePortPtr](_web.md#arkweb_webmessageportptr) | Defines a struct for the pointer to the struct of post message port. | 
| typedef void(\* [ArkWeb_OnMessageEventHandler](_web.md#arkweb_onmessageeventhandler)) (const char \*webTag, const [ArkWeb_WebMessagePortPtr](_web.md#arkweb_webmessageportptr) port, const [ArkWeb_WebMessagePtr](_web.md#arkweb_webmessageptr) message, void \*userData) | Defines a callback used to process the post message data sent by the HTML page. | 


### Enums

| Name| Description| 
| -------- | -------- |
| [ArkWeb_WebMessageType](_web.md#arkweb_webmessagetype) { [ARKWEB_NONE](_web.md) = 0, [ARKWEB_STRING](_web.md), [ARKWEB_BUFFER](_web.md) } | Enumerates the data types of post message. | 
| [ArkWeb_JavaScriptValueType](_web.md#arkweb_javascriptvaluetype) { [ARKWEB_JAVASCRIPT_NONE](_web.md) = 0, [ARKWEB_JAVASCRIPT_STRING](_web.md), [ARKWEB_JAVASCRIPT_BOOL](_web.md) } | Enumerates the JavaScript data types. | 
