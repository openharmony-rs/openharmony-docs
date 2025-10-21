# UITest User Guide

<!--Kit: Test Kit-->
<!--Subsystem: Test-->
<!--Owner: @inter515-->
<!--Designer: @inter515-->
<!--Tester: @laonie666-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

The UI test framework provides you with the capabilities of locating UIs and simulating operations, covering key scenarios of UI automation tests, including precise locating of UI controls, UI interaction operations (such as tapping, sliding, and text input), and peripheral behavior simulation (such as keyboard input, mouse operation, touchpad gesture, and stylus action). This helps you develop efficient and reliable UI automation test cases.

## Function Categorization

UITest Framework provides flexible and efficient technical support for UI automation testing by using ArkTS APIs and command lines.

**ArkTS script development capability:**
Provides simple and easy-to-use APIs to meet the requirements of various test scenarios. Common UI interaction operations such as tapping, double-tapping, long pressing, and swiping are supported, helping you quickly develop automation test scripts based on UI interaction logic.

**Command line test capability:**
Supports diversified test operations through command lines, including obtaining the screenshot of the current UI, obtaining the control tree, recording the UI operation process, and injecting UI simulation events.

UITest Framework consists of the client and server.

**Client:**
Includes the cross-language communication layer and IPC module. The main function is to export APIs externally and provide an entry for starting the UI test framework. The client is loaded by the test application and runs in the application process. The cross-language communication layer exports interfaces, processes JSON serialization objects, converts upper-layer ArkTS interfaces and lower-layer C++ interfaces, and parses and verifies parameters. In addition, this module involves the calling of ArkTS callback functions by the C++ layer. Therefore, the cross-language communication layer is responsible for managing and calling ArkTS callback functions.

**Server:**
Runs as an independent process and communicates with the client through IPC. After the server is started, it establishes a connection with the client through broadcast and ensures that the connection is not disconnected through IPC communication. The server listens for the client process status and starts or stops the client process as required. The server processes the core logic of the UI test framework, which is divided into the following two parts:
1. General framework running capability: processes IPC messages, manages processes, C++ interfaces, and error codes, and listens for interface calling.
2. UI test capabilities: parsing accessibility nodes to build a page control tree, control matching and search, operation event construction, multimodal event injection, UI event listening, and screen display control.

## Using ArkTS APIs for UI Testing

This section describes how to use the ArkTS APIs of the UI test framework.

UI tests are based on <!--RP14-->[unit tests](unittest-guidelines.md)<!--RP14End-->. For details about the API definitions and parameter description, see <!--RP13-->[API Reference](../reference/apis-test-kit/js-apis-uitest.md)<!--RP13End-->.

### UI Test Example

The following provides a simple UI test example to describe how to incrementally develop UI tests based on unit test scripts. The following functions are implemented:

1. Invoke the <!--RP1-->[program framework service](../reference/apis-test-kit/js-apis-inner-application-abilityDelegator.md)<!--RP1End--> capability to start the target application and check the application running status.
2. Call the UI test framework capability to perform a tap operation on the page.
3. Add an assertion using the <!--RP2-->[assertion capability](unittest-guidelines.md)<!--RP2End--> to check whether the actual changes on the current page are the same as the expected results.

The development procedure is as follows:

1. Write the Index.ets page code in the main > ets > pages folder as the demo to be tested.
    ```ts
    @Entry
    @Component
    struct Index {
        @State message: string = 'Hello World';
        @State text: string = '';
        build() {
        Row() {
            Column() {
            Text(this.message)
                .fontSize(50)
                .fontWeight(FontWeight.Bold)
            Text("Next")
                .fontSize(50)
                .margin({top:20})
                .fontWeight(FontWeight.Bold)          
                .onClick((event?: ClickEvent) => {
                    if(event){
                        this.text = "after click";
                    }
                })
            .width('100%')
            Text(this.text).margin(15)
            }
        }
        .height('100%')
        }
    }
    ```
2. Create the uitest.test.ets file in the ohosTest > ets > test folder and write the test code.
    ```ts
    import { describe, it, expect, Level } from '@ohos/hypium';
    // Import the test dependencies.
    import { abilityDelegatorRegistry, Driver, ON } from '@kit.TestKit';
    import { UIAbility, Want } from '@kit.AbilityKit';

    const delegator: abilityDelegatorRegistry.AbilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
    export default function abilityTest() {
      describe('ActsAbilityTest', () => {
        it('testUiExample',Level.LEVEL3, async (done: Function) => {
          console.info("uitest: TestUiExample begin");        
          // Initialize the Driver object.
          const driver = Driver.create();
          const bundleName = abilityDelegatorRegistry.getArguments().bundleName;
          // Specify the package name and ability name of the app to be tested. Replace them with the actual ones.
          const want: Want = {
              bundleName: bundleName,
              abilityName: 'EntryAbility'
          }
          // Start the app to be tested.
          await delegator.startAbility(want);
          // Wait until the app is started.
          await driver.waitForIdle(4000,5000);
          // Check whether the ability at the top of the current app is the specified ability.
          const ability: UIAbility = await delegator.getCurrentTopAbility();
          console.info("get top ability");
          expect(ability.context.abilityInfo.name).assertEqual('EntryAbility');

          // Search for the target control based on the specified text Next.
          const next = await driver.findComponent(ON.text('Next'));
          // Tap the target control.
          await next.click();
          await driver.waitForIdle(4000,5000);
          // Assert that the control whose text is after click exists, and confirm that the page change after the operation meets the expectation.
          await driver.assertComponentExist(ON.text('after click'));
          await driver.pressBack();
          done();
        })
      })
    }
    ```

### Control Search and Operation

UITest supports <!--RP3-->[creating a matcher based on multiple attributes](../reference/apis-test-kit/js-apis-uitest.md#on9)<!--RP3End--> to search for controls. You can search for one or more target controls that meet the matching conditions on the current page and return the control object. You can search for target controls inside the scroll component and <!--RP4-->[perform operations on control objects or obtain control attributes](../reference/apis-test-kit/js-apis-uitest.md#component9)<!--RP4End-->.

The following provides an example of control search and operation. Before running the following code, implement the code of the Index.ets page by referring to the UI test example.

  ```ts
  // ohosTest/ets/test/uitest.test.ets
  import { describe, it, TestType, Size, Level } from '@ohos/hypium';
  // Import the test dependencies.
  import { Driver, Component, ON, On } from '@kit.TestKit';

  export default function abilityTest() {
    describe('componentOperationTest', () => {
      /**
       * Search for the control of the Button type and click the control.
       */
      it("componentSearchAndOperation", TestType.FUNCTION, async () => {
        let driver: Driver = Driver.create();
        let button: Component = await driver.findComponent(ON.type('Button'));
        await button.click();
      })

      /**
       * Search for the control of the Scroll type whose text content is 123 based on the relative position.
       */
      it("relativePositioncomponentSearch", TestType.FUNCTION, async () => {
        let driver: Driver = Driver.create();
        let on: On = ON.text('123').within(ON.type('Scroll'));
        let items: Array<Component> = await driver.findComponents(on);
      })

      /**
       * Search for a control of the Image type and zoom in the control with two fingers.
       */
      it("componentPinch", TestType.FUNCTION, async () => {
        let driver: Driver = Driver.create();
        let image: Component = await driver.findComponent(ON.type('Image'));
        await image.pinchOut(1.5);
      })
    })
  }
  ```

### Simulating Touch Operations

UITest supports events such as tap, double-tap, long press, swipe, drag, and multi-finger operations.

The following provides an example of simulating finger operations based on touch coordinates. Before running the following code, implement the code on the Index.ets page by referring to the UI test example.

  ```ts
  // ohosTest/ets/test/uitest.test.ets
  import { describe, it, TestType, Size, Level } from '@ohos/hypium';
  // Import the test dependencies.
  import { Driver, PointerMatrix, UiDirection } from '@kit.TestKit';

  export default function abilityTest() {
    describe('screenOperationTest', () => {
      /**
       * Touch operations on a coordinate-based touchscreen
       */
      it("touchScreenOperation", TestType.FUNCTION, async () => {
        let driver: Driver = Driver.create();
        // Tap
        await driver.click(100,100);
        // Tap the specified screen.
        await driver.clickAt({ x: 100, y: 100, displayId: 0 });
        // Swipe
        await driver.swipe(100, 100, 200, 200, 600);
        // Swipe the specified screen.
        await driver.swipeBetween({x: 100, y: 100, displayId: 0}, {x: 1000, y: 1000, displayId: 0}, 800);
        // Throw
        await driver.fling({x: 100, y: 100},{x: 200, y: 200}, 5, 600);
        // Throw in the specified direction.
        await driver.fling(UiDirection.DOWN, 10000);
        // Drag
        await driver.drag(100, 100, 200, 200, 600);
        // Specify the screen ID and the long press duration before dragging.
        await driver.dragBetween( {x: 100, y: 100, displayId: 0}, {x: 1000, y: 1000, displayId: 0}, 800, 1500); 
        // Multi-finger operation. Specify two fingers and specify two coordinates for each finger to swipe.
        let pointers: PointerMatrix = PointerMatrix.create(2, 2);
        pointers.setPoint(0, 0, {x: 100, y: 100});
        pointers.setPoint(0, 1, {x: 200, y: 100});
        pointers.setPoint(1, 0, {x: 100, y: 200});
        pointers.setPoint(1, 1, {x: 200, y: 200});
        await driver.injectMultiPointerAction(pointers);
      })
    })
  }
  ```
### Page Loading

After interacting with a page, you can wait for a specified period of time for a control to appear or wait until the page is idle to determine whether the page redirection is complete.

The following is an example of page loading. Before running the following code, implement the code of the Index.ets page by referring to UI Test Example.

  ```ts
  // ohosTest/ets/test/uitest.test.ets
  import { describe, it, Level, TestType, Size } from '@ohos/hypium';
  // Import the test dependencies.
  import { abilityDelegatorRegistry, Driver, ON } from '@kit.TestKit';

  const delegator: abilityDelegatorRegistry.AbilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
  // Specify the package name and ability name of the app under test. Replace them with the actual ones.
  const bundleName: string = 'com.uitestScene.acts'
  const abilityName: string = 'com.uitestScene.acts.MainAbility'
  export default function abilityTest() {
    describe('ActsAbilityTest', () => {
      it('testWaitForComponent_static', TestType.FUNCTION | Size.MEDIUMTEST | Level.LEVEL3, async (): Promise<void> => {
        let driver = Driver.create();
        // Start the target app.     
        await delegator.executeShellCommand(`aa start -b ${bundleName} -a ${abilityName}`).then(result => {
          console.info(`UITestCase, start abilityFinished: ${result}`)
        }).catch((err: Error) => {
            console.error(`UITestCase, start abilityFailed: ${err}`)
        })
        // Check whether the target app is started by waiting for the specified control on the home screen of the target app to appear.
        let button = await driver.waitForComponent(ON.text('StartAbility Success!'), 1000);
      })
    })
  }
  ```

### Simulating Text Input

UITest allows you to enter text at a specified coordinate or control. <!--RP5-->[Specify the input mode](../reference/apis-test-kit/js-apis-uitest.md#inputtextmode20)<!--RP5End-->: whether to enter text in copy-paste mode or in append mode.

The following provides examples of text input based on controls and coordinates. Before running the following code, implement the code on the Index.ets page by referring to UI Test Example.

  ```ts
  // ohosTest/ets/test/uitest.test.ets
  import { describe, it, TestType, Size, Level } from '@ohos/hypium';
  // Import the test dependencies.
  import { Driver, ON } from '@kit.TestKit';

  export default function abilityTest() {
    describe('inputTextTest', () => {
      /**
       * Enter text based on controls. The interface is called to clear the content in the text box and enter the specified text.
       * If the entered text does not contain Chinese characters or special characters and the text length does not exceed 200 characters, the text is entered character by character by default.
       */
      it('componentInputText', TestType.FUNCTION, async () => {
        let driver = Driver.create();
        let input = await driver.findComponent(ON.type('TextInput'));
        await input.inputText('abc');
      })
      /**
       * Input text based on controls. The text is injected in copy-paste mode.
       * Input text in append mode. That is, the original content is not cleared when you input text.
       */
      it('componentInputTextAddition', TestType.FUNCTION, async () => {
        let driver = Driver.create();
        let input = await driver.findComponent(ON.type('TextInput'));
        await input.inputText('abc', {paste: true, addition: true});
      })

      /**
       * Input text based on coordinates. Click a specified position to make the text box focus, and enter the specified text at the cursor.
       * If the input text does not contain Chinese characters or special characters and the text length does not exceed 200 characters, the text is entered letter by letter by default.
       */
      it('pointInputText', TestType.FUNCTION | Size.MEDIUMTEST | Level.LEVEL3, async () => {
        let driver = Driver.create()
        let input = await driver.findComponent(ON.type('TextInput'))
        let center = await input.getBoundsCenter()
        await driver.inputText(center, 'abc')
      })

      /**
       * Input text based on coordinates. The text is injected in copy-paste mode.
       * Input text in append mode. That is, after you click a specified position to make the text box focus, the cursor is moved to the end of the original text.
       */
      it('pointInputTextAddition', TestType.FUNCTION | Size.MEDIUMTEST | Level.LEVEL3, async () => {
        let driver = Driver.create()
        let input = await driver.findComponent(ON.type('TextInput'))
        let center = await input.getBoundsCenter()
        await driver.inputText(center, '123', {paste: true, addition: true})
      })

      /**
       * Input text based on coordinates. The text is injected in copy-paste mode.
       * Input text in append mode. That is, after the input box is focused by tapping the specified position, the cursor is moved to the end of the original text and then the text is input.
       * If the input content contains Chinese characters or special characters, the text can be input only in copy-paste mode. The paste field does not take effect.
       */
      it('pointInputTextChinese', TestType.FUNCTION | Size.MEDIUMTEST | Level.LEVEL3, async () => {
        let driver = Driver.create()
        let input = await driver.findComponent(ON.type('TextInput'))
        let center = await input.getBoundsCenter()
        await driver.inputText(center, 'Hello', {paste: false, addition: true})
      })
    })
  }
  ```
### Screenshot

> **NOTE**
> 1. Specifies the path for storing the screenshot. The path must be the <!--RP6-->[sandbox path](../file-management/app-sandbox-directory.md)<!--RP6End--> of the current application.
> 2. <!--RP7-->[APL level](../security/AccessToken/app-permission-mgmt-overview.md)<!--RP7End--> of HAP is set to normal, which requires the application sandbox path of the user-level encryption area. The file needs to be saved in the subdirectory for storing persistent data of the application on the device.

The following example shows how to take a screenshot, specify the screen ID and the area to be captured, and save the screenshot to a specified path. Before running the following code, implement the code of the Index.ets page by referring to UI Test Example. In the multi-screen scenario, if you want to take a screenshot of a specified screen, you can call the API of the display module to <!--RP8-->[obtain the display object](../displaymanager/screenProperty-guideline.md)<!--RP8End--> and <!--RP9-->[obtain screen-related attributes](../displaymanager/screenProperty-guideline.md)<!--RP9End-->.

  ```ts
  // ohosTest/ets/test/uitest.test.ets
  import { describe, it, TestType, Size, Level } from '@ohos/hypium';
  // Import the test dependencies.
  import { Driver } from '@kit.TestKit';
  import { display } from '@kit.ArkUI';

  export default function abilityTest() {
    describe('screenCaptureTest', () => {
      /**
       * Capture the screen of a specified area and save the screenshot to a specified path.
       */
      it('screenCapture', TestType.FUNCTION, async () => {
        let driver = Driver.create();
        // Application sandbox path. el2 indicates the user-level encryption area, and base indicates the subdirectory for storing persistent data of the application on the device.
        //Replace it with the actual path.
        let savePath = '/data/storage/el2/base/cache/1.png';
        let res = await driver.screenCapture(savePath, {left: 0, top: 0, right: 100, bottom: 100});
      })

      /**
       * Capture the full screen of a specified screen ID and save the screenshot to a specified path.
       */
      it('screenCapWithId', TestType.FUNCTION | Size.MEDIUMTEST | Level.LEVEL3, async () => {
        let driver = Driver.create();
        // Obtain the default screen object.
        let disPlay = display.getDefaultDisplaySync();
        let savePath = '/data/storage/el2/base/cache/1.png'
        let res = await driver.screenCap(savePath, disPlay.id);// Obtaining the Default Screen ID
      })
    })
  }
  ```


### UI Event Listening

The following provides an example of listening to UI events. You can set the listening callback function to listen to the appearance of controls such as toast and dialog, and perform the next operation after the event occurs. Before running the following code, implement the code of the Index.ets page by referring to UI Test Example.

  ```ts
  // ohosTest/ets/test/uitest.test.ets
  import { describe, it, TestType, Size, Level } from '@ohos/hypium';
  // Import the test dependencies.
  import { Driver, UIElementInfo } from '@kit.TestKit';

  export default function abilityTest() {
    describe('observerTest', () => {
      // Listen to the appearance of the toast control.
      it("toastObserver", TestType.FUNCTION, async () => {
        let driver = Driver.create();
        let observer = driver.createUIEventObserver();
        let callback = (uiElementInfo : UIElementInfo) => {
          let bundleName = uiElementInfo.bundleName;
          let text = uiElementInfo.text;
          let type = uiElementInfo.type;
        }
        observer.once('toastShow', callback);
      })
    })
  }
  ```

### Simulating Keyboard and Mouse Operations

The following provides examples of simulating keyboard and mouse operations, including keyboard key pressing, composite key pressing, mouse clicking, moving, dragging, and composite operations. Before running the following code, implement the code of the Index.ets page by referring to UI Test Example.

  ```ts
  // ohosTest/ets/test/uitest.test.ets
  import { describe, it, TestType, Size, Level } from '@ohos/hypium';
  // Import the test dependencies.
  import { Driver, MouseButton } from '@kit.TestKit';
  import { KeyCode } from '@ohos.multimodalInput.keyCode';

  export default function abilityTest() {
    describe('KeyboardMouseTest', () => {
      // Simulate keyboard input and composite key input.
      it('keyBoardOperation', TestType.FUNCTION | Size.MEDIUMTEST | Level.LEVEL3, async () => {
        let driver = Driver.create();
        // Simulate keyboard input (injecting the back key).
        await driver.triggerKey(KeyCode.KEYCODE_BACK);
        // Simulate composite key input (injecting the save composite key).
        await driver.triggerCombineKeys(KeyCode.KEYCODE_CTRL_LEFT,  KeyCode.KEYCODE_S);
      })

      // Simulate left mouse button click, mouse movement, and mouse dragging.
      it('mouseOperation', TestType.FUNCTION | Size.MEDIUMTEST | Level.LEVEL3, async () => {
        let driver = Driver.create();
        // Simulate left mouse button click.
        await driver.mouseClick({x: 100, y: 100}, MouseButton.MOUSE_BUTTON_LEFT); 
        // Simulate mouse movement.
        await driver.mouseMoveTo({x: 100, y: 100});
        // Simulate mouse dragging.
        await driver.mouseDrag({x: 100, y: 100}, {x: 200, y: 200}, 600);
      })

      // Simulate keyboard and mouse operations.
      it('combinedOperation', TestType.FUNCTION | Size.MEDIUMTEST | Level.LEVEL3, async () => {
        let driver = Driver.create();
        // Press the left Ctrl key and scroll the mouse wheel.
        await driver.mouseScroll({x:100, y:100}, true, 30, KeyCode.KEYCODE_CTRL_LEFT);
        // Press the left Ctrl key and hold down the left mouse button.
        await driver.mouseLongClick({x:100, y:100}, MouseButton.MOUSE_BUTTON_LEFT, KeyCode.KEYCODE_CTRL_LEFT);
      })
    })
  }
  ```

### Window Search and Operations
The following provides an example of searching for and operating a window. You can search for a window based on window attributes and perform operations such as minimizing the window. Before running the following code, refer to the UI test example to implement the code on the Index.ets page.

  ```ts
  // ohosTest/ets/test/uitest.test.ets
  import { describe, it, TestType, expect } from '@ohos/hypium';
  // Import the test dependencies.
  import { Driver } from '@kit.TestKit';
  const DeviceErrorCode = 17000005;

  export default function abilityTest() {
    describe('windowOperationTest', () => {
      // Search for an active window based on specified conditions and minimize the window.
      it("windowSearchAndOperation", TestType.FUNCTION, async () => {
        let driver = Driver.create();
        try {
          let window = await driver.findWindow({active: true});
          await window.minimize();
        } catch (error) {
          // If the minimize API is called to operate a window on a device that does not support window operations, the 17000005 error code is returned.
          console.log(`$ windowSearchAndOperation error is: ${JSON.stringify(error)}`);
          expect(error.code).assertEqual(DeviceErrorCode);
        }
      })
    })
  }
  ```

### Simulating Touchpad Operations
The following code snippet simulates the touchpad operations of swiping up with three fingers to return to the home screen and swiping down with three fingers to restore the app window. Before running the following code, refer to the UI test example to implement the Index.ets page code.

  ```ts
  // ohosTest/ets/test/uitest.test.ets
  import { describe, it, TestType, Size, Level, expect } from '@ohos/hypium';
  // Import the test dependencies.
  import { Driver, UiDirection } from '@kit.TestKit';
  const DeviceErrorCode = 17000005;

  export default function abilityTest() {
    describe('touchPadOperationTest', () => {
      // In the PC/2-in-1 scenario, simulate the operation of swiping up with three fingers on the touchpad (returning to the home screen) and swiping down with three fingers on the touchpad (restoring the app window).
      it('touchPadOperation', TestType.FUNCTION | Size.MEDIUMTEST | Level.LEVEL3, async () => {
        let driver = Driver.create();
        try {
          // Swipe up with three fingers to return to the home screen.
          await driver.touchPadMultiFingerSwipe(3, UiDirection.UP);
          // Swipe down with three fingers to restore the app window.
          await driver.touchPadMultiFingerSwipe(3, UiDirection.DOWN);
        } catch (error) {
          // If this method is called on a device that does not support touchpad operations, the 17000005 error code will be thrown.
          console.log(`$ windowSearchAndOperation error is: ${JSON.stringify(error)}`);
          expect(error.code).assertEqual(DeviceErrorCode);
        }
      })
    })
  }

  ```

### Simulating Stylus Operations
The following provides examples of stylus simulation operations, including tapping and swiping. You can set the pressure value during the operations. Before running the following code, implement the code of the Index.ets page by referring to the UI test example.

  ```ts
  // ohosTest/ets/test/uitest.test.ets
  import { describe, it, TestType, Size, Level } from '@ohos/hypium';
  // Import the test dependencies.
  import { Driver } from '@kit.TestKit';

  export default function abilityTest() {
    describe('penOperationTest', () => {
      // Simulate stylus operations, including tapping, double-tapping, long pressing, and swiping.
      it('penOperation', TestType.FUNCTION | Size.MEDIUMTEST | Level.LEVEL3, async () => {
        let driver = Driver.create();
        // Stylus tapping
        await driver.penClick({x: 100, y: 100});
        // Stylus double-tapping
        await driver.penDoubleClick({x: 100, y: 100});
        // Stylus long pressing
        await driver.penLongClick({x: 100, y: 100}, 0.5);
        // Stylus swiping
        await driver.penSwipe({x: 100, y: 100}, {x: 100, y: 500}, 600, 0.5);
      })
    })
  }
  ```

### Simulating Crown Operations
The following provides an example of simulating crown operations, including clockwise and counterclockwise rotation. Before running the following code, implement the code of the Index.ets page by referring to the UI test example.

  ```ts
  // ohosTest/ets/test/uitest.test.ets
  import { describe, it, TestType, Size, Level, expect } from '@ohos/hypium';
  // Import the test dependencies.
  import { Driver } from '@kit.TestKit';
  const CapabilityCode = 801;

  export default function abilityTest() {
    describe('crownRotateTest', () => {
      // Simulate the watch crown to rotate smoothly or counterclockwise.
      it('crownRotate', TestType.FUNCTION | Size.MEDIUMTEST | Level.LEVEL3, async () => {
        let driver = Driver.create();
        try {
          // Rotate 50 ticks clockwise at a speed of 30 ticks per second.
          await driver.crownRotate(50, 30);
          // Rotate 20 ticks counterclockwise at a speed of 30 ticks per second.
          await driver.crownRotate(-20, 30);
        } catch (error) {
          // driver.crownRotate is valid only on smart watches. If it is called on other devices, error code 801 will be returned.
          console.log(`$ testCrownRotate error is: ${JSON.stringify(error)}`);
          expect(error.code).assertEqual(CapabilityCode);
        }
      })
    })
  }
  ```

### Screen Display Operations
The following shows how to obtain screen attributes such as the screen size and resolution, and perform operations such as screen wakeup and rotation. Before running the following code, refer to the UI test example to implement the code on the Index.ets page.

  ```ts
  // ohosTest/ets/test/uitest.test.ets
  import { describe, it, TestType, Size, Level } from '@ohos/hypium';
  // Import the test dependencies.
  import { Driver, Point } from '@kit.TestKit';
  
  export default function abilityTest() {
    describe('crownRotateTest', () => {
      // Obtain screen attributes and perform screen operations.
      it('displayOperation', TestType.FUNCTION | Size.MEDIUMTEST | Level.LEVEL3, async () => {
        let driver = Driver.create();
        // Obtain the screen size.
        let size: Point = await driver.getDisplaySize();
        // Obtain the screen resolution.
        let density: Point = await driver.getDisplayDensity();
        // Wake up the screen.
        await driver.wakeUpDisplay();
        // Rotate the screen clockwise by 90 degrees.
        await driver.setDisplayRotation(DisplayRotation.ROTATION_90);
      })
    })
  }
  ```

## Performing UI Tests Using Commands

During development, you can use commands to quickly perform test operations such as taking screenshots, recording UI operations, injecting UI simulation operations, and obtaining the control tree, improving test efficiency.

### Environment Requirements

The environment for OpenHarmony Device Connector (hdc) has been set up. For details, see <!--RP10-->[Environment Setup](../dfx/hdc.md#environment-setup)<!--RP10End-->. The devices are properly connected and **hdc shell** is executed.

### Command List
| Envelope command.           | Parameter  |Description                             |
|---------------|---------------------------------|---------------------------------|
| help          | - |  Displays the commands supported by the UITest tool.           |
| screenCap       |[-p] [-d]| Takes a screenshot.<br> |
| dumpLayout      |[-p] \<-i \| -a \| -b \| -w \| -m \| -d>| Obtains the control tree.<br> |
| uiRecord        | \<record \| read>|Records UI operations.<br> **record**: starts recording. The current UI operations are recorded in /data/local/tmp/record.csv. Press Ctrl+C to stop recording.<br> **read**: reads and prints recorded data.<br> |
| uiInput       | \<help \| click \| doubleClick \| longClick \| fling \| swipe \| drag \| dircFling \| inputText \| keyEvent \| text>| Injects simulated UI operations.<br> |
| --version | - |Obtains the version information about the current UITest tool.|
| start-daemon| - | Starts the UITest test process.|

### Taking Screenshots

| Parameter   |   Level-2 Parameter  |Description      |
|---------|---------|------------|
| -p | \<savePath\> | Specifies the storage path and file name. The file can be stored only in /data/local/tmp/. The default storage path is /data/local/tmp, and the file name is Timestamp+.png.|
| -d | \<displayId\> | Obtains the screenshot of the screen with the specified ID in the multi-screen scenario.<br> **Note**: This command is supported since API version 20.|

```bash
# Specify the file name in the format of Timestamp + .png.
hdc shell uitest screenCap
# Save the file in /data/local/tmp/.
hdc shell uitest screenCap -p /data/local/tmp/1.png
```

### Obtains the control tree.
| Parameter   | Level-2 Parameter  |  Description      |
|---------|---------|-----------|
| -p | \<savePath\> | Specifies the storage path and file name. The file can be stored only in /data/local/tmp/. The default storage path is /data/local/tmp, and the file name is Timestamp+.json.|
| -i | - | Disables filtering of invisible components and window merging.|
| -a | - | Saves the BackgroundColor, Content, FontColor, FontSize, and extraAttrs attributes of controls.<br>**Note**: By default, the preceding attributes are not saved. **-a and -i cannot be used at the same time.**|
| -b | \<bundleName\> | Obtains the control tree information of the target window corresponding to the specified package name.|
| -w | \<windowId\>  | Obtains the control tree information of the target window with the specified ID.<br> **Note**:<br>You can use the hidumper tool to obtain the application window information, including the ID of the window corresponding to the application. <!--RP11-->[Obtaining Application Window Information](../dfx/hidumper.md#obtaining-application-window-information) <!--RP11End-->|
| -m | \<true\|false\> | Specifies whether to merge window information when obtaining the control tree information. true indicates that window information is merged, and false indicates that window information is not merged. If this parameter is not set, the default value true is used.|
| -d | \<displayId\>  | Obtains the control tree of the screen with the specified ID in the multi-screen scenario.<br> **Note**:<br> 1. This command is supported since API version 20.<br>2. You can use the hidumper tool to obtain the application window information, including the display ID of the application window. For details, see [Obtaining Application Window Information](../dfx/hidumper.md)<!--RP11End-->.|

```bash
# Save the file in /data/local/tmp/.
hdc shell uitest dumpLayout -p /data/local/tmp/1.json
```

### Recording UI Operations
>**Description**
>
> During the recording, you should perform the next operation after the recognition result of the current operation is displayed in the command line.

**Parameters**
| Parameter  | Level-2 Parameter   |   Description             |
|-------|--------------|-----------------|
| -W    | \<true/false> |  Whether to save the component information corresponding to the operation coordinates to the **/data/local/tmp/record.csv** file during recording. The value **true** means to save the component information, and **false** means to record only the coordinate information. The default value is **true**.<br> **Note**: This command is supported since API version 20.|
| -l    | - |  The current layout information is saved after each operation. The file path is **/data/local/tmp/layout_Start timestamp of the recording_Operation ID.json**.<br> **Note**: This command is supported since API version 20.|
| -c    | \<true/false> | Whether to print the recorded operation event information to the console. true indicates that the information is printed, and false indicates that the information is not printed. If this parameter is not set, the default value true is used.<br> **Note**: This command is supported since API version 20.|

```bash
# Record the operations on the current page to **/data/local/tmp/record.csv**. To stop the recording, press **Ctrl+C**.
hdc shell uitest uiRecord record
# Only the coordinates of the operations are recorded during recording, and the target control is not matched.
hdc shell uitest uiRecord record -W false
# After each operation, the page layout is saved in /data/local/tmp/layout_Start timestamp of the recording _Operation ID.json.
hdc shell uitest uiRecord record -l
# Do not print the recorded operation event information to the console.
hdc shell uitest uiRecord record -c false
# Read and print record data.
hdc shell uitest uiRecord read
```

The fields in the recording data and their meanings are as follows:

 ```json
 {
   "ABILITY": "com.ohos.launcher.MainAbility", // Ability name of the application that is operated
   "BUNDLE": "com.ohos.launcher", // Package name of the app to be operated.
   "CENTER_X ": "", // Reserved field, which is not used currently.
   "CENTER_Y ": "", // Reserved field, which is not used currently.
   "EVENT_TYPE": "pointer", // Operation type.
   "LENGTH": "0", // Total length.
   "OP_TYPE": "click", // Event type. Currently, click, double-click, long-press, drag, pinch, swipe, and fling types are supported.
   "VELO": "0.000000", // Hands-off velocity.
   "direction.X": "0.000000",// Movement along the x-axis.
   "direction.Y": "0.000000", // Movement along the y-axis.
   "duration": 33885000.0, // Gesture duration.
   "fingerList": [{
     "LENGTH": "0", // Total length.
     "MAX_VEL": "40000", // Maximum velocity.
     "VELO": "0.000000", // Hands-off velocity.
     "W1_BOUNDS": "{"bottom":361,"left":37,"right":118,"top":280}", // Boundary of the start control.
     "W1_HIER": "ROOT,3,0,0,0,0,0,0,0,0,5,0,0,0,0,0,0,0", // Page level of the start control.
     "W1_ID": "", // ID of the starting component.
     "W1_Text": "", // Text of the starting component.
     "W1_Type": "Image", // Type of the starting component.
     "W2_BOUNDS": "{"bottom":361,"left":37,"right":118,"top":280}", // Boundary of the end control.
     "W2_HIER": "ROOT,3,0,0,0,0,0,0,0,0,5,0,0,0,0,0,0,0", // Page level of the end control.
     "W2_ID": "", // ID of the ending component.
     "W2_Text": "", // Text of the ending component.
     "W2_Type": "Image", // Type of the ending component.
     "X2_POSI": "47", // X coordinate of the ending point.
     "X_POSI": "47", // X coordinate of the starting point.
     "Y2_POSI": "301", // Y coordinate of the ending point.
     "Y_POSI": "301", // Y coordinate of the starting point.
     "direction.X": "0.000000", // X Movement amount in the direction.
     "direction.Y": "0.000000" // Movement along the y-axis.
   }],
   "fingerNumber": "1" // Number of fingers.
 }
 ```
### Injecting Simulated UI Operations

| Parameter  |  Description             |
|------|----------------|
| help   |Displays help information about the uiInput commands.|
| click   |  Simulates a tap operation. For details, see **Examples of Using uiInput-click/doubleClick/longClick**.     |
| doubleClick   |  Simulates a double-tap operation. For details, see **Examples of Using uiInput click/doubleClick/longClick**.     |
| longClick   |Simulates a touch and hold operation. For details, see **Examples of Using uiInput click/doubleClick/longClick**.    |
| fling   | Simulates a flick operation. That is, the page keeps scrolling after the operation is complete. For details, see **Examples of Using uiInput fling**.  |
| swipe   |  Simulates a swipe operation. For details, see **Examples of Using uiInput swipe/drag**.    |
| drag   | Simulates a drag operation. For details, see **Examples of Using uiInput swipe/drag**.    |
| dircFling   |  Simulates a swipe operation in a specified direction. For details, see **Examples of Using uiInput dircFling**.    |
| inputText   |  Simulates a text input operation in an input box by specifying the coordinates. For details, see **Examples of Using uiInput inputText**.                  |
| text   |  Simulates a text input operation in an input box at the current focus without specifying the coordinates. For details, see **Examples of Using uiInput text**.<br> **Note**: This command is supported since API version 18.|
| keyEvent   | Simulates a physical key event (such as the keyboard, power key, back key, and home key) and a combination key operation. For details, see **Examples of Using uiInput keyEvent**.    |


- Example of Using click/doubleClick/longClick

| Parameter   | Mandatory| Description           |
|---------|------|-----------------|
| point_x | Yes     | The x-coordinate point to click.|
| point_y | Yes      | The y-coordinate point to click.|

```shell
# Execute the click event.
hdc shell uitest uiInput click 100 100

# Execute the double-click event.
hdc shell uitest uiInput doubleClick 100 100

# Execute a long-click event.
hdc shell uitest uiInput longClick 100 100
```

- Example of Running the uiInput fling Command

| Parameter | Mandatory            | Description              |
|------|------------------|-----------------|
| from_x   | Yes               | The x-coordinate of the start point.|
| from_y   | Yes               | The y-coordinate of the start point.|
| to_x   | Yes               | The x-coordinate of the stop point.|
| to_y   | Yes               | The y-coordinate of the stop point.|
| swipeVelocityPps_   | No     | Swipe speed, in px/s. The value ranges from 200 to 40000.<br> Default value: **600** If the value is out of the range, the default value is used.|
| stepLength_   | No| Swipe step, in px. The default value is the swipe distance divided by 50.<br> **NOTE**<br> The swipe distance is calculated based on the start and end coordinates specified by the input parameters.<br> To achieve better simulation effect, you are advised to use the default value. |


```shell  
# Execute the fling event. The default value of stepLength_ is used.
hdc shell uitest uiInput fling 10 10 200 200 500 
```

- Example of Running the uiInput swipe/drag Command

| Parameter | Mandatory            | Description              |
|------|------------------|-----------------|
| from_x   | Yes               | The x-coordinate of the start point.|
| from_y   | Yes               | The y-coordinate of the start point.|
| to_x   | Yes               | The x-coordinate of the stop point.|
| to_y   | Yes               | The y-coordinate of the stop point.|
| swipeVelocityPps_   | No     | Swipe speed, in px/s. The value ranges from 200 to 40000.<br> Default value: **600** If the value is out of the range, the default value is used.|

```shell  
# Execute the swipe event.
hdc shell uitest uiInput swipe 10 10 200 200 500

# Execute the drag event.
hdc shell uitest uiInput drag 10 10 100 100 500 
```

- Example of Running the uiInput dircFling Command

| Parameter            | Mandatory      | Description|
|-------------------|-------------|----------|
| direction         | No | Fling direction, which can be **0**, **1**, **2**, or **3**. The default value is **0**.<br> The value **0** indicates leftward fling, **1** indicates rightward fling, **2** indicates upward fling, and **3** indicates downward fling.   |
| swipeVelocityPps_ | No | Swipe speed, in px/s. The value ranges from 200 to 40000.<br> Default value: **600** If the value is out of the range, the default value is used.   |
| stepLength        | No | Swipe step, in px.<br> **Default value**: If the swipe direction is 0 or 1, the default value is the screen width divided by 200. If the swipe direction is 2 or 3, the default value is the screen height divided by 200. To achieve better simulation effect, you are advised to use the default value.|

```shell  
# Execute the leftward fling event.
hdc shell uitest uiInput dircFling 0 500
# Execute the rightward fling event.
hdc shell uitest uiInput dircFling 1 600
# Execute the upward fling event.
hdc shell uitest uiInput dircFling 2 
# Execute the downward fling event.
hdc shell uitest uiInput dircFling 3
```

- Example of Running the uiInput inputText Command

| Parameter            | Mandatory      | Description|
|------|------------------|----------|
| point_x   | Yes               | The x-coordinate of the input box.|
| point_y   | Yes               | The y-coordinate of the input box.|
| text      | Yes               | Text in the input box. |

```shell  
# Execute the input text event.
hdc shell uitest uiInput inputText 100 100 hello 
```

- Example of Running the uiInput text Command

| Parameter            | Mandatory      | Description|
|--------|-------------------|----------------|
| text   | Yes               | Text in the input box. |

```shell  
# Execute the text input in the text box at the focused position. If the current focused position does not support text input, no effect is displayed.
hdc shell uitest uiInput text hello
```

- Example of Running the uiInput keyEvent Command

| Parameter            | Mandatory      | Description                                                                                                                             |
|------|------|---------------------------------------------------------------------------------------------------------------------------------|
| keyID1   | Yes   | ID of the physical key. The value can be Back, Home, Power, or [KeyCode key code value](../reference/apis-input-kit/js-apis-keycode.md#keycode).<!--RP12End--><br>When the value is set to **Back**, **Home**, or **Power**, combination keys are not supported.<br>Currently, the Caps Lock key (**KeyCode**=**2074**) does not take effect. Use composition keys to input uppercase letters. For example, press **Shift+V** to input uppercase letter V.|
| keyID2    | No   | ID of the physical key. The value can be [KeyCode key code value](../reference/apis-input-kit/js-apis-keycode.md#keycode).<!--RP12End-->. This parameter is left empty by default.|
| keyID3    | No   | ID of the physical key. The value can be [KeyCode key code value](../reference/apis-input-kit/js-apis-keycode.md#keycode).<!--RP12End-->. This parameter is left empty by default.|

```shell  
# Back to home page.
hdc shell uitest uiInput keyEvent Home
# Return.
hdc shell uitest uiInput keyEvent Back
# Perform a key combination to copy and paste text.
hdc shell uitest uiInput keyEvent 2072 2038
# Input the lowercase letter v.
hdc shell uitest uiInput keyEvent 2038
# Input the uppercase letter V.
hdc shell uitest uiInput keyEvent 2047 2038
```

### Obtain the version information.

```bash
hdc shell uitest --version
```
### Starting the UITest test process

>**Description**
>
> Only the test HAP started by the ability aa test can call the Uitest capability, and the <!--RP7-->[APL level](../security/AccessToken/app-permission-mgmt-overview.md)<!--RP7End--> of the test HAP must be normal.

```shell  
hdc shell uitest start-daemon
```


<!--Del-->
## UI test script instance

### Searching for Specified Components
For details about how to search for a component in an application UI by specifying the attributes of the component, see [Example of Searching for Specified Components](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Project/Test/uitest/entry/src/ohosTest/ets/test/findCommentExampleTest/Component/findCommentExample.test.ets).

### Simulating Click Events
For details about how to simulate a click event, a long-click event or a double-click event, see [Example of Simulating Click Events](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Project/Test/uitest/entry/src/ohosTest/ets/test/operationExampleTest/ui/clickEvent.test.ets).

### Simulating Mouse Events
For details about how to simulate a mouse left-click event, a mouse right-click event, or a mouse scroll wheel event, see [Example of Simulating Mouse Events](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Project/Test/uitest/entry/src/ohosTest/ets/test/operationExampleTest/ui/MouseEvent.test.ets).

### Simulating Input Events
For details about how to simulate Chinese and English text input, see [Example of Simulating Text Input Events](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Project/Test/uitest/entry/src/ohosTest/ets/test/operationExampleTest/ui/InputEvent.test.ets).

### Simulating Screenshot Events
For details about how to simulate capturing a screenshot (in a specified area), see [Example of Simulating Screenshot Events](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Project/Test/uitest/entry/src/ohosTest/ets/test/operationExampleTest/ui/ScreenCapEvent.test.ets).

### Simulating Fling Events
For details about how to simulate a fling event (the finger leaves the screen after swiping), see [Example of Simulating Fling Events](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Project/Test/uitest/entry/src/ohosTest/ets/test/operationExampleTest/ui/FlingEvent.test.ets).

### Simulating Swipe Events
For details about how to simulate a swipe event (the finger stays on the screen after swiping), see [Example of Simulating Swipe Events](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Project/Test/uitest/entry/src/ohosTest/ets/test/operationExampleTest/ui/SwipeEvent.test.ets).

### Simulating Pinch Events
For details about how to simulate a zoom-in and zoom-out operation on pictures, see [Example of Simulating Pinch Events](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Project/Test/uitest/entry/src/ohosTest/ets/test/operationExampleTest/ui/PinchEvent.test.ets).

### Simulating Scroll Events
For details about how to simulate components scrolling, see [Example of Simulating Scroll Events](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Project/Test/uitest/entry/src/ohosTest/ets/test/operationExampleTest/ui/ScrollerEvent.test.ets).

### Searching for Specified Windows
For details about how to search for an application window based on the bundle name of the application, see [Example of Searching for Specified Windows](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Project/Test/uitest/entry/src/ohosTest/ets/test/findCommentExampleTest/window/findWindowExample.test.ets).

### Simulating Window Move Events
For details about how to simulate moving a window to a specified position, see [Example of Simulating Window Move Events](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Project/Test/uitest/entry/src/ohosTest/ets/test/operationExampleTest/window/MoveToEvent.test.ets).

### Simulating Window Size Adjustments
For details about how to simulate a window size adjustment and direction specification, see [Example of Simulating Window Size Adjustments](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Project/Test/uitest/entry/src/ohosTest/ets/test/operationExampleTest/window/ReSizeWindow.test.ets).
<!--DelEnd-->

## Common issues

### What should I do if the failure log contains "uitest-api does not allow calling concurrently"?

**Description**

The UI test case fails to be executed. The HiLog file contains the error message "uitest-api does not allow calling concurrently".

**Possible Causes**

1. In the test case, the **await** operator is not added to the asynchronous API provided by the UI test framework.
2. The UI test case is executed in multiple processes. As a result, multiple UI test processes are started. The framework does not support multi-process invoking.

**Solution**

1. Check the case implementation and add the **await** operator to the asynchronous API.
2. Do not execute UI test cases in multiple processes.

### What should I do if the failure log contains "does not exist on current UI! Check if the UI has changed after you got the widget object"?

**Problem**

The UI test case fails to be executed. The HiLog file contains the error message "does not exist on current UI! Check if the UI has changed after you got the widget object."

**Possible Causes**

After the target component is found in the code of the test case, the device UI changes, resulting in loss of the found component and inability to perform emulation.

**Solution**

Run the UI test case again to ensure that the control exists on the screen during the simulation operation.

### What should I do if he failure log contains the " Cannot connect to AAMS, RET_ERR_CONNECTION_EXIST" error information?

**Problem**

The UI test case fails to be executed. The hilog log contains the error message "Cannot connect to AAMS, RET_ERR_CONNECTION_EXIST".

**Possible Causes**

Other test tools that depend on the UI test framework are used during the execution of the test case.

**Solution**

Close the test tools that depend on the UI test framework or restart the device.
