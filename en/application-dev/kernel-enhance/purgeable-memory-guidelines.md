# Purgeable Memory Development

<!--Kit: Common-->
<!--Subsystem: Common-->
<!--Owner: @fang-jinxu-->
<!--Designer: @lingminghw-->
<!--Tester: @RayShih-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=906890335bf480362f63f05961ebc2618e5bb601 translatedAt=2026-07-02T12:58:09.556Z pushedAt=2026-07-03T10:42:31.353Z -->

Purgeable Memory refers to memory that can be discarded at any time. This memory area is used to store data that can be easily reconstructed through recalculation. The data can be directly released when the system is low on memory and reconstructed when the user accesses it again. Purgeable Memory is suitable for storing large blocks (at least 4 KB) of data with low recovery cost. It is reclaimed with priority when the system is under high memory pressure (here, it refers to dropping anonymous pages in a manner similar to file pages, rather than compressing them). When used again, the user needs to restore the data themselves before use.

## When to Use

OpenHarmony provides a Purgeable Memory management mechanism. You can use related APIs to create PurgeableMemory objects to manage Purgeable Memory.

This guide describes how to use related Native APIs to operate Purgeable Memory in OpenHarmony applications. The supported operations include requesting and releasing Purgeable Memory.

Common development scenarios for the Purgeable Memory management mechanism are as follows:

1. Use related Native APIs provided by this mechanism to request and manage a **PurgeableMemory** object, and write data content to the object.

2. Release the **PurgeableMemory** object after it is no longer used.

## Available APIs

| Name | Description |
| -------- | -------- |
| OH_PurgeableMemory *OH_PurgeableMemory_Create(size_t size, OH_PurgeableMemory_ModifyFunc func, void *funcPara) | Creates a **PurgeableMemory** object. Each call generates a new **PurgeableMemory** object. |
| bool OH_PurgeableMemory_Destroy(OH_PurgeableMemory *purgObj) | Destroys a **PurgeableMemory** object. |
| bool OH_PurgeableMemory_BeginRead(OH_PurgeableMemory *purgObj) | Performs read access on a **PurgeableMemory** object and increments the read reference count by 1. |
| void OH_PurgeableMemory_EndRead(OH_PurgeableMemory *purgObj) | Ends a read operation and decrements the read reference count of the **PurgeableMemory** object by 1. |
| bool OH_PurgeableMemory_BeginWrite(OH_PurgeableMemory *purgObj) | Performs write access on a **PurgeableMemory** object and increments the write reference count by 1. |
| void OH_PurgeableMemory_EndWrite(OH_PurgeableMemory *purgObj) | Ends a write operation and decrements the write reference count of the **PurgeableMemory** object by 1. |
| void *OH_PurgeableMemory_GetContent(OH_PurgeableMemory *purgObj) | Obtains the memory data pointer of a **PurgeableMemory** object. The return type is void*. Convert it based on the actual data type before use. |
| size_t OH_PurgeableMemory_ContentSize(OH_PurgeableMemory *purgObj) | Obtains the memory data size of a **PurgeableMemory** object. |
| bool OH_PurgeableMemory_AppendModify(OH_PurgeableMemory *purgObj, OH_PurgeableMemory_ModifyFunc func, void *funcPara) | Adds a modification method for a **PurgeableMemory** object. |

## How to Develop

The following steps describe how to use the Native APIs provided by `Purgeable Memory` in **OpenHarmony** to request a PurgeableMemory object, write content to the object, and then perform read and write access on the object.

1. Declare the creation rules for the **PurgeableMemory** object.

    ```c++
    // Declare the parameters of the build function
    struct ParaData{
        int start;
        int end;
    };

    // Declare a function that uses ModifyFunc (example: factorial function)
    bool FactorialFunc(void* data, size_t size, void* param){
        bool ret = true;
        ParaData *pdata = (ParaData*) param;
        int* oriData = (int*)data;
        // Initialize the value to 1 before calculating the factorial
        *oriData = 1;
        int i = pdata->start;
        while (i <= pdata->end) {
            *oriData *= i;
            i++;
        }
        return ret;
    }

    // Declare the parameters of the extension function for modifying the PurgeableMemory object
    struct AppendParaData{
        int newPara;
    };

    // Declare the extension function for modifying the PurgeableMemory object
    bool AddFunc(void* data, size_t size, void* param){
        bool ret = true;
        int *oriDatap = (int*) data;
        AppendParaData* apData = (AppendParaData*)param;
        *oriDatap += apData->newPara;
        return ret;
    }
    ```

2. Create a **PurgeableMemory** object.

    ```c++
    // Declare the size of a 4 MB PurgeableMemory object
    #define DATASIZE (4 * 1024 * 1024)

    // Declare the parameters of the creation function
    struct ParaData pdata = {1,2};

    // Create a PurgeableMemory object
    OH_PurgeableMemory* pPurgmem = OH_PurgeableMemory_Create(DATASIZE, FactorialFunc, &pdata);
    ```

3. Perform read access on the **PurgeableMemory** object.

    ```c++
    // User-defined service object type. Add member variables and methods in service code.
    class ReqObj {
    };

    // Read the object
    if(OH_PurgeableMemory_BeginRead(pPurgmem)) {
        // Obtain the size of the PurgeableMemory object
        size_t size = OH_PurgeableMemory_ContentSize(pPurgmem);

        // Obtain the content of the PurgeableMemory object. Ensure the object content has been initialized before use.
        ReqObj* pReqObj = reinterpret_cast<ReqObj*>(OH_PurgeableMemory_GetContent(pPurgmem));

        // End reading the PurgeableMemory object
        OH_PurgeableMemory_EndRead(pPurgmem);
    }
    ```

4. Perform write access on the **PurgeableMemory** object.

    ```c++
    // User-defined service object type. Add member variables and methods in service code.
    class ReqObj {
    };

    // Modify the PurgeableMemory object
    if(OH_PurgeableMemory_BeginWrite(pPurgmem)) {
        // Get the PurgeableMemory object data
        ReqObj* pReqObj = reinterpret_cast<ReqObj*>(OH_PurgeableMemory_GetContent(pPurgmem));

        // Define and initialize the parameters of the extension modification function
        struct AppendParaData apdata = {1};

        // Update the rebuild rules of the PurgeableMemory object
        OH_PurgeableMemory_AppendModify(pPurgmem, AddFunc, &apdata);

        // End modifying the PurgeableMemory object
        OH_PurgeableMemory_EndWrite(pPurgmem);
    }
    ```

5. Destroy the **PurgeableMemory** object.

    ```c++
    // Destroy the object
    OH_PurgeableMemory_Destroy(pPurgmem);
    // Set the pointer to null to prevent dangling pointer access
    pPurgmem = nullptr;
    ```