# ArkTS

- [Introduction to ArkTS](arkts-overview.md)
- ArkTS Utility
    - [ArkTS Utils Overview](arkts-utils-overview.md)
    - XML Generation, Parsing, and Conversion
        - [XML Overview](xml-overview.md)
        - [XML Generation](xml-generation.md)
        - [XML Parsing](xml-parsing.md)
        - [XML Conversion](xml-conversion.md)
    - [Buffer Introduction](buffer.md)
    - ArkTS Containers
        - [Container Overview](container-overview.md)
        - [Linear Containers](linear-container.md)
        - [Nonlinear Containers](nonlinear-container.md)
- ArkTS Concurrency
    - [Concurrency Overview](concurrency-overview.md)
    - [Asynchronous Concurrency](async-concurrency-overview.md)
    - Multithreaded Concurrency
        - [Multithreaded Concurrency Overview](multi-thread-concurrency-overview.md)
        - [TaskPool Introduction](taskpool-introduction.md)
        - [Worker Introduction](worker-introduction.md)
        - [Comparison Between TaskPool and Worker](taskpool-vs-worker.md)
    - Inter-Thread Communication
        - [ArkTS Inter-Thread Communication Overview](interthread-communication-overview.md)
        - Inter-Thread Communication Objects
            - [Common Object](normal-object.md)
            - [ArrayBuffer Object](arraybuffer-object.md)
            - [SharedArrayBuffer Object](shared-arraybuffer-object.md)
            - [Transferable Object (NativeBinding Object)](transferabled-object.md)
            - Sendable Object
                - [Sendable Object Overview](arkts-sendable.md)
                - [Sendable Usage Rules and Constraints](sendable-constraints.md)
                - [Asynchronous Lock](arkts-async-lock-introduction.md)
                - [ASON Parsing and Generation](ason-parsing-generation.md)
                - [Shared Container](arkts-collections-introduction.md)
                - [Shared Module](arkts-sendable-module.md)
                - [Freezing a Sendable Object](sendable-freeze.md)
                - [Sendable Use Scenarios](sendable-guide.md)
        - Communication Between Threads
            - [Using TaskPool for Independent Time-Consuming Tasks](independent-time-consuming-task.md)
            - [Using TaskPool for Multiple Time-Consuming Tasks](multi-time-consuming-tasks.md)
            - [Communication Between the TaskPool Task and Host Thread](taskpool-communicates-with-mainthread.md)
            - [Instant Communication Between the Worker Thread and Host Thread](worker-communicates-with-mainthread.md)
            - [Worker Thread Synchronously Calling Methods of the Host Thread](worker-invoke-mainthread-interface.md)
    - Multithreaded Development
        - [Multithreaded Development Overview](multithread-develop-overview.md)
        - Concurrent Time-Consuming Tasks
            - [Concurrent Time-Consuming Task Scenarios](time-consuming-task-overview.md)
            - [CPU Intensive Task Development (TaskPool and Worker)](cpu-intensive-task-development.md)
            - [I/O Intensive Task Development (TaskPool)](io-intensive-task-development.md)
            - [Synchronous Task Development (TaskPool and Worker)](sync-task-development.md)
        - Concurrent Continuous Tasks
            - [Concurrent Continuous Task Scenarios](long-time-task-overview.md)
            - [Continuous Task Development (TaskPool)](long-time-task-guide.md)
        - Concurrent Resident Tasks
            - [Concurrent Resident Task Scenarios](resident-task-overview.md)
            - [Resident Task Development (Worker)](resident-task-guide.md)
        - Multithreaded Development Practice Cases
            - [Batch Data Writing to the Database](batch-database-operations-guide.md)
            - [Concurrent Loading of Service Modules](concurrent-loading-modules-guide.md)
            - [Global Configuration Items](global-configuration-guide.md)
            - [ArkUI Data Updates](makeobserved-sendable.md)
            - [Data Sharing Between C++ Threads](native-interthread-shared.md)
- [ArkTS Cross-Language Interaction](arkts-cross-language-interaction.md)
- ArkTS Runtime
    - [ArkTS Runtime Overview](arkts-runtime-overview.md)
    - [GC](gc-introduction.md)
    - ArkTS Modularization
        - [Introduction to Modular Operation](module-principle.md)
        - [Dynamic Import](arkts-dynamic-import.md)
        - [Lazy Import](arkts-lazy-import.md)
        - [Dynamically Loading a Native Module in Synchronous Mode](js-apis-load-native-module.md)
        - [Loading Modules Using Node-API](load-module-base-nodeapi.md)
        - [Module Loading Side Effects and Optimization](arkts-module-side-effects.md)
- ArkTS Compilation Toolchain
    - [ArkTS Compilation Toolchain Overview](compilation-tool-chain-overview.md)
    - Ark Bytecode
        - [Ark Bytecode Overview](arkts-bytecode-overview.md)
        - [Ark Bytecode File Format](arkts-bytecode-file-format.md)
        - [Ark Bytecode Fundamentals](arkts-bytecode-fundamentals.md)
        - [Naming Rules of Ark Bytecode Functions](arkts-bytecode-function-name.md)
        - [Customizing Ark Bytecode During Compilation](customize-bytecode-during-compilation.md)
    - [Disassembler](tool-disassembler.md)
    - ArkGuard Code Obfuscation
        - [ArkGuard](source-obfuscation.md)
    - [Configuring arkOptions in build-profile.json5](arkoptions-guide.md)
