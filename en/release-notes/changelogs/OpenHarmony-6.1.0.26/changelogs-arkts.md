# ArkTS Changelog

## cl.arkcompiler.1 Change of JS OOM Exception Crash Stack Format

**Access Level**

Others

**Reason for Change**

Previously, when a JS OOM exception occurred in an application, **jscrash** or **cppcrash** was generated, which affected the OOM exception data statistics of third-party ecosystem applications.

**Change Impact**

This change does not require application adaptation.

Before the change: When a JS OOM exception occurs in the main thread heap of an application, a **jscrash** is generated. When a JS OOM exception occurs in the worker/taskpool thread heap, a **cppcrash** is generated. When a JS OOM exception occurs in the shared heap, a **jscrash** or **cppcrash** is generated.

After the change: A JS OOM in the main thread heap, worker/taskpool thread heap, or shared heap generates only a **jscrash**.

| Thread Heap| Before| After|
|------|--------|--------|
|Main thread heap|jscrash|jscrash|
|Worker/Taskpool thread heap|cppcrash|jscrash|
|Shared heap|jscrash/cppcrash|jscrash|

**Starting API Level**

API 12

**Effective Version**

OpenHarmony SDK 6.1.0.26

**Affected APIs/Components**

None

**Adaptation Guide**

This change modifies the default behavior. You need to assess whether it affects your application logic and update your code as needed.
