# Node-API

- [Getting Started with the NDK](ndk-development-overview.md)
- [Creating an NDK Project](create-with-ndk.md)
- Building an NDK Project
  - [NDK Project Building Overview](build-with-ndk-overview.md)
  - [Building an NDK Project with the DevEco Studio Template](build-with-ndk-ide.md)
  - [Building an NDK Project with the Command Line CMake](build-with-ndk-cmake.md)
  - [Building an NDK Project with Prebuilt Libraries](build-with-ndk-prebuilts.md)
- Code Development
  - [Development Overview](develop-code-overview.md)
  - C/C++ Standard Library
    - [C/C++ Mechanisms](c-cpp-overview.md)
  - Using Node-API
    - [Node-API Overview](napi-introduction.md)
    - [Node-API Data Types and APIs](napi-data-types-interfaces.md)
    - [Node-API Development Specifications](napi-guidelines.md)
    - [Node-API Development Process](use-napi-process.md)
    - Node-API Use Cases
      - [Asynchronous Task Development Using Node-API](use-napi-asynchronous-task.md)
      - [Thread Safety Development Using Node-API](use-napi-thread-safety.md)
      - [Wrapping a Native Object in an ArkTS Object](use-napi-object-wrap.md)
      - [Calling Back ArkTS APIs in a Non-ArkTS Thread](use-uv-queue-work.md)
      - [Creating an ArkTs Runtime Environment Using Node-API](use-napi-ark-runtime.md)
      - [Loading a Module in the Main Thread Using Node-API](use-napi-load-module.md)
      - [Running or Stopping an Event Loop in an Asynchronous Thread Using Extended Node-API](use-napi-event-loop.md)
      - [Loading a Module Using Node-API](use-napi-load-module-with-info.md)
      - [Passing a Task with the Specified Priority to an ArkTS Thread from an Asynchronous Thread Using Node-API](use-call-threadsafe-function-with-priority.md)
      - [Using Node-API Extension APIs](use-napi-about-extension.md)
    - [Node-API FAQs](use-napi-faqs.md)
  - Using JSVM-API
    - [JSVM-API Overview](jsvm-introduction.md)
    - [JSVM-API Data Types and APIs](jsvm-data-types-interfaces.md)
    - [JSVM-API Development Specifications](jsvm-guidelines.md)
    - [Debugging and Tuning JS Code Using JSVM-API](jsvm-debugger-cpuprofiler-heapsnapshot.md)
    - JSVM-API Use Cases
      - [Creating and Destroying JS VMs Using JSVM-API](use-jsvm-runtime-task.md)
  - Resource Management
    - [Raw File Development](rawfile-guidelines.md)
  - Thread Scheduling
    - [QoS Development](qos-guidelines.md)
  - Memory Management
    - [Purgeable Memory Development](purgeable-memory-guidelines.md)
  - Device Management
    - [USB DDK Development](usb-ddk-guidelines.md)
    - [HID DDK Development](hid-ddk-guidelines.md)
  - Bundle Management
    - [Native Bundle Development](native-bundle-guidelines.md)
- Debugging and Profiling
  - [Overview of Debugging and Profiling](debug-performance-profiling-overview.md)
- Debugging and Profiling
  - [Debugging and Profiling Overview](debug-performance-profiling-overview.md)
  - [Debugging in DevEco Studio](debug-ide.md)
  - [LLDB Debugger](debug-lldb.md)
  - [C/C++ Memory Error Detection](debug-asan.md)
- Hardware Compatibility
  - [Introduction to Hardware Compatibility](hw-guide.md)
  - [OpenHarmony ABIs](ohos-abi.md)
  - [CPU Features](cpu-features.md)
  - [Using Neon Instructions](neon-guide.md)
