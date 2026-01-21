# Overview of Word Selection Service Subsystem

<!--Kit: Basic Services Kit-->
<!--Subsystem: SelectionInput-->
<!--Owner: @no86-->
<!--Designer: @mmwwbb-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

Since API version 20, the word selection service subsystem is available. It provides capabilities for obtaining selected text globally and managing word selection applications.

By calling the APIs provided by this subsystem, you can easily implement the word selection extension ability based on existing applications. With this extension ability, you can capture the text selected by users globally, and then implement your own service logic based on the captured text, such as text translation, content summary, and intelligent expansion. In addition, the word selection service provides comprehensive panel management capabilities, allowing you to create, display, move, hide, and destroy panels. You can customize the UI style and interaction logic of the panel to flexibly display the translation and summary, achieving a smooth experience from selecting text to displaying the intelligent panel. For details about the API description and usage, see [Developing a Word Selection Application](./selection-services-application-guide-sys.md).

## Working Principles

The workflow of the word selection service depends on the collaboration of modules such as the word selection application, application with selected text, system settings application, system service management, multimodal input, and pasteboard service. The following describes these modules and their services:

**Word selection application**: an application that implements the word selection extension ability. After the word selection service successfully launches the selected word selection application, you can listen for the [selectionCompleted](../../reference/apis-basic-services-kit/js-apis-selectionInput-selectionManager-sys.md#onselectioncompleted) event to identify the user action for selecting text, call [getSelectionContent](../../reference/apis-basic-services-kit/js-apis-selectionInput-selectionManager-sys.md#getselectioncontent22) to obtain the selected text, and call [createPanel](../../reference/apis-basic-services-kit/js-apis-selectionInput-selectionManager-sys.md#createpanel) and [show](../../reference/apis-basic-services-kit/js-apis-selectionInput-selectionManager-sys.md#show) to create and display the panel. This process corresponds to step 6 in the following figure. For details about the API description and usage, see [Developing a Word Selection Application](./selection-services-application-guide-sys.md).

**Application with selected text**: an application where text is selected by the user. Currently, the word selection service uses the standard system copy mechanism. Therefore, the word selection service can implement a cross-application word selection without any adaptation or modification performed on the target application. This process corresponds to step 11 in the following figure. However, for some applications that do not support system-level copy operations (such as certain controlled **WebView**s, sandbox applications, or applications that support only internal paste operations), the word selection service cannot obtain the selected text through the standard system copy mechanism. In this case, the word selection service becomes invalid. Therefore, you are advised to use trustlist or blocklist when developing a word selection application and add the target applications that support the word selection service to the trustlist.

**System settings application**: a built-in settings application in the system. The system settings application automatically scans and identifies all applications that have implemented the word selection extension ability, and displays them on the **Settings** > **System** > **Smart text selection** screen for users to select. (If no application is specified, the first word selection application in the list is used by default.) In addition, users can enable or disable the global word selection functionality on the **Smart text selection** screen, and select the trigger mode of the word selection panel (directly triggering the panel after selecting text or triggering the pane after selecting text and pressing **Ctrl**). All configuration items are synchronized to system parameters by the system settings application for other modules to access. This process corresponds to step 2 in the following figure.

**System service management**: a module that manages system services in a unified manner. For the word selection service, this module listens for the changes of the **sys.selection.switch** parameter in the system parameters. If **sys.selection.switch** is set to **on**, the word selection service is started; if set to **off**, the service is terminated.	This process corresponds to steps 1 and 3 in the following figure. For details about system service management, see [System Ability Manager (Samgr)](https://gitcode.com/openharmony/systemabilitymgr_samgr).

**Multimodal input**: a module that processes events input by touchscreen, keyboard, or mouse in a unified manner. The word selection service registers a listener to listen for multimodal input events, captures users' input events from the keyboard, mouse, and touchpad in real time, drives the state machine based on preset rules, and accurately identifies word selection behavior. In addition, the word selection service injects the **CTRL+C** event into the target application through the multimodal input module to simulate the system copy operation. This process corresponds to steps 7, 9, and 10 in the following figure. For details about multimodal input, see [multimodalinput_input](https://gitcode.com/openharmony/multimodalinput_input).

**Pasteboard service**: a core module that manages the pasteboard status and supports global copy and paste functionalities in a unified manner. To meet the requirements of the word selection service, the pasteboard service introduces the word selection flag mechanism. When the flag exists, the pasteboard service does not write the subsequently received content to the system pasteboard, but directly transfers the content to the word selection service, and immediately clears the flag after the transfer is complete. Therefore, the word selection operation does not interfere with the normal copy and paste process. This process corresponds to steps 8, 11, and 12 in the following figure. For details about the pasteboard service, see [Clipboard Service](https://gitcode.com/openharmony/distributeddatamgr_pasteboard).

**Word selection service**: When the word selection service is started, the word selection application selected by the user on the **Smart text selection** screen is started based on the value in the system parameters. In addition, the word selection service listens for parameter changes of the word selection triggering mode to ensure that the configuration takes effect in real time. and also registers a listener to listen for multimodal input events, captures users' input events from the keyboard, mouse, and touchpad in real time, drives the state machine based on preset rules, and accurately identifies word selection behavior. Once the state machine determines that the user performs a word selection operation, the word selection service injects a **CTRL+C** event into the word selection application through the multimodal input module to simulate a system copy operation and trigger a text copy process. At the same time, the word selection service writes a dedicated word selection flag and callback to the pasteboard service for subsequent content interception and transfer. After receiving the **CTRL+C** event, the target application executes the standard copy logic to write the content selected by the user to the system pasteboard, which then checks whether the word selection flag exists. If the flag is valid, the content is not written to the system pasteboard but directly transferred to the word selection service, and the flag is cleared immediately. Finally, the word selection service forwards the obtained text content to the current word selection application, which then completes subsequent processing (such as translation, abstract, and expansion) and creates and displays a custom panel. This process corresponds to steps 4 to 13 in the following figure.

![Schematic diagram of the word selection service](figures/selection-service-schematic.png)

## Capabilities

- Selecting words:

  Supported: holding left button of the mouse or touchpad and moving the cursor, double-click, and triple-click.<br>Unsupported: pressing **CTRL+A** on the keyboard and selecting through a touchscreen.

- Triggering panels:

  A panel can be triggered after the user selects text or presses **Ctrl** upon a text selection. Users can switch between the two modes on **Settings** > **System** > **Smart text selection**.

- Managing panels:

  You can create and manage menu panels and main panels, perform panel operations (such as adding, moving, hiding, and destroying panels), and customize panel content.

- Managing applications:

  Word selection extension ability can be implemented to multiple applications, but only one application can communicate with the word selection service at a time. You can change the word selection application on **Settings** > **System **> **Smart text selection**.

## Constraints

- This service is supported on 2-in-1 devices with external keyboards and mouse devices.

- The maximum length of selected text is 6000 bytes.

- This service can be used on an extended screen, but cannot be used across devices.

- For applications that do not support copy or supports only internal copy and paste, the word selection service is invalid. Therefore, you are advised to configure a blocklist or trustlist when developing a word selection application.
