# Listening for Component Events
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->


The NDK API provides a way to listen for UI component events through listener functions. First, you can use the [addNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addnodeeventreceiver) function to add an event listener for the component, which will listen for all events that occur on that component, such as click events and focus events. Then, you can use the [registerNodeEvent](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) function to declare which events of the component need to be listened for. The range of events supported by the NDK API is defined through the [ArkUI_NodeEventType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype) enum.


> **NOTE**
> - Event registration requires the declaration of [addNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addnodeeventreceiver) listener registration and [registerNodeEvent](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent) event types. The listener can only listen for declared events.
> 
> - Pay attention to the logic of event deregistration. For example, before the component is destroyed, call [removeNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#removenodeeventreceiver) to remove the event listener and [unregisterNodeEvent](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#unregisternodeevent) to notify the ArkUI framework that the listened events no longer need to be listened for.
> 
> - [addNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addnodeeventreceiver) can add multiple function pointers, each of which is triggered when the corresponding event occurs. To remove a listener, the corresponding [removeNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#removenodeeventreceiver) function must be called with the exact function pointer used for adding the listener.
> 
> - [registerNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver) is a global event listener function. Unlike [addNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addnodeeventreceiver), [registerNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeeventreceiver) can listen for the event triggers of all native components, but it can only accept a single function pointer. If it is called multiple times, only the last function pointer provided will be used for callbacks. To release the listener, use the [unregisterNodeEventReceiver](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#unregisternodeeventreceiver) function.


The following example is based on the [Integrating with ArkTS Pages](ndk-access-the-arkts-page.md) section, supplementing related event listening. For the complete sample code, see [Sample Code](ndk-listen-to-component-events.md#sample-code).


- Event registration and deregistration

  Bind event handlers to nodes using **addNodeEventReceiver**, and then register specific events with **registerNodeEvent**.

  > **NOTE**
  > 
  > The **ArkUI_NodeEvent* event** parameter in event callbacks is only valid during the callback execution. Do not cache this pointer or process it asynchronously.

  ```
  ArkUI_NativeNodeAPI_1 *nodeAPI = nullptr;
  OH_ArkUI_GetModuleInterface(ARKUI_NATIVE_NODE, ArkUI_NativeNodeAPI_1, nodeAPI);
  void NodeEventReceiver(ArkUI_NodeEvent *event) {
    // Handle specific event types, such as NODE_ON_CLICK_EVENT.
  };
  auto button = nodeAPI->createNode(ARKUI_NODE_BUTTON);
  nodeAPI->addNodeEventReceiver(button, NodeEventReceiver);
  nodeAPI->registerNodeEvent(button, NODE_ON_CLICK_EVENT, 0, nullptr);
  ```
  For details about event types, see [ArkUI_NodeEventType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype).

  Deregister events using **unregisterNodeEvent** and remove handlers with **removeNodeEventReceiver**.

  ```
  nodeAPI->unregisterNodeEvent(button, NODE_ON_CLICK_EVENT);
  nodeAPI->removeNodeEventReceiver(button, NodeEventReceiver);
  ```

- Global event listening

  Register a global event handler with **registerNodeEventReceiver** for centralized event processing. Release it with **unregisterNodeEventReceiver** when it is no longer needed.

  ```cpp
  nodeAPI->registerNodeEventReceiver([](ArkUI_NodeEvent *event){
    auto *inputEvent = OH_ArkUI_NodeEvent_GetInputEvent(event);
    auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
    switch(eventType){
        case NODE_ON_CLICK_EVENT: {
            // Handle click events.
        }
        default: {
            break;
        }
    }
  })
  nodeAPI->unregisterNodeEventReceiver();
  ```

- Event information retrieval

  Use [OH_ArkUI_NodeEvent_GetInputEvent()](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeevent_getinputevent) to obtain input event objects for interaction-related component events (such as NODE_ON_CLICK_EVENT and NODE_TOUCH_EVENT). Then, you can call APIs such as [OH_ArkUI_PointerEvent_GetDisplayX()](../reference/apis-arkui/capi-ui-input-event-h.md#oh_arkui_pointerevent_getdisplayx), [OH_ArkUI_PointerEvent_GetDisplayXByIndex()](../reference/apis-arkui/capi-ui-input-event-h.md#oh_arkui_pointerevent_getdisplayxbyindex), [OH_ArkUI_UIInputEvent_GetAction()](../reference/apis-arkui/capi-ui-input-event-h.md#oh_arkui_uiinputevent_getaction), and [OH_ArkUI_UIInputEvent_GetEventTime()](../reference/apis-arkui/capi-ui-input-event-h.md#oh_arkui_uiinputevent_geteventtime) to obtain more information from the basic event. Applications can implement differentiated interaction logic during gesture event execution based on the obtained information.

  ```cpp
  // Register the click event.
  const unsigned int LOG_PRINT_DOMAIN = 0xFF00;
  nodeAPI->registerNodeEvent(button, NODE_ON_CLICK_EVENT, 0, nullptr);
  // Set a global component event listener.
  nodeAPI->registerNodeEventReceiver([](ArkUI_NodeEvent *event) {
      // Obtain the basic event object from the component event.
      auto *inputEvent = OH_ArkUI_NodeEvent_GetInputEvent(event);
      // Obtain the event type from the component event.
      auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
      OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "eventInfo", "inputEvent = %{public}p", inputEvent);
      OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "eventInfo", "eventType = %{public}d", eventType);
      auto componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
      // Obtain the numerical data from the component event.
      OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "eventInfo", "componentEvent = %{public}p",
                    componentEvent);
      // Obtain the component object that triggers the event.
      auto nodeHandle = OH_ArkUI_NodeEvent_GetNodeHandle(event);
      OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "eventInfo", "nodeHandle = %{public}p", nodeHandle);
      // Differentiate event types and handle them accordingly. Other event information APIs follow similar usage patterns.
      switch (eventType) {
      case NODE_ON_CLICK_EVENT: {
          // Perform operations when the click event is triggered. Obtain event information from the base input event.
          auto x = OH_ArkUI_PointerEvent_GetX(inputEvent);
          auto y = OH_ArkUI_PointerEvent_GetY(inputEvent);
          auto displayX = OH_ArkUI_PointerEvent_GetDisplayX(inputEvent);
          auto displayY = OH_ArkUI_PointerEvent_GetDisplayY(inputEvent);
          auto windowX = OH_ArkUI_PointerEvent_GetWindowX(inputEvent);
          auto windowY = OH_ArkUI_PointerEvent_GetWindowY(inputEvent);
          auto pointerCount = OH_ArkUI_PointerEvent_GetPointerCount(inputEvent);
          auto xByIndex = OH_ArkUI_PointerEvent_GetXByIndex(inputEvent, 0);
          auto yByIndex = OH_ArkUI_PointerEvent_GetYByIndex(inputEvent, 0);
          auto displayXByIndex = OH_ArkUI_PointerEvent_GetDisplayXByIndex(inputEvent, 0);
          auto displayYByIndex = OH_ArkUI_PointerEvent_GetDisplayYByIndex(inputEvent, 0);
          auto windowXByIndex = OH_ArkUI_PointerEvent_GetWindowXByIndex(inputEvent, 0);
          auto windowYByIndex = OH_ArkUI_PointerEvent_GetWindowYByIndex(inputEvent, 0);
          auto pointerId = OH_ArkUI_PointerEvent_GetPointerId(inputEvent, 0);
          auto pressure = OH_ArkUI_PointerEvent_GetPressure(inputEvent, 0);
          auto action = OH_ArkUI_UIInputEvent_GetAction(inputEvent);
          auto eventTime = OH_ArkUI_UIInputEvent_GetEventTime(inputEvent);
          auto sourceType = OH_ArkUI_UIInputEvent_GetSourceType(inputEvent);
          auto type = OH_ArkUI_UIInputEvent_GetType(inputEvent);
          std::string eventInfo =
              "x: " + std::to_string(x) + ", y: " + std::to_string(y) +
              ", displayX: " + std::to_string(displayX) + ", displayY: " + std::to_string(displayY) +
              ", windowX: " + std::to_string(windowX) + ", windowY: " + std::to_string(windowY) +
              ", pointerCount: " + std::to_string(pointerCount) + ", xByIndex: " + std::to_string(xByIndex) +
              ", yByIndex: " + std::to_string(yByIndex) +
              ", displayXByIndex: " + std::to_string(displayXByIndex) +
              ", displayYByIndex: " + std::to_string(displayYByIndex) +
              ", windowXByIndex: " + std::to_string(windowXByIndex) +
              ", windowYByIndex: " + std::to_string(windowYByIndex) +
              ", pointerId: " + std::to_string(pointerId) + ", pressure: " + std::to_string(pressure) +
              ", action: " + std::to_string(action) + ", eventTime: " + std::to_string(eventTime) +
              ", sourceType: " + std::to_string(sourceType) + ", type: " + std::to_string(type);
          OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "eventInfoOfCommonEvent", "eventInfo = %{public}s",
                       eventInfo.c_str());
          break;
      }
      default: {
          break;
      }
      }
  });
  nodeAPI->unregisterNodeEventReceiver();
  nodeAPI->unregisterNodeEvent(button, NODE_ON_CLICK_EVENT);
  ```


- Color mode change event

  The ArkUI development framework provides system color mode (dark/light) change events through NDK APIs at the component level. When the system color mode changes, the framework notifies registered component callbacks, enabling color mode adaptation capabilities on the NDK side.

  > **NOTE**
  > - Multiple components can share the same callback for color mode changes.
  > - A single component can only register one callback for system color mode changes.
  > - It is recommended that you register persistent nodes (those that will not be destroyed during the page lifecycle) to prevent callback failures due to node destruction.

    ```cpp
    const unsigned int LOG_PRINT_DOMAIN = 0xFF00;
    struct ColorModeInfo {
        const char* lightMsg;
        const char* darkMsg;
    };

    // Register the callback.
    void onColorModeChange(ArkUI_SystemColorMode colorMode, void *userData)
    {
        ColorModeInfo* info = static_cast<ColorModeInfo*>(userData);
        if (colorMode == ARKUI_SYSTEM_COLOR_MODE_LIGHT) {
            OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "Manager", "Light mode: ", info->lightMsg);
        } else if (colorMode == ARKUI_SYSTEM_COLOR_MODE_DARK) {
            OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "Manager", "Dark mode: ", info->darkMsg);
        }
    }

    ArkUI_NodeHandle testColorModeChange(ArkUI_NativeNodeAPI_1 *nodeAPI) {
        ArkUI_NodeHandle text = nodeAPI->createNode(ARKUI_NODE_TEXT);
        static ColorModeInfo info = {"Light mode", "Dark mode"};
        OH_ArkUI_RegisterSystemColorModeChangeEvent(text, &info, onColorModeChange);

        ArkUI_AttributeItem itemstring = {nullptr, 0, ("Enjoy the moment")};
        nodeAPI->setAttribute(text, NODE_TEXT_CONTENT, &itemstring);

        return text;
    }
    ```

## Sample Code

1. Implement common event registration logic in the **ArkUINode** base class object.

   ```c
   // ArkUINode.h
   // Provide encapsulation of common properties and events.
   
   #ifndef MYAPPLICATION_ARKUINODE_H
   #define MYAPPLICATION_ARKUINODE_H
   
   #include "ArkUIBaseNode.h"
   #include "NativeModule.h"
   
   #include <arkui/native_node.h>
   #include <arkui/native_type.h>
   
   namespace NativeModule {
   
   class ArkUINode : public ArkUIBaseNode {
   public:
       explicit ArkUINode(ArkUI_NodeHandle handle) : ArkUIBaseNode(handle) {
           nativeModule_ = NativeModuleInstance::GetInstance()->GetNativeNodeAPI();
           // When an event is triggered, you need to get the corresponding event object through a function. Here, by setting the node's custom data, the encapsulated class pointer is kept on the component for subsequent event distribution.
           nativeModule_->setUserData(handle_, this);
           // Register the node event receiver.
           nativeModule_->addNodeEventReceiver(handle_, ArkUINode::NodeEventReceiver);
       }
   
       ~ArkUINode() override {
           if (onClick_) {
               nativeModule_->unregisterNodeEvent(handle_, NODE_ON_CLICK_EVENT);
           }
           if (onTouch_) {
               nativeModule_->unregisterNodeEvent(handle_, NODE_TOUCH_EVENT);
           }
           if (onDisappear_) {
               nativeModule_->unregisterNodeEvent(handle_, NODE_EVENT_ON_DISAPPEAR);
           }
           if (onAppear_) {
               nativeModule_->unregisterNodeEvent(handle_, NODE_EVENT_ON_APPEAR);
           }
           nativeModule_->removeNodeEventReceiver(handle_, ArkUINode::NodeEventReceiver);
       }
   
       void SetWidth(float width) {
           assert(handle_);
           ArkUI_NumberValue value[] = {{.f32 = width}};
           ArkUI_AttributeItem item = {value, 1};
           nativeModule_->setAttribute(handle_, NODE_WIDTH, &item);
       }
       void SetPercentWidth(float percent) {
           assert(handle_);
           ArkUI_NumberValue value[] = {{.f32 = percent}};
           ArkUI_AttributeItem item = {value, 1};
           nativeModule_->setAttribute(handle_, NODE_WIDTH_PERCENT, &item);
       }
       void SetHeight(float height) {
           assert(handle_);
           ArkUI_NumberValue value[] = {{.f32 = height}};
           ArkUI_AttributeItem item = {value, 1};
           nativeModule_->setAttribute(handle_, NODE_HEIGHT, &item);
       }
       void SetPercentHeight(float percent) {
           assert(handle_);
           ArkUI_NumberValue value[] = {{.f32 = percent}};
           ArkUI_AttributeItem item = {value, 1};
           nativeModule_->setAttribute(handle_, NODE_HEIGHT_PERCENT, &item);
       }
       void SetBackgroundColor(uint32_t color) {
           assert(handle_);
           ArkUI_NumberValue value[] = {{.u32 = color}};
           ArkUI_AttributeItem item = {value, 1};
           nativeModule_->setAttribute(handle_, NODE_BACKGROUND_COLOR, &item);
       }
       // Process common events.
       void RegisterOnClick(const std::function<void(ArkUI_NodeEvent *event)> &onClick) {
           assert(handle_);
           onClick_ = onClick;
           // Register the click event.
           nativeModule_->registerNodeEvent(handle_, NODE_ON_CLICK_EVENT, 0, nullptr);
       }
   
       void RegisterOnTouch(const std::function<void(int32_t type, float x, float y)> &onTouch) {
           assert(handle_);
           onTouch_ = onTouch;
           // Register the touch event.
           nativeModule_->registerNodeEvent(handle_, NODE_TOUCH_EVENT, 0, nullptr);
       }
   
       void RegisterOnDisappear(const std::function<void()> &onDisappear) {
           assert(handle_);
           onDisappear_ = onDisappear;
           // Register the disappear event.
           nativeModule_->registerNodeEvent(handle_, NODE_EVENT_ON_DISAPPEAR, 0, nullptr);
       }
   
       void RegisterOnAppear(const std::function<void()> &onAppear) {
           assert(handle_);
           onAppear_ = onAppear;
           // Register the appear event.
           nativeModule_->registerNodeEvent(handle_, NODE_EVENT_ON_APPEAR, 0, nullptr);
       }
   
   protected:
       // Event listener function pointer.
       static void NodeEventReceiver(ArkUI_NodeEvent *event) {
           // Obtain the UI component object where the event occurs.
           auto nodeHandle = OH_ArkUI_NodeEvent_GetNodeHandle(event);
           // Obtain the custom data kept in the UI component object, and return the encapsulated class pointer.
           auto *node = reinterpret_cast<ArkUINode *>(
               NativeModuleInstance::GetInstance()->GetNativeNodeAPI()->getUserData(nodeHandle));
           // Process the event based on the encapsulated class instance object.
           node->ProcessNodeEvent(event);
       }
       void ProcessNodeEvent(ArkUI_NodeEvent *event) {
           auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
           switch (eventType) {
           case NODE_ON_CLICK_EVENT: {
               if (onClick_) {
                   onClick_(event);
               }
               break;
           }
           case NODE_TOUCH_EVENT: {
               if (onTouch_) {
                   auto *uiInputEvent = OH_ArkUI_NodeEvent_GetInputEvent(event);
                   float x = OH_ArkUI_PointerEvent_GetX(uiInputEvent);
                   float y = OH_ArkUI_PointerEvent_GetY(uiInputEvent);
                   auto type = OH_ArkUI_UIInputEvent_GetAction(uiInputEvent);
                   onTouch_(type, x, y);
               }
           }
           case NODE_EVENT_ON_DISAPPEAR: {
               if (onDisappear_) {
                   onDisappear_();
               }
               break;
           }
           case NODE_EVENT_ON_APPEAR: {
               if (onAppear_) {
                   onAppear_();
               }
               break;
           }
           default: {
               // Component-specific events are processed by child classes.
               OnNodeEvent(event);
           }
           }
       }
   
       virtual void OnNodeEvent(ArkUI_NodeEvent *event) {}
   
       void OnAddChild(const std::shared_ptr<ArkUIBaseNode> &child) override {
           nativeModule_->addChild(handle_, child->GetHandle());
       }
   
       void OnRemoveChild(const std::shared_ptr<ArkUIBaseNode> &child) override {
           nativeModule_->removeChild(handle_, child->GetHandle());
       }
   
       void OnInsertChild(const std::shared_ptr<ArkUIBaseNode> &child, int32_t index) override {
           nativeModule_->insertChildAt(handle_, child->GetHandle(), index);
       }
   
   private:
       std::function<void(ArkUI_NodeEvent *event)> onClick_;
       std::function<void()> onDisappear_;
       std::function<void()> onAppear_;
       std::function<void(int32_t type, float x, float y)> onTouch_;
   };
   } // namespace NativeModule
   
   #endif // MYAPPLICATION_ARKUINODE_H
   
   ```

2. Implement list event registration logic in the **ArkUIListNode** object.
   ```c
   // ArkUIListNode.h
   // List encapsulation class object
   
   #ifndef MYAPPLICATION_ARKUILISTNODE_H
   #define MYAPPLICATION_ARKUILISTNODE_H
   
   #include "ArkUINode.h"
   #include <hilog/log.h>
   
   namespace NativeModule {
   class ArkUIListNode : public ArkUINode {
   public:
       ArkUIListNode()
           : ArkUINode((NativeModuleInstance::GetInstance()->GetNativeNodeAPI())->createNode(ARKUI_NODE_LIST)) {}
   
       ~ArkUIListNode() override { nativeModule_->unregisterNodeEvent(handle_, NODE_LIST_ON_SCROLL_INDEX); }
   
       void SetScrollBarState(bool isShow) {
           assert(handle_);
           ArkUI_ScrollBarDisplayMode displayMode =
               isShow ? ARKUI_SCROLL_BAR_DISPLAY_MODE_ON : ARKUI_SCROLL_BAR_DISPLAY_MODE_OFF;
           ArkUI_NumberValue value[] = {{.i32 = displayMode}};
           ArkUI_AttributeItem item = {value, 1};
           nativeModule_->setAttribute(handle_, NODE_SCROLL_BAR_DISPLAY_MODE, &item);
       }
   
       // Register list-related events.
       void RegisterOnScrollIndex(const std::function<void(int32_t index)> &onScrollIndex) {
           assert(handle_);
           onScrollIndex_ = onScrollIndex;
           nativeModule_->registerNodeEvent(handle_, NODE_LIST_ON_SCROLL_INDEX, 0, nullptr);
       }
   
   protected:
      // Process list-related events.
       void OnNodeEvent(ArkUI_NodeEvent *event) override {
           auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
           switch (eventType) {
           case NODE_LIST_ON_SCROLL_INDEX: {
               auto index = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event)->data[0];
               if (onScrollIndex_) {
                   onScrollIndex_(index.i32);
               }
           }
           default: {
           }
           }
       }
   
   private:
       std::function<void(int32_t index)> onScrollIndex_;
   };
   } // namespace NativeModule
   
   #endif // MYAPPLICATION_ARKUILISTNODE_H
   ```

3. Add related events.
   ```c
   // NormalTextListExample.h
   // Text list example.
   
   #ifndef MYAPPLICATION_NORMALTEXTLISTEXAMPLE_H
   #define MYAPPLICATION_NORMALTEXTLISTEXAMPLE_H
   
   #include "ArkUIBaseNode.h"
   #include "ArkUIListItemNode.h"
   #include "ArkUIListNode.h"
   #include "ArkUITextNode.h"
   #include <hilog/log.h>

   const unsigned int LOG_PRINT_DOMAIN = 0xFF00;
   
   namespace NativeModule {
   
   std::shared_ptr<ArkUIBaseNode> CreateTextListExample() {
       // Create components and mount them.
       // 1: Create a List component.
       auto list = std::make_shared<ArkUIListNode>();
       list->SetPercentWidth(1);
       list->SetPercentHeight(1);
       // 2: Create a ListItem child component and mount it to the List component.
       for (int32_t i = 0; i < 30; ++i) {
           auto listItem = std::make_shared<ArkUIListItemNode>();
           auto textNode = std::make_shared<ArkUITextNode>();
           textNode->SetTextContent(std::to_string(i));
           textNode->SetFontSize(16);
           textNode->SetPercentWidth(1);
           textNode->SetHeight(100);
           textNode->SetBackgroundColor(0xFFfffacd);
           textNode->SetTextAlign(ARKUI_TEXT_ALIGNMENT_CENTER);
           listItem->AddChild(textNode);
           // Register the click event for the list item.
           auto onClick = [](ArkUI_NodeEvent *event) {
               // Obtain the basic event object from the component event.
               auto *inputEvent = OH_ArkUI_NodeEvent_GetInputEvent(event);
               if (inputEvent == nullptr) {
                    return;
               }
               // Obtain the event type from the component event.
               auto eventType = OH_ArkUI_NodeEvent_GetEventType(event);
               OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "eventInfo", "inputEvent = %{public}p", inputEvent);
               OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "eventInfo", "eventType = %{public}d", eventType);
               auto componentEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event);
               // Obtain the numerical data from the component event.
               OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "eventInfo", "componentEvent = %{public}p",
                            componentEvent);
               // Obtain the component object that triggers the event.
               auto nodeHandle = OH_ArkUI_NodeEvent_GetNodeHandle(event);
               if (nodeHandle == nullptr) {
                    return;
               }
               OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "eventInfo", "nodeHandle = %{public}p", nodeHandle);
               // Differentiate event types and handle them accordingly. Other event information APIs follow similar usage patterns.
               switch (eventType) {
                    case NODE_ON_CLICK_EVENT: {
                        // Perform operations when the click event is triggered. Obtain event information from the base input event.
                        auto x = OH_ArkUI_PointerEvent_GetX(inputEvent);
                        auto y = OH_ArkUI_PointerEvent_GetY(inputEvent);
                        auto displayX = OH_ArkUI_PointerEvent_GetDisplayX(inputEvent);
                        auto displayY = OH_ArkUI_PointerEvent_GetDisplayY(inputEvent);
                        auto windowX = OH_ArkUI_PointerEvent_GetWindowX(inputEvent);
                        auto windowY = OH_ArkUI_PointerEvent_GetWindowY(inputEvent);
                        auto pointerCount = OH_ArkUI_PointerEvent_GetPointerCount(inputEvent);
                        auto xByIndex = OH_ArkUI_PointerEvent_GetXByIndex(inputEvent, 0);
                        auto yByIndex = OH_ArkUI_PointerEvent_GetYByIndex(inputEvent, 0);
                        auto displayXByIndex = OH_ArkUI_PointerEvent_GetDisplayXByIndex(inputEvent, 0);
                        auto displayYByIndex = OH_ArkUI_PointerEvent_GetDisplayYByIndex(inputEvent, 0);
                        auto windowXByIndex = OH_ArkUI_PointerEvent_GetWindowXByIndex(inputEvent, 0);
                        auto windowYByIndex = OH_ArkUI_PointerEvent_GetWindowYByIndex(inputEvent, 0);
                        auto pointerId = OH_ArkUI_PointerEvent_GetPointerId(inputEvent, 0);
                        auto pressure = OH_ArkUI_PointerEvent_GetPressure(inputEvent, 0);
                        auto action = OH_ArkUI_UIInputEvent_GetAction(inputEvent);
                        auto eventTime = OH_ArkUI_UIInputEvent_GetEventTime(inputEvent);
                        auto sourceType = OH_ArkUI_UIInputEvent_GetSourceType(inputEvent);
                        auto type = OH_ArkUI_UIInputEvent_GetType(inputEvent);
                        std::string eventInfo =
                            "x: " + std::to_string(x) + ", y: " + std::to_string(y) +
                            ", displayX: " + std::to_string(displayX) + ", displayY: " + std::to_string(displayY) +
                            ", windowX: " + std::to_string(windowX) + ", windowY: " + std::to_string(windowY) +
                            ", pointerCount: " + std::to_string(pointerCount) + ", xByIndex: " + std::to_string(xByIndex) +
                            ", yByIndex: " + std::to_string(yByIndex) +
                            ", displayXByIndex: " + std::to_string(displayXByIndex) +
                            ", displayYByIndex: " + std::to_string(displayYByIndex) +
                            ", windowXByIndex: " + std::to_string(windowXByIndex) +
                            ", windowYByIndex: " + std::to_string(windowYByIndex) +
                            ", pointerId: " + std::to_string(pointerId) + ", pressure: " + std::to_string(pressure) +
                            ", action: " + std::to_string(action) + ", eventTime: " + std::to_string(eventTime) +
                            ", sourceType: " + std::to_string(sourceType) + ", type: " + std::to_string(type);
                        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "eventInfoOfCommonEvent",
                                        "eventInfo = %{public}s", eventInfo.c_str());
                    }
                    default: {
                        break;
                    }
                }
           };
           listItem->RegisterOnClick(onClick);
           list->AddChild(listItem);
       }
       // 3: Register list-related listening events.
       list->RegisterOnScrollIndex([](int32_t index) { OH_LOG_INFO(LOG_APP, "on list scroll index: %{public}d", index); });
       // 4: Register the appear event.
       list->RegisterOnAppear([]() { OH_LOG_INFO(LOG_APP, "on list mount to tree"); });
       // 5: Register the disappear event.
       list->RegisterOnDisappear([]() { OH_LOG_INFO(LOG_APP, "on list unmount from tree"); });
       return list;
   }
   } // namespace NativeModule
   
   #endif // MYAPPLICATION_NORMALTEXTLISTEXAMPLE_H
   
   ```

   Since log-related APIs are used, add a reference to **libhilog_ndk.z.so** in the **CMakeLists.txt** file as follows:
   
   ```
   add_library(entry SHARED napi_init.cpp NativeEntry.cpp)
   target_link_libraries(entry PUBLIC libace_napi.z.so libace_ndk.z.so libhilog_ndk.z.so)
   ```
