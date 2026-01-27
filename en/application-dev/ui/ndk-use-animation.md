# Using Animations
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->


## Using Property Animations

The ArkUI framework primarily offers property animations through NDK APIs to implement component transition effects for appearance and disappearance. Additionally, frame animation capabilities from the ArkTS side can be bridged through the Node-API to achieve animation effects on the native side.

> **NOTE**
>
> - Obtain [this.getUIContext()](../reference/apis-arkui/arkui-ts/ts-custom-component-api.md#getuicontext) from ArkTS and pass it to the native side.
> 
> - On the native side, obtain the context using the [OH_ArkUI_GetContextFromNapiValue](../reference/apis-arkui/capi-native-node-napi-h.md) API.
> 
> - Animation property changes must be encapsulated within the callback of [ArkUI_ContextCallback](../reference/apis-arkui/capi-arkui-nativemodule-arkui-contextcallback.md).
> 
> - Ensure that the properties intended for animation have been set before the animation is executed.
>
> - This section demonstrates core API usage only. For the complete sample project, see <!--RP1-->[AnimationNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/AnimationNDK)<!--RP1End-->.

A global **animateTo** explicit animation API is provided to specify transition effects for state changes caused by closure code. Like property animations, layout changes such as width and height adjustments are animated directly to their final states.

1. Create a [NodeContent](../reference//apis-arkui/js-apis-arkui-NodeContent.md) object in the .ets file and pass it as a parameter to the native method.

    <!-- @[get_content](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AnimationNDK/entry/src/main/ets/pages/UseFrameAnimation.ets) -->
    
    ``` TypeScript
      // Initialize the NodeContent object.
      private rootSlot = new NodeContent();
      @State @Watch('changeNativeFlag') showNative: boolean = false;
    // ···
      changeNativeFlag(): void {
        // ···
        if (this.showNative) {
          // Pass the NodeContent object for the native side to create component mounting and display.
          nativeNode?.createNativeRoot(this.rootSlot);
        } else {
        // ···
        }
      }
    ```

2. Parse the **NodeContent** object and convert it to the corresponding **ArkUI_NodeContentHandle** structure in C.

    <!-- @[get_context](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AnimationNDK/entry/src/main/cpp/NativeEntry.cpp) -->
    
    ``` C++
    // Obtain the NodeContent object.
    ArkUI_NodeContentHandle contentHandle;
    OH_ArkUI_GetNodeContentFromNapiValue(env, args[0], &contentHandle);
    ```

3. Obtain the **ArkUI_NativeAnimateAPI_1** object.

    <!-- @[get_Api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AnimationNDK/entry/src/main/cpp/ArkUIAnimate.h) -->
    
    ``` C
    // Obtain the ArkUI_NativeAnimateAPI.
    ArkUI_NativeAnimateAPI_1 *animateApi = nullptr;
    OH_ArkUI_GetModuleInterface(ARKUI_NATIVE_ANIMATE, ArkUI_NativeAnimateAPI_1, animateApi);
    ```

4. Set the **ArkUI_AnimateOption** parameters using the provided C APIs.

    <!-- @[set_option](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AnimationNDK/entry/src/main/cpp/ArkUIAnimate.h) -->
    
    ``` C
    // Set the animation parameters.
    ArkUI_AnimateOption *option = OH_ArkUI_AnimateOption_Create();
    OH_ArkUI_AnimateOption_SetDuration(option, NUM_2000); // NUM_2000 = 2000
    OH_ArkUI_AnimateOption_SetTempo(option, 1.1);
    OH_ArkUI_AnimateOption_SetCurve(option, ARKUI_CURVE_EASE);
    ArkUI_CurveHandle cubicBezierCurve = OH_ArkUI_Curve_CreateCubicBezierCurve(0.5f, 4.0f, 1.2f, 0.0f);
    // Set the animation curve parameters, which take precedence over OH_ArkUI_AnimateOption_SetCurve.
    OH_ArkUI_AnimateOption_SetICurve(option, cubicBezierCurve);
    OH_ArkUI_AnimateOption_SetDelay(option, NUM_20); // NUM_20 = 20
    OH_ArkUI_AnimateOption_SetIterations(option, NUM_1); // NUM_1 = 1
    OH_ArkUI_AnimateOption_SetPlayMode(option, ARKUI_ANIMATION_PLAY_MODE_REVERSE);
    ArkUI_ExpectedFrameRateRange *range = new ArkUI_ExpectedFrameRateRange;
    range->min = NUM_10; // NUM_10 = 10
    range->max = NUM_120; // NUM_120 = 120
    range->expected = NUM_60; // NUM_60 = 60
    OH_ArkUI_AnimateOption_SetExpectedFrameRateRange(option, range);
    ```

5. Set callback parameters.

    <!-- @[set_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AnimationNDK/entry/src/main/cpp/ArkUIAnimate.h) -->
    
    ``` C
    // Create and set user data for the completion callback.
    ArkUI_AnimateCompleteCallback *completeCallback = new ArkUI_AnimateCompleteCallback;
    completeCallback->type = ARKUI_FINISH_CALLBACK_REMOVED;
    // The AnimateData struct contains ArkUI_AnimateOption* option and ArkUI_CurveHandle curve.
    AnimateData* data = new AnimateData();
    data->option = option;
    data->curve = cubicBezierCurve;
    completeCallback->userData = reinterpret_cast<void*>(data);
    completeCallback->callback = [](void *userData) {
        AnimateData* data = reinterpret_cast<AnimateData*>(userData);
        if (data) {
            ArkUI_AnimateOption* option = data->option;
            ArkUI_CurveHandle curve = data->curve;
            if (option) {
                OH_ArkUI_AnimateOption_Dispose(option);
                OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN,
                    "Init", "CXX OH_ArkUI_AnimateOption_Dispose  success!");
            }
            if (curve) {
                OH_ArkUI_Curve_DisposeCurve(curve);
                OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN,
                    "Init", "CXX OH_ArkUI_Curve_DisposeCurve  success!");
            }
            delete data; // Release the struct.
        }
    };
                
    // Set the closure function.
    static bool isback = true;
    ArkUI_ContextCallback *update = new ArkUI_ContextCallback;
    update->callback = [](void *user) {
        // Example of changing width and height properties
        if (isback) {
            g_animateto_button->SetWidth(NUM_200); // NUM_200 = 200
            g_animateto_button->SetHeight(NUM_80); // NUM_80 = 80
            g_animateto_button->SetBackgroundColor(0xFFA280FF);
        } else {
            g_animateto_button->SetWidth(NUM_100); // NUM_100 = 100
            g_animateto_button->SetHeight(NUM_40); // NUM_40 = 40
            g_animateto_button->SetBackgroundColor(0xFFFF2E77);
        }
        isback = !isback;
    };
    // Execute the animation with the set options and callbacks.
    animateApi->animateTo(context, option, update, completeCallback);
    ```

   ![GIF](figures/animateTo.gif)

## Using Component Appearance/Disappearance Transitions

Use **NODE_*XX*_TRANSITION** properties (where *XX* can be **OPACITY**, **TRANSLATE**, **SCALE**, **ROTATE**, or **MOVE**) to configure transition effects for components, enhancing the user experience when components are added to or removed from containers. The **NODE_TRANSFORM_CENTER** property sets the center point for animations including **NODE_SCALE_TRANSITION** and **NODE_ROTATE_ROTATE**.  

1. Design an interactive UI with a button to manage the addition and removal of transition nodes. For details about how to obtain and use the ArkUI_NodeContentHandle node, see [Integrating with ArkTS Pages](ndk-access-the-arkts-page.md).

    <!-- @[main_view_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AnimationNDK/entry/src/main/cpp/ArkUITransition.h) -->
    
    ``` C
    constexpr int32_t BUTTON_CLICK_ID = 1;
    bool g_flag = false;
    ArkUI_NodeHandle parentNode;
    ArkUI_NodeHandle childNode;
    ArkUI_NodeHandle buttonNode;
    // ···
    void mainViewMethod(ArkUI_NodeContentHandle handle)
    {
        ArkUI_NativeNodeAPI_1 *nodeAPI = reinterpret_cast<ArkUI_NativeNodeAPI_1 *>(
            OH_ArkUI_QueryModuleInterfaceByName(ARKUI_NATIVE_NODE, "ArkUI_NativeNodeAPI_1"));
        ArkUI_NodeHandle column = nodeAPI->createNode(ARKUI_NODE_COLUMN);
        ArkUI_NumberValue widthValue[] = {{.f32 = 500}};
        ArkUI_AttributeItem widthItem = {.value = widthValue, .size = sizeof(widthValue) / sizeof(ArkUI_NumberValue)};
        nodeAPI->setAttribute(column, NODE_WIDTH, &widthItem);
        ArkUI_NumberValue heightValue[] = {{.f32 = 500}};
        ArkUI_AttributeItem heightItem = {.value = heightValue, .size = sizeof(heightValue) / sizeof(ArkUI_NumberValue)};
        nodeAPI->setAttribute(column, NODE_HEIGHT, &heightItem);
        ArkUI_NodeHandle buttonShow = nodeAPI->createNode(ARKUI_NODE_BUTTON);
        ArkUI_NumberValue buttonWidthValue[] = {{.f32 = 200}};
        ArkUI_AttributeItem buttonWidthItem = {.value = buttonWidthValue,
                                               .size = sizeof(buttonWidthValue) / sizeof(ArkUI_NumberValue)};
        nodeAPI->setAttribute(buttonShow, NODE_WIDTH, &buttonWidthItem);
        ArkUI_NumberValue buttonHeightValue[] = {{.f32 = 50}};
        ArkUI_AttributeItem buttonHeightItem = {.value = buttonHeightValue,
                                                .size = sizeof(buttonHeightValue) / sizeof(ArkUI_NumberValue)};
        nodeAPI->setAttribute(buttonShow, NODE_HEIGHT, &buttonHeightItem);
        ArkUI_AttributeItem labelItem = {.string = "show"};
        nodeAPI->setAttribute(buttonShow, NODE_BUTTON_LABEL, &labelItem);
        ArkUI_NumberValue buttonOpenTypeValue[] = {{.i32 = static_cast<int32_t>(ARKUI_BUTTON_TYPE_NORMAL)}};
        ArkUI_AttributeItem buttonOpenTypeItem = {.value = buttonOpenTypeValue,
                                                  .size = sizeof(buttonOpenTypeValue) / sizeof(ArkUI_NumberValue)};
        nodeAPI->setAttribute(buttonShow, NODE_BUTTON_TYPE, &buttonOpenTypeItem);
        ArkUI_NumberValue buttonShowMarginValue[] = {{.f32 = 20}};
        ArkUI_AttributeItem buttonShowMarginItem = {.value = buttonShowMarginValue,
                                                    .size = sizeof(buttonShowMarginValue) / sizeof(ArkUI_NumberValue)};
        nodeAPI->setAttribute(buttonShow, NODE_MARGIN, &buttonShowMarginItem);
        nodeAPI->registerNodeEvent(buttonShow, NODE_ON_CLICK, BUTTON_CLICK_ID, nullptr);
        nodeAPI->addNodeEventReceiver(buttonShow, OnButtonShowClicked);
        parentNode = column;
        buttonNode = buttonShow;
        nodeAPI->addChild(column, buttonShow);
        OH_ArkUI_NodeContent_AddNode(handle, column);
    }
    ```

2. Create a node with **Transition** properties that play a transition animation when the target node is mounted or unmounted.

    <!-- @[create_child_node](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AnimationNDK/entry/src/main/cpp/ArkUITransition.h) -->
    
    ``` C
    ArkUI_NodeHandle CreateChildNode()
    {
        ArkUI_NativeNodeAPI_1 *nodeAPI = reinterpret_cast<ArkUI_NativeNodeAPI_1 *>(
            OH_ArkUI_QueryModuleInterfaceByName(ARKUI_NATIVE_NODE, "ArkUI_NativeNodeAPI_1"));
        ArkUI_NodeHandle image = nodeAPI->createNode(ARKUI_NODE_IMAGE);
        ArkUI_AttributeItem imageSrcItem = {.string = "/pages/common/scenery.jpg"};
        nodeAPI->setAttribute(image, NODE_IMAGE_SRC, &imageSrcItem);
        ArkUI_NumberValue textWidthValue[] = {{.f32 = 300}};
        ArkUI_AttributeItem textWidthItem = {.value = textWidthValue,
                                             .size = sizeof(textWidthValue) / sizeof(ArkUI_NumberValue)};
        nodeAPI->setAttribute(image, NODE_WIDTH, &textWidthItem);
        ArkUI_NumberValue textHeightValue[] = {{.f32 = 300}};
        ArkUI_AttributeItem textHeightItem = {.value = textHeightValue,
                                              .size = sizeof(textWidthValue) / sizeof(ArkUI_NumberValue)};
        nodeAPI->setAttribute(image, NODE_HEIGHT, &textHeightItem);
        ArkUI_NumberValue transformCenterValue[] = {0.0f, 0.0f, 0.0f, 0.5f, 0.5f};
        ArkUI_AttributeItem transformCenterItem = {.value = transformCenterValue,
                                                   .size = sizeof(transformCenterValue) / sizeof(ArkUI_NumberValue)};
        nodeAPI->setAttribute(image, NODE_TRANSFORM_CENTER, &transformCenterItem);
        ArkUI_NumberValue rotateAnimationValue[] = {
            0.0f, 0.0f, 1.0f, 360.0f, 0.0f, {.i32 = 500}, {.i32 = static_cast<int32_t>(ARKUI_CURVE_SHARP)}};
        ArkUI_AttributeItem rotateAnimationItem = {.value = rotateAnimationValue,
                                                   .size = sizeof(rotateAnimationValue) / sizeof(ArkUI_NumberValue)};
        nodeAPI->setAttribute(image, NODE_ROTATE_TRANSITION, &rotateAnimationItem);
        ArkUI_NumberValue scaleAnimationValue[] = {
            0.0f, 0.0f, 0.0f, {.i32 = 500}, {.i32 = static_cast<int32_t>(ARKUI_CURVE_SHARP)}};
        ArkUI_AttributeItem scaleAnimationItem = {.value = scaleAnimationValue,
                                                  .size = sizeof(scaleAnimationValue) / sizeof(ArkUI_NumberValue)};
        nodeAPI->setAttribute(image, NODE_SCALE_TRANSITION, &scaleAnimationItem);
        ArkUI_NumberValue translateAnimationValue[] = {
            200, 200, 0.0f, {.i32 = 500}, {.i32 = static_cast<int32_t>(ARKUI_CURVE_SHARP)}};
        ArkUI_AttributeItem translateAnimationItem = {.value = translateAnimationValue,
                                                      .size = sizeof(translateAnimationValue) / sizeof(ArkUI_NumberValue)};
        nodeAPI->setAttribute(image, NODE_TRANSLATE_TRANSITION, &translateAnimationItem);
        return image;
    }
    ```

3. Add logic for mounting and unmounting the transition node within the **Button** component event callback to control the appearance and disappearance of the transition node.

    <!-- @[button_show](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AnimationNDK/entry/src/main/cpp/ArkUITransition.h) -->
    
    ``` C
    void OnButtonShowClicked(ArkUI_NodeEvent *event)
    {
        if (!event) {
            return;
        }
        if (!childNode) {
            childNode = CreateChildNode();
        }
        ArkUI_NativeNodeAPI_1 *nodeAPI = reinterpret_cast<ArkUI_NativeNodeAPI_1 *>(
            OH_ArkUI_QueryModuleInterfaceByName(ARKUI_NATIVE_NODE, "ArkUI_NativeNodeAPI_1"));
        if (g_flag) {
            g_flag = false;
            ArkUI_AttributeItem labelItem = {.string = "show"};
            nodeAPI->setAttribute(buttonNode, NODE_BUTTON_LABEL, &labelItem);
            nodeAPI->removeChild(parentNode, childNode);
        } else {
            g_flag = true;
            ArkUI_AttributeItem labelItem = {.string = "hide"};
            nodeAPI->setAttribute(buttonNode, NODE_BUTTON_LABEL, &labelItem);
            nodeAPI->addChild(parentNode, childNode);
        }
    }
    ```

    ![en-us_image_0000001903284256](figures/en-us_image_0000001903284256.gif)

## Using Keyframe Animations

You can use the [keyframeAnimateTo](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativeanimateapi-1.md#keyframeanimateto) API to specify several keyframe states to create segmented animations. Like property animations, layout changes such as width and height adjustments are animated directly to their final states.

This example demonstrates how to use the [keyframeAnimateTo](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativeanimateapi-1.md#keyframeanimateto) API to set up keyframe animations. For the complete process of mounting a UI developed with NDK APIs to the ArkTS main page, see [Integrating with ArkTS Pages](ndk-access-the-arkts-page.md).

<!-- @[get_keyframeAnimateTo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AnimationNDK/entry/src/main/cpp/ArkUIAnimate.h) -->    

``` C
// ArkUIColumnNode is a project-encapsulated node type.
auto column = std::make_shared<ArkUIColumnNode>();
// Set width to 300 (NUM_300 = 300).
column->SetWidth(NUM_300);
// Set height to 250 (NUM_250 = 250).
column->SetHeight(NUM_250);
// Create a text node with content "This is a keyframe animation."
auto textNode = std::make_shared<ArkUITextNode>();
textNode->SetTextContent("This is a keyframe animation");
// Set width to 120 (NUM_120 = 120).
textNode->SetWidth(NUM_120);
// Set height to 120 (NUM_120 = 120).
textNode->SetHeight(NUM_50);
// Create a button that will be the target of the keyframe animation.
auto button = std::make_shared<ArkUIButtonNode>();
// Set the initial width and height of the button (NUM_100 = 100).
button->SetWidth(NUM_100);
button->SetHeight(NUM_100);
// Store the button as a global variable for use in onTouch registration.
g_keyframe_button = button;
// Register a click event for the button (NUM_1 = 1).
button->RegisterNodeEvent(button->GetHandle(), NODE_ON_CLICK, NUM_1, nullptr);
g_keyframe_text = std::make_shared<ArkUITextNode>();
// This function encapsulates logic to print AnimateTo parameter values in a text component (to be implemented by the user based on specific requirements).
g_keyframe_text->KeyframeAnimatetoToString();
auto onTouch = [](ArkUI_NodeEvent *event) {
    // Trigger logic when the target button (NUM_1 = 1) is clicked.
    if (OH_ArkUI_NodeEvent_GetTargetId(event) == NUM_1) {
        // Obtain the context object.
        ArkUI_ContextHandle context = nullptr;
        // g_keyframe_button (std::shared_ptr<ArkUIButtonNode>) is a global variable that holds the button node instance for use in onTouch event registration.
        context = OH_ArkUI_GetContextByNode(g_keyframe_button->GetHandle());
        // Obtain the ArkUI_NativeAnimateAPI.
        ArkUI_NativeAnimateAPI_1 *animateApi = nullptr;
        OH_ArkUI_GetModuleInterface(ARKUI_NATIVE_ANIMATE, ArkUI_NativeAnimateAPI_1, animateApi);
            
        // The following code is the key process for creating a keyframe animation, including setting keyframe animation parameters and starting the animation.
        // Set the ArkUI_KeyframeAnimateOption parameters using the provided C APIs.
        // Number of keyframe animation states (NUM_2 = 2, NUM_500 = 500).
        ArkUI_KeyframeAnimateOption *option =  OH_ArkUI_KeyframeAnimateOption_Create(NUM_2);
        OH_ArkUI_KeyframeAnimateOption_SetDelay(option, NUM_500);
        // Duration for the first keyframe segment (NUM_1000 = 1000, NUM_0 = 0).
        OH_ArkUI_KeyframeAnimateOption_SetDuration(option, NUM_1000, NUM_0);
        // Duration for the second keyframe segment (NUM_2000 = 2000, NUM_1 = 1).
        OH_ArkUI_KeyframeAnimateOption_SetDuration(option, NUM_2000, NUM_1);
        // Animation playback iterations (NUM_5 = 5).
        OH_ArkUI_KeyframeAnimateOption_SetIterations(option, NUM_5);
        ArkUI_CurveHandle curve = OH_ArkUI_Curve_CreateCubicBezierCurve(0.5f, 4.0f, 1.2f, 0.0f);
        // Select the animation curves based on service requirements.
        ArkUI_CurveHandle springCurve = OH_ArkUI_Curve_CreateSpringCurve(0.5f, 4.0f, 1.2f, 0.0f);
        ArkUI_CurveHandle springMotionCurve = OH_ArkUI_Curve_CreateSpringMotion(0.5f, 0.6f, 0.0f);
        ArkUI_CurveHandle responsiveSpringMotionCurve = OH_ArkUI_Curve_CreateResponsiveSpringMotion(0.5f,
            4.0f, 1.2f);
        ArkUI_CurveHandle interpolatingSpringCurve = OH_ArkUI_Curve_CreateInterpolatingSpring(0.5f,
            4.0f, 1.2f, 0.0f);
        OH_ArkUI_KeyframeAnimateOption_SetCurve(option, curve, 1);
        OH_ArkUI_KeyframeAnimateOption_RegisterOnEventCallback(option, nullptr, [](void *userData) {
              g_keyframe_button->SetWidth(NUM_150);
        }, NUM_0); // Callback for the first keyframe state (NUM_150 = 150, NUM_0 = 0).
        OH_ArkUI_KeyframeAnimateOption_RegisterOnEventCallback(option, nullptr, [](void *userData) {
              g_keyframe_button->SetWidth(80);
        }, NUM_1); // Callback for the second keyframe state (NUM_1 = 1).
        KeyFrameAnimateToData* data = new KeyFrameAnimateToData();
        data->option = option;
        data->curve = curve;
        OH_ArkUI_KeyframeAnimateOption_RegisterOnFinishCallback(option, nullptr, [](void *user) {
            KeyFrameAnimateToData* data = reinterpret_cast<KeyFrameAnimateToData*>(user);
            if (data) {
                ArkUI_KeyframeAnimateOption* option = data->option;
                ArkUI_CurveHandle curve = data->curve;
                if (option) {
                    OH_ArkUI_KeyframeAnimateOption_Dispose(option);
                    OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN,
                        "Init", "CXX OH_ArkUI_KeyframeAnimateOption_Dispose  success!");
                }
                if (curve) {
                    OH_ArkUI_Curve_DisposeCurve(curve);
                    OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN,
                        "Init", "CXX OH_ArkUI_Curve_DisposeCurve  success!");
                }
                delete data; // Release the struct.
            }
        }); // Keyframe animation completion callback.
        ArkUI_ExpectedFrameRateRange *range = new ArkUI_ExpectedFrameRateRange;
        range->max = NUM_120; // NUM_120 = 120
        range->expected = NUM_60; // NUM_60 = 60
        range->min = NUM_30; // NUM_30 = 30
        OH_ArkUI_KeyframeAnimateOption_SetExpectedFrameRate(option, range); // Set the expected frame rate for keyframes.

        // Execute the animation with the set options and callbacks.
        animateApi->keyframeAnimateTo(context, option);
        auto delay = OH_ArkUI_KeyframeAnimateOption_GetDelay(option);
        auto iter = OH_ArkUI_KeyframeAnimateOption_GetIterations(option);
        auto expected = OH_ArkUI_KeyframeAnimateOption_GetExpectedFrameRate(option); // Obtain the expected frame rate range from the keyframe animation parameters.
        auto dur0 = OH_ArkUI_KeyframeAnimateOption_GetDuration(option, NUM_1); // NUM_1 = 1
        auto dur1 = OH_ArkUI_KeyframeAnimateOption_GetDuration(option, NUM_1);
        auto curves = OH_ArkUI_KeyframeAnimateOption_GetCurve(option, NUM_1); // Obtain the animation curve for a specific keyframe segment.
        g_keyframe_text->KeyframeAnimatetoToString(dur0, dur1, delay, iter, *expected);
    }
};
// Register a callback function for the click event.
button->RegisterNodeEventReceiver(onTouch);
// Mount the button to the column and return the column node.
column->AddChild(g_keyframe_text);
column->AddChild(textNode);
column->AddChild(button);
```

![en-us_image_0000001903284256](figures/en-us_image_keyframeAnimateTo.gif)

## Using Frame Animations

Frame animation enables adjustment of animation properties on each frame through its per-frame callback mechanism. By leveraging the **onFrame** callback, you can dynamically set property values frame by frame, creating smooth and natural-looking animations. For details about the frame animation APIs, see [createAnimator](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativeanimateapi-1.md#createanimator).

Compared with the property animation, the frame animation offers the benefits of real-time visibility into the animation process and allows you to modify UI values on the fly. In addition, it provides high responsiveness to events and can be paused as needed. However, it is worth noting that the frame animation may not deliver the same performance efficiency as the property animation. Therefore, where the property animation meets your requirements, you are advised to use the property animation APIs. For details about how to use the [animateTo](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativeanimateapi-1.md#animateto) API, see [Using Property Animations](#using-property-animations).

This example demonstrates how to use the [createAnimator](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativeanimateapi-1.md#createanimator) API to set up frame animations. For the complete sample project, see <!--RP1-->[AnimationNDK](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/AnimationNDK)<!--RP1End-->.

<!-- @[get_createAnimator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AnimationNDK/entry/src/main/cpp/ArkUIAnimate.h) -->

```C
std::shared_ptr<ArkUIBaseNode> CreateAnimator()
{
    auto column = std::make_shared<ArkUIColumnNode>();
    column->SetWidth(NUM_300); // NUM_300 = 300
    column->SetHeight(NUM_250); // NUM_250 = 250
    // Create a text node with content "This is an animator animation."
    auto textNode = std::make_shared<ArkUITextNode>();
    textNode->SetTextContent("This is an animator animation");
    textNode->SetWidth(NUM_120); // NUM_120 = 120
    textNode->SetHeight(NUM_50); // NUM_50 = 50
    // Create createButton to initialize animator parameters.
    auto createButton = std::make_shared<ArkUIButtonNode>();
    // Create a button that serves as the target of the animator animation.
    auto button = std::make_shared<ArkUIButtonNode>();
    // Set the initial width and height of the button (NUM_100 = 100).
    button->SetWidth(NUM_100);
    button->SetHeight(NUM_100);
    // Store the button as a global variable for use in onTouch registration.
    g_animator_button = button;
    // Register a click event for the button (NUM_3 = 3).
    createButton->RegisterNodeEvent(createButton->GetHandle(), NODE_ON_CLICK, NUM_3, nullptr);
    g_animator_text = std::make_shared<ArkUITextNode>();
    g_animator_text->AnimatorToString();
    auto onTouch = [](ArkUI_NodeEvent *event) {
        // Trigger logic when the target button (NUM_3 = 3) is clicked.
        if (OH_ArkUI_NodeEvent_GetTargetId(event) == NUM_3) {
            // Obtain the context object.
            static ArkUI_ContextHandle context = nullptr;
            context = OH_ArkUI_GetContextByNode(g_animator_button->GetHandle());

            // Obtain the ArkUI_NativeAnimateAPI.
            ArkUI_NativeAnimateAPI_1 *animateApi = nullptr;
            OH_ArkUI_GetModuleInterface(ARKUI_NATIVE_ANIMATE, ArkUI_NativeAnimateAPI_1, animateApi);
            
            // The following demonstrates the key process for creating an Animator animation, including setting Animator animation parameters and starting the animation.
            // Set the ArkUI_AnimatorOption parameters using the provided C APIs (NUM_0 = 0).
            static ArkUI_AnimatorOption *option =  OH_ArkUI_AnimatorOption_Create(NUM_0); // Number of animator animation states.
            OH_ArkUI_AnimatorOption_SetDuration(option, NUM_2000); // NUM_2000 = 2000
            OH_ArkUI_AnimatorOption_SetDelay(option, NUM_10); // NUM_10 = 10
            OH_ArkUI_AnimatorOption_SetIterations(option, NUM_3); // NUM_3 = 3
            OH_ArkUI_AnimatorOption_SetFill(option, ARKUI_ANIMATION_FILL_MODE_NONE);
            OH_ArkUI_AnimatorOption_SetDirection(option, ARKUI_ANIMATION_DIRECTION_NORMAL);
            ArkUI_CurveHandle curve = OH_ArkUI_Curve_CreateCubicBezierCurve(0.5f, 4.0f, 1.2f, 0.0f); // Create a cubic Bézier curve object.
            OH_ArkUI_AnimatorOption_SetCurve(option, curve);
            OH_ArkUI_AnimatorOption_SetBegin(option, NUM_100); // NUM_100 = 100
            OH_ArkUI_AnimatorOption_SetEnd(option, NUM_150); // NUM_150 = 150
            ArkUI_ExpectedFrameRateRange *range = new ArkUI_ExpectedFrameRateRange;
            range->max = NUM_120; // NUM_120 = 120
            range->expected = NUM_60; // NUM_60 = 60
            range->min = NUM_30; // NUM_30 = 30
            OH_ArkUI_AnimatorOption_SetExpectedFrameRateRange(option, range);
            OH_ArkUI_AnimatorOption_SetKeyframe(option, 0.5, 120.5, NUM_0); // Set the keyframe parameters of the animator animation (NUM_0 = 0).
            OH_ArkUI_AnimatorOption_SetKeyframeCurve(option, curve, NUM_0); // Set the keyframe curve type of the animator animation.
            OH_ArkUI_AnimatorOption_RegisterOnFrameCallback(option, nullptr, [](ArkUI_AnimatorOnFrameEvent *event)
            {
                OH_ArkUI_AnimatorOnFrameEvent_GetUserData(event); // Obtain the custom object from the animation event object.
                auto value = OH_ArkUI_AnimatorOnFrameEvent_GetValue(event); // Obtain the current progress from the animation event object.
                OH_LOG_Print(LOG_APP, LOG_ERROR, LOG_PRINT_DOMAIN, "Init",
                    "CXX OH_ArkUI_AnimatorOption_RegisterOnFrameCallback  %{public}f", value);
                g_animator_button->SetWidth(value);
            });
            OH_ArkUI_AnimatorOption_RegisterOnFinishCallback(option, nullptr, [](ArkUI_AnimatorEvent* event)
            {
                OH_ArkUI_AnimatorEvent_GetUserData(event); // Obtain the custom object from the animation event object.
            });
            OH_ArkUI_AnimatorOption_RegisterOnCancelCallback(option, nullptr, [](ArkUI_AnimatorEvent* event)
            {
            });
            OH_ArkUI_AnimatorOption_RegisterOnRepeatCallback(option, nullptr, [](ArkUI_AnimatorEvent* event)
            {
            });
            // Execute the animation with the set options and callbacks.
            animatorHandle = animateApi->createAnimator(context, option);
            
            auto duration = OH_ArkUI_AnimatorOption_GetDuration(option);
            auto delay = OH_ArkUI_AnimatorOption_GetDelay(option);
            auto iterations = OH_ArkUI_AnimatorOption_GetIterations(option);
            auto fill = OH_ArkUI_AnimatorOption_GetFill(option);
            auto direction = OH_ArkUI_AnimatorOption_GetDirection(option);
            auto curves = OH_ArkUI_AnimatorOption_GetCurve(option); // Obtain the animator animation interpolation curve.
            auto begin = OH_ArkUI_AnimatorOption_GetBegin(option);
            auto end = OH_ArkUI_AnimatorOption_GetEnd(option); // Obtain the interpolation end point of the animator animation.
            auto expected = OH_ArkUI_AnimatorOption_GetExpectedFrameRateRange(option); // Obtain the expected frame rate range from the keyframe animation parameters.
            auto keyframeTime = OH_ArkUI_AnimatorOption_GetKeyframeTime(option, NUM_0); // Obtain the keyframe time of the animator animation.
            auto keyframeValue = OH_ArkUI_AnimatorOption_GetKeyframeValue(option, NUM_0); // Obtain the keyframe value from the animator animation parameters.
            auto keyframeCurve = OH_ArkUI_AnimatorOption_GetKeyframeCurve(option, NUM_0); // Obtain the keyframe interpolation curve of the animator animation.
            g_animator_text->AnimatorToString(duration, delay, iterations, fill, direction, begin,
                end, *expected, keyframeTime, keyframeValue);
        }
    };

    // Register a callback function for the click event.
    createButton->RegisterNodeEventReceiver(onTouch);
    createButton->SetButtonLabel("create");
    // Create a container for storing the button.
    auto buttoColumn = std::make_shared<ArkUIColumnNode>();
    buttoColumn->SetPadding(NUM_30, false); // Set the layout padding (NUM_30=30).
    buttoColumn->SetWidth(NUM_300); // NUM_300 = 300
    // Create a container for storing playButton.
    auto playButtonColumn = std::make_shared<ArkUIColumnNode>();
    playButtonColumn->SetPadding(NUM_10, false); // Set the layout padding (NUM_10 = 10).
    playButtonColumn->SetWidth(NUM_300); // NUM_300 = 300
    // Set the animator play button.
    auto playButton = std::make_shared<ArkUIButtonNode>();
    playButton->SetButtonLabel("play");
    playButton->RegisterNodeEvent(playButton->GetHandle(), NODE_ON_CLICK, NUM_4, nullptr);
    auto onTouchPlay = [](ArkUI_NodeEvent *event) {
        // Trigger logic when the target button (NUM_4 = 4) is clicked.
        if (OH_ArkUI_NodeEvent_GetTargetId(event) == NUM_4) {
            OH_ArkUI_Animator_Play(animatorHandle);
        }
    };
    playButton->RegisterNodeEventReceiver(onTouchPlay);
    // Set the animator end button.
    auto finishButton = std::make_shared<ArkUIButtonNode>();
    finishButton->SetButtonLabel("finish");
    finishButton->RegisterNodeEvent(finishButton->GetHandle(), NODE_ON_CLICK, NUM_5, nullptr); // NUM_5 = 5
    auto onTouchFinish = [](ArkUI_NodeEvent *event) {
        // Trigger logic when the target button (NUM_5 = 5) is clicked.
        if (OH_ArkUI_NodeEvent_GetTargetId(event) == NUM_5) {
            OH_ArkUI_Animator_Finish(animatorHandle);
        }
    };
    finishButton->RegisterNodeEventReceiver(onTouchFinish);
    // Create a container for storing resetButton.
    auto resetButtonColumn = std::make_shared<ArkUIColumnNode>();
    resetButtonColumn->SetPadding(NUM_10, false); // Set the layout padding (NUM_10 = 10).
    resetButtonColumn->SetWidth(NUM_300); // NUM_300 = 300
    // Set the animator update button.
    auto resetButton = std::make_shared<ArkUIButtonNode>();
    resetButton->SetButtonLabel("reset");
    resetButton->RegisterNodeEvent(resetButton->GetHandle(), NODE_ON_CLICK, NUM_6, nullptr); // NUM_6 = 6
    auto onTouchReset = [](ArkUI_NodeEvent *event) {
        // Trigger logic when the target button (NUM_6 = 6) is clicked.
        if (OH_ArkUI_NodeEvent_GetTargetId(event) == NUM_6) {
            static ArkUI_AnimatorOption *option =  OH_ArkUI_AnimatorOption_Create(NUM_0); // Number of animator animation states.
            OH_ArkUI_AnimatorOption_SetDuration(option, NUM_1000); // NUM_1000 = 1000
            OH_ArkUI_AnimatorOption_SetDelay(option, NUM_0);
            OH_ArkUI_AnimatorOption_SetIterations(option, NUM_4); // NUM_4 = 4
            // Choose a curve based on actual service requirements for OH_ArkUI_AnimatorOption_SetCurve.
            auto curve = OH_ArkUI_Curve_CreateCurveByType(ARKUI_CURVE_EASE); // The animation starts slowly, accelerates, and then slows down towards the end.
            auto stepsCurve = OH_ArkUI_Curve_CreateStepsCurve(NUM_20, true); // Create a steps curve object (NUM_20 = 20).
            OH_ArkUI_AnimatorOption_SetCurve(option, curve);
            OH_ArkUI_AnimatorOption_SetBegin(option, NUM_200); // NUM_200 = 200
            OH_ArkUI_AnimatorOption_SetEnd(option, NUM_100); // NUM_100 = 100
            OH_ArkUI_AnimatorOption_RegisterOnFrameCallback(option, nullptr, [](ArkUI_AnimatorOnFrameEvent *event)
            {
                OH_ArkUI_AnimatorOnFrameEvent_GetUserData(event); // Obtain the custom object from the animation event object.
                auto value = OH_ArkUI_AnimatorOnFrameEvent_GetValue(event); // Obtain the current progress from the animation event object.
                g_animator_button->SetWidth(value);
            });
            OH_ArkUI_Animator_ResetAnimatorOption(animatorHandle, option);
        }
    };
    resetButton->RegisterNodeEventReceiver(onTouchReset);
    // Set the animator pause button.
    auto pauseButton = std::make_shared<ArkUIButtonNode>();
    pauseButton->SetButtonLabel("pause");
    pauseButton->RegisterNodeEvent(pauseButton->GetHandle(), NODE_ON_CLICK, NUM_7, nullptr); // NUM_7 = 7
    auto onTouchPause = [](ArkUI_NodeEvent *event) {
        // Trigger logic when the target button (NUM_7 = 7) is clicked.
        if (OH_ArkUI_NodeEvent_GetTargetId(event) == NUM_7) {
            OH_ArkUI_Animator_Pause(animatorHandle);
        }
    };
    pauseButton->RegisterNodeEventReceiver(onTouchPause);
    // Create a container for storing cancelButton.
    auto cancelButtonColumn = std::make_shared<ArkUIColumnNode>();
    cancelButtonColumn->SetPadding(NUM_10, false); // Set the layout padding (NUM_10 = 10).
    cancelButtonColumn->SetWidth(NUM_300); // NUM_300 = 300
    // Set the animator cancel button.
    auto cancelButton = std::make_shared<ArkUIButtonNode>();
    cancelButton->SetButtonLabel("cancel");
    cancelButton->RegisterNodeEvent(cancelButton->GetHandle(), NODE_ON_CLICK, NUM_8, nullptr); // NUM_8 = 8
    auto onTouchCancel = [](ArkUI_NodeEvent *event) {
        // Trigger logic when the target button (NUM_8 = 8) is clicked.
        if (OH_ArkUI_NodeEvent_GetTargetId(event) == NUM_8) {
            OH_ArkUI_Animator_Cancel(animatorHandle);
        }
    };
    cancelButton->RegisterNodeEventReceiver(onTouchCancel);
    // Set the animator reverse-play button.
    auto reverseButton = std::make_shared<ArkUIButtonNode>();
    reverseButton->SetButtonLabel("reverse");
    reverseButton->RegisterNodeEvent(reverseButton->GetHandle(), NODE_ON_CLICK, NUM_9, nullptr);
    auto onTouchReverse = [](ArkUI_NodeEvent *event) {
        // Trigger logic when the target button (NUM_9 = 9) is clicked.
        if (OH_ArkUI_NodeEvent_GetTargetId(event) == NUM_9) {
            OH_ArkUI_Animator_Reverse(animatorHandle);
        }
    };
    reverseButton->RegisterNodeEventReceiver(onTouchReverse);
    // Mount the button to the column and return the column node.
    column->AddChild(g_animator_text);
    column->AddChild(textNode);
    column->AddChild(button);
    buttoColumn->AddChild(createButton);
    playButtonColumn->AddChild(playButton);
    buttoColumn->AddChild(playButtonColumn);
    buttoColumn->AddChild(finishButton);
    resetButtonColumn->AddChild(resetButton);
    buttoColumn->AddChild(resetButtonColumn);
    buttoColumn->AddChild(pauseButton);
    cancelButtonColumn->AddChild(cancelButton);
    buttoColumn->AddChild(cancelButtonColumn);
    buttoColumn->AddChild(reverseButton);
    column->AddChild(buttoColumn);
    return column;
}
```

![en-us_image_animator](figures/en-us_image_animator.gif)
