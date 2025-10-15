# Ability Kit Terminology

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @ccllee1-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

## A

### AbilityStage

[AbilityStage](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md) is a component manager at the [module](../quick-start/application-package-overview.md#multi-module-design-mechanism) level.

### ArkTS Child Process

An ArkTS child process is where the system automatically sets up an ArkTS runtime environment when it starts.


## C

### Candidate Master Process

When an application has multiple processes, the system automatically designates a master process at application startup. If you want the current process to be selected as the master process, you can add it to the candidate master process list. Processes in this list are considered candidate master processes. When the current master process is destroyed, the system sets the candidate master process at the head of the list as the new master process.


## F

### FA Model

The FA model is an early application model that provides essential components and runtime mechanisms for applications. Each application component in this model has its own ArkTS engine instance, making it ideal for developing simple applications.


## M

### Master Process

When an application has multiple processes and you need to dynamically assign different ability instances to specific processes, the system automatically designates a process to handle overall coordination and allocation at application startup. This designated process is the master process. By default, the system designates the first process launched by the application as the master process.

You can set the return value of [onNewProcessRequest](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#onnewprocessrequest11) to allow the master process to determine which process will run the new ability instance based on the callback information received through this API.


## N

### Native Child Process

A native child process runs only C/C++ code. By default, the system does not create an ArkTS runtime environment for this type of child process.

## S

### Stage Model

The stage model is the currently recommended application model, providing essential components and runtime mechanisms for applications. This model introduces the AbilityStage component manager and the WindowStage window manager, which act as the stages for application components and windows, respectively—hence the name "stage model."

The stage model allows multiple application components to share a single ArkTS engine instance and supports state sharing and object invocation between components. This reduces memory overhead and enhances development efficiency, making it well-suited for complex application development.
