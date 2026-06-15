# Purgeable Memory Management Development

<!--Kit: Common-->
<!--Subsystem: Common-->
<!--Owner: @fang-jinxu-->
<!--Designer: @lingminghw-->
<!--Tester: @RayShih-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T06:18:59.816Z pushedAt=2026-06-03T09:38:08.619Z -->

Purgeable Memory refers to memory that can be discarded at any time. This memory area is used to store data that can be easily reconstructed through recalculation. The data can be directly released when the system is low on memory and reconstructed when the user accesses it again. Purgeable Memory is suitable for storing large blocks (at least 4K) of data with low recovery cost. It is reclaimed with priority when the system is under high pressure (here, it refers to dropping anonymous pages in a form similar to file pages, rather than compression). When used again, the user needs to restore the data before use.

## When to Use

OpenHarmony provides the Purgeable Memory management mechanism. Developers can use relevant APIs to create PurgeableMemory objects to manage purgeable memory.

Through this guide, developers can learn how to use Native layer APIs to operate purgeable memory in OpenHarmony applications. Functions include applying for and releasing purgeable memory.

For the Purgeable Memory memory management mechanism, common development scenarios are as follows:

* Use the `NAPI` interface provided by this mechanism to apply for and manage a PurgeableMemory object, and write data content into the object.

* Release it after use.

## Available APIs

| Name | Description | 
| -------- | -------- |
| OH_PurgeableMemory \*OH_PurgeableMemory_Create(size_t size, OH_PurgeableMemory_ModifyFunc func, void \*funcPara) | Creates a PurgeableMemory object. A new PurgeableMemory object is generated for each call. | 
| bool OH_PurgeableMemory_Destroy(OH_PurgeableMemory \*purgObj) | Destroys a PurgeableMemory object. | 
| bool OH_PurgeableMemory_BeginRead(OH_PurgeableMemory \*purgObj) | Begins read access to a PurgeableMemory object. | 
| void OH_PurgeableMemory_EndRead(OH_PurgeableMemory \*purgObj) | Ends the read operation and decrements the reference count of the PurgeableMemory object by 1. When the reference count reaches 0, the PurgeableMemory object can be reclaimed by the system. | 
|bool OH_PurgeableMemory_BeginWrite(OH_PurgeableMemory \*purgObj) | Begins write access to a PurgeableMemory object.|
|void OH_PurgeableMemory_EndWrite(OH_PurgeableMemory \*purgObj)|Ends the write operation and decrements the reference count of the PurgeableMemory object by 1. When the reference count reaches 0, the PurgeableMemory object can be reclaimed by the system.|
|void \*OH_PurgeableMemory_GetContent(OH_PurgeableMemory \*purgObj)|Obtains the memory data of a PurgeableMemory object.|
|size_t OH_PurgeableMemory_ContentSize(OH_PurgeableMemory \*purgObj)|Obtains the size of the memory data of a PurgeableMemory object.|
|bool OH_PurgeableMemory_AppendModify(OH_PurgeableMemory \*purgObj, OH_PurgeableMemory_ModifyFunc func, void \*funcPara)|Adds a modification method for the PurgeableMemory object.|

## How to Develop

The following steps describe how to use the `NAPI` interface provided by `Purgeable Memory` in **OpenHarmony** to request a PurgeableMemory object, write content into it, and then perform read and write access to the object.

1. Declare the rules for creating a PurgeableMemory object.

    ```c++
    // Declare the parameters of the constructor function.
    struct ParaData{
        int start;
        int end;
    };

    // Declare a function that uses ModifyFunc.
    bool FactorialFunc(void* data, size_t size, void* param){
        bool ret = true;
        ParaData *pdata = (ParaData*) param;
        int* oriData = (int*)data;
        int i = pdata->start;
        while (i < pdata->end) {
            *oriData *= i;
            i++;
        }
        return ret;
    }

    // Declare the parameters for the extended function that modifies the PurgeableMemory object.
    struct AppendParaData{
        int newPara;
    };

    // Declare the extended function that modifies the PurgeableMemory object.
    bool AddFunc(void* data, size_t size, void* param){
        bool ret = true;
        int *oriDatap = (int*) data;
        AppendParaData* apData = (AppendParaData*)param;
        *oriDatap += apData->newPara;
        return ret;
    }
    ```

2. Create a PurgeableMemory object.

    ```c++
    // Declare a PurgeableMemory object size of 4 MB.
    #define DATASIZE (4 * 1024 * 1024)

    // Declare the parameters for the creation function.
    struct ParaData pdata = {1,2};

    // Create a PurgeableMemory object
    OH_PurgeableMemory* pPurgmem = OH_PurgeableMemory_Create(DATASIZE, FactorialFunc, &pdata);
    ```

3. Read access to the PurgeableMemory object.

    ```c++
    // Service-defined object type
    class ReqObj;

    // Read the object
    if(OH_PurgeableMemory_BeginRead(pPurgmem)) {
        // Get the size of the PurgeableMemory object
        size_t size = OH_PurgeableMemory_ContentSize(pPurgmem);

        // Obtain the content of the PurgeableMemory object
        ReqObj* pReqObj = (ReqObj*) OH_PurgeableMemory_GetContent(pPurgmem);

        // End reading the PurgeableMemory object
        OH_PurgeableMemory_EndRead(pPurgmem);
    }
    ```

4. Write access to the PurgeableMemory object.

    ```c++
    // Business-defined object type
    class ReqObj;

    // Modify the PurgeableMemory object
    if(OH_PurgeableMemory_BeginWrite(pPurgmem)) {
        // Obtain PurgeableMemory object data
        ReqObj* pReqObj = (ReqObj*) OH_PurgeableMemory_GetContent(pPurgmem);

        // Declare parameters for the extended creation function
        struct AppendParaData apdata = {1};

        // Update PurgeableMemory object rebuild rules
        OH_PurgeableMemory_AppendModify(pPurgmem, AddFunc, &apdata);

        // End modifying the PurgeableMemory object
        OH_PurgeableMemory_EndWrite(pPurgmem);
    }
    ```

5. Destroy the PurgeableMemory object.

    ```c++
    // Destroy the object
    OH_PurgeableMemory_Destroy(pPurgmem);
    // Set the pointer to null to prevent UAF
    pPurgmem = nullptr;
    ```