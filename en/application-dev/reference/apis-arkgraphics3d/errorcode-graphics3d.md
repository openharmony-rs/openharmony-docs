# Graphics 3D Error Codes

<!--Kit: ArkGraphics 3D-->
<!--Subsystem: Graphics-->
<!--Owner: @jason_stark-->
<!--Designer: @zdustc-->
<!--Tester: @dongchao01-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=1c2fc501136ceec9ba29fd39d66bab83ae7d758a translatedAt=2026-11-14T08:09:34.901Z pushedAt=2026-11-14T08:16:02.575Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 25601002 Scene Used After Destruction

**Error Message**

Scene used after destruction.

**Description**

The Scene is still accessed or used after being destroyed.

**Possible Causes**

1. The developer still holds a reference to the Scene after it is destroyed and continues to call its methods.
2. An asynchronous callback (Promise, setTimeout, etc.) references the destroyed Scene.

**Solution**

1. Check when the Scene is destroyed in the code, and ensure that no property or method of the Scene instance is accessed after destruction.
2. Check whether any asynchronous operation (Promise callback, setTimeout, animation callback, etc.) may reference the destroyed Scene, and cancel all unfinished asynchronous operations or set the reference to null before the Scene is destroyed.

## 25601005 Memory Allocation Failure

**Error Message**

Memory allocation failed.

**Description**

Memory allocation failed, including CPU memory, GPU memory, or DMA buffer allocation failure.

**Possible Causes**

1. The system is running out of memory and cannot allocate the required CPU memory.
2. The GPU memory is insufficient to allocate GPU resources (textures, buffers, etc.).
3. The DMA buffer is insufficient.
4. A memory leak has exhausted the available memory.

**Solution**

1. Use system tools to check the memory usage of the application and confirm whether it is approaching the system limit.
2. Reduce the texture resolution or use compressed texture formats, and reduce the number of models in the scene or simplify the model polygon count.
3. Reduce the resolution of the off-screen render target to lower the DMA buffer usage.
4. Check resource lifecycle management to ensure that all created resources are properly destroyed when no longer needed, especially the release of resources such as animations, materials, and textures.

## 25601006 Using an Expired Resource

**Error Message**

Expired or invalid resource.

**Description**

An expired resource is used, including a Node, Material, Animation, Sampler, Environment, or RenderTarget that has been destroyed or invalidated.

**Possible Causes**

1. The resource is still referenced after being destroyed and released.
2. The Scene to which the resource belongs has been destroyed, so the resource becomes invalid but is still referenced.

**Solution**

1. Check the destruction timing of the resource to ensure that it is no longer referenced after destruction, and release all references to the resources of a Scene before the Scene is destroyed.
2. Check whether the resource is valid before using it (for example, check whether the resourceType attribute is accessible). Use try-catch to wrap the code that may reference an expired resource, and handle the exception after it is caught.

## 25603001 Parameter Exceeds the Allowed Range

**Error Message**

Parameter exceeds the allowed range.

**Description**

A single parameter does not meet the constraints of the interface, including but not limited to the value range, length, and content validity.

**Possible Causes**

1. The parameter value exceeds the range allowed by the interface.
2. The length of the array parameter exceeds the upper limit allowed by the interface.
3. The content of the array parameter does not meet the rule constraints of the interface, for example, the array is empty or its elements do not meet the interface requirements.

**Solution**

1. Check whether the numeric parameter exceeds the value range allowed by the interface.
2. Check whether the array length exceeds the upper limit allowed by the interface.
3. Check whether the content of the array parameter meets the rule constraints of the interface.

## 25603002 Parameter Type or Count Mismatch

**Error Message**

Input parameter type or count mismatch.

**Description**

When an interface has multiple input parameters, the types or counts of the parameters do not satisfy the matching constraints.

**Possible Causes**

The interface requires a correspondence between multiple parameters, but the parameters actually passed in do not satisfy this relationship.

**Solution**

Check the API reference to confirm the correspondence between the parameters, and pass in the parameters correctly as required by the interface.
