# Common Stability Issues with Graphics Buffers (C/C++)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T06:18:13.652Z pushedAt=2026-06-03T09:28:01.512Z -->

This section describes common issues encountered during development with NativeWindow, NativeBuffer, and NativeImage, helping developers avoid or locate these issues in a timely manner and improve application stability.

## OHNativeWindow and NativeWindowBuffer

OHNativeWindow and NativeWindowBuffer are passed between multiple system modules and applications. They implement pseudo-smart pointers through NDK interfaces that increment and decrement reference counts, with each module maintaining its own reference count. Over 90% of issues are caused by mismatched increment and decrement reference count interface calls.

Interface for incrementing the NativeWindow reference count:

```text
int32_t OH_NativeWindow_NativeObjectReference(void *obj)

int32_t OH_NativeWindow_CreateNativeWindowFromSurfaceId(uint64_t surfaceId, OHNativeWindow **window)

OHNativeWindow* OH_NativeImage_AcquireNativeWindow(OH_NativeImage* image)

int32_t OH_NativeWindow_ReadFromParcel(OHIPCParcel *parcel, OHNativeWindow **window)
```

Interface for decrementing the NativeWindow reference count:

```text
int32_t OH_NativeWindow_NativeObjectUnreference(void *obj)

void OH_NativeWindow_DestroyNativeWindow(OHNativeWindow* window)

void OH_NativeImage_Destroy(OH_NativeImage** image)
```

Interface for incrementing the NativeWindowBuffer reference count:

```text
int32_t OH_NativeWindow_NativeObjectReference(void *obj)

int32_t OH_NativeWindow_GetLastFlushedBufferV2(OHNativeWindow *window, OHNativeWindowBuffer **buffer,int *fenceFd, float matrix[16])

OHNativeWindowBuffer* OH_NativeWindow_CreateNativeWindowBufferFromNativeBuffer(OH_NativeBuffer* nativeBuffer)

int32_t OH_NativeImage_AcquireNativeWindowBuffer(OH_NativeImage* image,OHNativeWindowBuffer** nativeWindowBuffer, int* fenceFd)
```

Interface for decrementing the NativeWindowBuffer reference count:

```text
int32_t OH_NativeWindow_NativeObjectUnreference(void *obj)

void OH_NativeWindow_DestroyNativeWindowBuffer(OHNativeWindowBuffer* buffer)

int32_t OH_NativeImage_ReleaseNativeWindowBuffer(OH_NativeImage* image,OHNativeWindowBuffer* nativeWindowBuffer, int fenceFd) // Decrement the reference count only when the interface returns success
```

## NativeWindow Lifecycle Issues

### Typical Crash Logs and Causes

A typical crash log is as follows:

```text
**Typical crash log 1**
00 /system/lib64/chipset-sdk-sp/libsurface.z.so(OH_NativeWindow_DestroyNativeWindow())

**Typical crash log 2**
00 /system/lib64/chipset-sdk-sp/libsurface.z.so(...)
01 /system/lib64/chipset-sdk-sp/libsurface.z.so(...)
02 /system/lib64/chipset-sdk-sp/libsurface.z.so(OH_NativeWindow_NativeWindowHandleOpt)

**Typical crash log 3**
00 /system/lib64/chipset-sdk-sp/libsurface.z.so(OH_NativeWindow_NativeObjectUnreference())
```

The possible causes are as follows:

1. The NativeWindow reference count is incorrectly decremented once, causing the NativeWindow count to drop to 0 and be released. A crash occurs when it is called elsewhere or decremented again.

2. The NativeWindow obtained from the XComponent component is passed to a child thread for use. When the XComponent component is destroyed, the NativeWindow reference count is decremented by one. If it drops to 0 and is destructed, a crash will occur if the child thread is still using it.

### Typical Error Codes and Solutions

**Typical Error 1**

```c++
OH_NativeImage *image_ = OH_NativeImage_Create(textureId, GL_TEXTURE_2D);
OHNativeWindow *nativewindow_ = OH_NativeImage_AcquireNativeWindow();

// Error: OH_NativeImage_Destroy decrements the OHNativeWindow reference count, so there is no need to call OH_NativeWindow_DestroyNativeWindow again.
OH_NativeImage_Destroy(image_);
OH_NativeWindow_DestroyNativeWindow(nativewindow_);
```

**Detailed Analysis**

OH_NativeImage_Destroy decrements the OHNativeWindow reference count, so there is no need to call OH_NativeWindow_DestroyNativeWindow again.

Fix: Delete OH_NativeWindow_DestroyNativeWindow(nativewindow_), and set image_ and nativewindow_ to null immediately after OH_NativeImage_Destroy to prevent subsequent use of dangling pointers.

```c++
OH_NativeImage *image_ = OH_NativeImage_Create(textureId, GL_TEXTURE_2D);
OHNativeWindow *nativewindow_ = OH_NativeImage_AcquireNativeWindow();

// Set image_ and nativewindow_ to null when releasing NativeImage to prevent subsequent use of dangling pointers
OH_NativeImage_Destroy(image_);
image_ = nullptr;
nativewindow_ = nullptr;
```

**Typical Error Code 2**

```c++
void OnSurfaceCreatedCB(OH_NativeXComponent* component, void* window)
{
    uint64_t width = 0;
    uint64_t height = 0;
    int32_t ret = OH_NativeXComponent_GetXComponentSize(component, window, &width, &height);
    OHNativeWindow* nativewindow_ = static_cast<OHNativeWindow*>(window);

    // Directly passing NativeWindow to a child thread without incrementing the reference count
    NativeRender::GetInstance()->SetNativeWindow(nativewindow_, width, height);
}

void OnSurfaceDestroyedCB(OH_NativeXComponent* component, void* window)
{
    if ((component == nullptr) || (window == nullptr)) {
        LOGE("OnSurfaceDestroyedCB: component or window is null");
        return;
    }

    // Error: The child thread is signaled to stop, but no wait operation is performed. After OnSurfaceDestroyedCB completes, NativeWindow may be released, and the child thread may crash while still using it.
    NativeRender::GetInstance()->Release();
    OHNativeWindow* nativewindow_ = static_cast<OHNativeWindow*>(window);
    // Error: Calling DestroyNativeWindow without incrementing the reference count of nativewindow_ causes nativewindow_ to be released prematurely, leading to a crash.
    OH_NativeWindow_DestroyNativeWindow(nativewindow_);
}
```

**Detailed Analysis**

After obtaining the NativeWindow from the XComponent component, it is passed to a rendering sub-thread for use. When the page exits and the XComponent component is destroyed, the reference count of the NativeWindow is decremented by one. If the application has not incremented the NativeWindow reference count, the NativeWindow will be released, while the sub-thread may still be using it, potentially causing a concurrent crash.

Fix 1: Before passing the NativeWindow to the sub-thread, increment its reference count by one. In this case, when the XComponent component is destroyed, the NativeWindow will not be destroyed because the application holds a reference count to it. After the sub-thread finishes using it, decrement its reference count by one.

```c++
void OnSurfaceCreatedCB(OH_NativeXComponent* component, void* window)
{
    uint64_t width = 0;
    uint64_t height = 0;
    int32_t ret = OH_NativeXComponent_GetXComponentSize(component, window, &width, &height);
    OHNativeWindow* nativewindow_ = static_cast<OHNativeWindow*>(window);

    // Increment the reference count of nativeWindow by one before posting the task.
    OH_NativeWindow_NativeObjectReference(nativewindow_);
    NativeRender::GetInstance()->SetNativeWindow(nativewindow_, width, height);
}

void OnSurfaceDestroyedCB(OH_NativeXComponent* component, void* window)
{
    if ((component == nullptr) || (window == nullptr)) {
        LOGE("OnSurfaceDestroyedCB: component or window is null");
        return;
    }

    // Notify the child thread to stop. Because the reference count was incremented earlier, it will not be released when OnSurfaceDestroyedCB ends.
    // When the child thread finishes using it, execute OH_NativeWindow_NativeObjectUnreference(nativewindow_) to decrement the reference count.
    NativeRender::GetInstance()->Release();
}
```

Fix 2: In the OnSurfaceDestroyedCB callback notification for XComponent component destruction, notify the child thread to stop and wait until the child thread ends, preventing the child thread from still being in use after the NativeWindow is destroyed.

```c++
void OnSurfaceCreatedCB(OH_NativeXComponent* component, void* window)
{
    uint64_t width = 0;
    uint64_t height = 0;
    int32_t ret = OH_NativeXComponent_GetXComponentSize(component, window, &width, &height);
    OHNativeWindow* nativewindow_ = static_cast<OHNativeWindow*>(window);

    NativeRender::GetInstance()->SetNativeWindow(nativewindow_, width, height);
}

void OnSurfaceDestroyedCB(OH_NativeXComponent* component, void* window)
{
    if ((component == nullptr) || (window == nullptr)) {
        LOGE("OnSurfaceDestroyedCB: component or window is null");
        return;
    }

    NativeRender::GetInstance()->Release();
    // Notify the child thread to stop, then wait for the child thread task to finish before ending OnSurfaceDestroyedCB.
    renderThread.join();
}
```

## NativeWindowBuffer Lifecycle Issues

### Typical Crash Logs and Causes

A typical crash log is as follows:

```text
**Typical crash log 1**
00 /system/lib64/chipset-sdk-sp/libsurface.z.so(OH_NativeWindow_GetBufferHandleFromNative())

**Typical crash log 2**
00 /system/lib64/chipset-sdk-sp/libsurface.z.so(OH_NativeWindow_NativeObjectUnreference())

**Typical crash log 3**
00 /system/lib64/chipset-sdk-sp/libsurface.z.so(OH_NativeWindow_NativeObjectReference())
```

The possible causes are as follows:

The NativeWindow obtained from the XComponent component is passed to a child thread for use. When the XComponent component is destroyed, the NativeWindow reference count is decremented by one. When the NativeWindow is destroyed, the reference count of the internal NativeWindowBuffer is decremented by one. At this point, the child thread has just called RequestBuffer and is using the buffer, causing a crash.

### Typical Error Codes and Solutions

Same as the typical error codes and solutions for the NativeWindow lifecycle issues above.

## NativeWindowBuffer Deadlock Issues

### Typical Deadlock Logs and Causes

A typical deadlock log is as follows:

```text
/system/lib64/chipset-sdk-sp/libsurface.z.so(RequestBufferLocked())
```

The possible causes are as follows:

The application requests a buffer but does not return it, resulting in no available buffer for subsequent use and causing the application to hang when requesting a buffer again.

**Typical Error Codes**

```c++
auto ret = OH_NativeWindow_NativeWindowRequestBuffer(nativewindow_, &buffer, &fence);
if (ret != NATIVE_ERROR_OK) {
    return;
}

// Error: The buffer is not returned in the exception branch. The number of buffers in NativeWindow is fixed, which may cause a hang due to no available buffer for subsequent use.
if (error) {
    return;
}

OH_NativeWindow_NativeWindowFlushBuffer(nativewindow_, buffer, fence, region);
```

**Detailed Analysis**

The number of NativeWindowBuffers in NativeWindow is fixed. If buffers are only requested but not returned, the buffers in NativeWindow will be exhausted, causing a hang when requesting a buffer again.

Fix: Ensure that requested buffers are always returned to NativeWindow. Successfully drawn buffers can be returned via OH_NativeWindow_NativeWindowFlushBuffer, and undrawn buffers can be returned via OH_NativeWindow_NativeWindowAbortBuffer.

```c++
auto ret = OH_NativeWindow_NativeWindowRequestBuffer(nativewindow_, &buffer, &fence);
if (ret != NATIVE_ERROR_OK) {
    return;
}

if (error) {
    // Returning buffers in exception branches
    OH_NativeWindow_NativeWindowAbortBuffer(nativewindow_, buffer);
    return;
}

OH_NativeWindow_NativeWindowFlushBuffer(nativewindow_, buffer, fence, region);
```

## Memory Leak Issues

### Typical Causes of Memory Leaks

A memory leak occurs when an interface that increments the reference count is called without a corresponding call to an interface that decrements the reference count.

### Typical Error Codes and Solutions

**Typical Error 1**

```c++
auto ret = OH_NativeWindow_NativeWindowRequestBuffer(nativewindow_, &buffer, &fence);
if (ret != NATIVE_ERROR_OK) {
    return;
}
ret = OH_NativeWindow_NativeObjectReference(buffer);
if (ret != NATIVE_ERROR_OK) {
    return;
}

// Error: The reference count of the buffer was incremented, but the drawing process took an exception branch where the reference count was not correspondingly decremented, causing a leak.
if (error) {
    OH_NativeWindow_NativeWindowAbortBuffer(nativewindow_, buffer);
    return;
}

OH_NativeWindow_NativeWindowFlushBuffer(nativewindow_, buffer, fence, region);
OH_NativeWindow_NativeObjectReference(buffer);
```

**Detailed Analysis**

After requesting the buffer, the reference count was incremented to extend its lifecycle, but it was not correspondingly decremented, preventing the buffer from being released.

Fix: Ensure that after incrementing the reference count, a corresponding interface call is made to decrement the reference count.

```c++
auto ret = OH_NativeWindow_NativeWindowRequestBuffer(nativewindow_, &buffer, &fence);
if (ret != NATIVE_ERROR_OK) {
    return;
}
ret = OH_NativeWindow_NativeObjectReference(buffer);
if (ret != NATIVE_ERROR_OK) {
    return;
}

if (error) {
    // Decrement reference count in exception branches
    OH_NativeWindow_NativeWindowAbortBuffer(nativewindow_, buffer);
    OH_NativeWindow_NativeObjectUnreference(buffer);
    return;
}

OH_NativeWindow_NativeWindowFlushBuffer(nativewindow_, buffer, fence, region);
OH_NativeWindow_NativeObjectReference(buffer);
```

**Typical Error Code 2**

```c++
auto ret = OH_NativeImage_AcquireNativeWindowBuffer(nativeimage, &buffer, &fence);
if (ret != NATIVE_ERROR_OK) {
    return;
}
ret = OH_NativeWindow_NativeObjectReference(buffer);
if (ret != NATIVE_ERROR_OK) {
    return;
}

// Error: The release failure scenario is not handled. A successful AcquireNativeWindowBuffer call increments the buffer's reference count by one, but a failed ReleaseNativeWindowBuffer call does not decrement it.
OH_NativeImage_ReleaseNativeWindowBuffer(nativeimage, buffer, fence);
OH_NativeWindow_NativeObjectUnreference(buffer);
```

**Detailed Analysis**

The buffer acquired by the OH_NativeImage_AcquireNativeWindowBuffer interface increments the reference count. The OH_NativeImage_ReleaseNativeWindowBuffer interface decrements the reference count only upon success. Failure to handle the return value can lead to memory leaks.

Fix: When the OH_NativeImage_ReleaseNativeWindowBuffer interface does not return NATIVE_ERROR_OK, additionally call OH_NativeWindow_NativeObjectUnreference to decrement the reference count once.

```c++
auto ret = OH_NativeImage_AcquireNativeWindowBuffer(nativeimage, &buffer, &fence);
if (ret != NATIVE_ERROR_OK) {
    return;
}
ret = OH_NativeWindow_NativeObjectReference(buffer);
if (ret != NATIVE_ERROR_OK) {
    return;
}

// Perform exception handling for OH_NativeImage_ReleaseNativeWindowBuffer failure
ret = OH_NativeImage_ReleaseNativeWindowBuffer(nativeimage, buffer, fence);
if (ret != NATIVE_ERROR_OK) {
    OH_NativeWindow_NativeObjectUnreference(buffer);
}
OH_NativeWindow_NativeObjectUnreference(buffer);
```