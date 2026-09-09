# Neural Network Runtime Kit Glossary

<!--Kit: Neural Network Runtime Kit-->
<!--Subsystem: AI-->
<!--Owner: @GbuzhidaoR-->
<!--Designer: @GbuzhidaoR-->
<!--Tester: @GbuzhidaoR-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=90ddd4aa2a6fcab28cba204a29e7abdc361e1d79 translatedAt=2026-09-09T03:11:42.871Z pushedAt=2026-09-09T03:30:02.779Z -->

## A

### Acceleration Chip

A hardware chip specifically designed to accelerate the computational tasks of AI neural network execution. As the underlying computing resource of NNRt, it provides more efficient matrix computation capabilities than general-purpose CPUs.

### Asynchronous Inference

An inference execution mode in which the request returns immediately after submission, and the caller is notified of inference completion through a callback. Compared with synchronous inference, it can improve system throughput.

## C

### Compilation Cache

A mechanism that saves model compilation results as cache files or in-memory data. When the same model is compiled again, the cache can be loaded directly, significantly reducing compilation time.

### Custom Extension Property

A proprietary configuration item for specific AI hardware, set through the extension configuration interface provided by NNRt. Refer to the hardware vendor for specific property names and values.

## D

### Device Management

One of the functional modules of NNRt, responsible for displaying the information of connected AI hardware and providing interfaces for selecting AI hardware.

## F

### FP16 Mode

A half-precision floating-point computation mode that trades lower numerical precision for higher computation performance and lower memory usage, suitable for inference scenarios that do not require high precision.

## H

### Hardware Driver

The AI acceleration chip driver at the bottom layer of NNRt, responsible for converting the model representation of NNRt into a computation format executable by the hardware.

### Heterogeneous Inference

The capability of a model to collaboratively execute model inference across different types of hardware, such as CPU, GPU, and acceleration chips.

## I

### In-memory Model Cache

Stores the compiled model object in memory for fast loading and reuse, avoiding repeated compilation overhead.

### Inference Framework

A software framework that runs on top of AI acceleration chips and provides model inference capabilities, such as MindSpore Lite. The inference framework implements cross-chip inference by calling NNRt interfaces.

### In-series Operator Fusion

An optimization technique that merges multiple adjacent operators into a single operator for execution, reducing data movement and kernel launch overhead to improve inference performance.

## L

### Low-level Device Abstraction Layer (HDI)

A layer that defines standardized hardware device interfaces, allowing upper-layer software (such as NNRt) to access AI acceleration chips from different vendors through unified interfaces.

## M

### Memory Management

One of the functional modules of NNRt. It is responsible for applying for shared memory on the AI hardware driver and allocating it to the inference input and output tensors, and releasing the corresponding shared memory when the tensors are destroyed.

### MindIR

The model graph format used by the MindSpore Lite inference framework. It is compatible with the NNRt internal model graph format, so MindSpore Lite can directly interoperate without calling the NNRt graph construction interface.

### MindSpore Lite

Huawei's self-developed AI inference framework with built-in NNRt support. It can directly connect to NNRt through the MindIR model graph to achieve transparent inference across AI hardware.

### Model Cache

One of the functional modules of NNRt. It saves compiled model objects in a cache format (file or memory), which can be loaded directly at the next compilation to greatly improve compilation speed.

### Model Compilation

A processing stage of NNRt that converts an internal model graph or an offline model file into a hardware-specific model object on the underlying AI hardware driver through the compilation interface.

### Model Construction

A processing stage of NNRt that converts the model graph of an inference framework into an internal model graph of NNRt by calling graph construction interfaces.

### Model Graph

A graph structure that represents the topology of a neural network, containing operator nodes and tensor connection relationships, and is used to describe the computational flow of a model.

### Model Inference

The processing stage of NNRt, which creates an executor based on the compiled model object, sets the inference input and output tensors, and then executes model computation on AI hardware.

## N

### Neural Network Runtime (NNRt)

A cross-chip inference computing runtime for the AI domain. It serves as an intermediate bridge connecting the upper-layer AI inference framework and the underlying acceleration chip, enabling cross-chip inference computing of AI models.

### NN_Tensor

A tensor handle in NNRt, used to set the inference input and output tensors of an executor, including data layout, data type, shape, and so on.

### NPU

A dedicated chip specifically designed to accelerate neural network computation, and one of the AI acceleration hardware types that NNRt connects to.

## O

### OH_NNCompilation; compiler handle

The compiler handle type of NNRt, used to configure and execute model compilation, including specifying the device, device cache, device performance parameters, and so on.

### OH_NNExecutor

The executor handle type of NNRt, used to construct the model graph, including adding tensors, adding operators, and specifying inputs and outputs.

### Offline Model

A model file format directly related to specific AI hardware, converted from the original trained model by a model converter provided by the hardware vendor. Offline models compile quickly but cannot be compatible across different hardware.

### Online Graph Construction

The process in which the AI inference framework calls the NNRt graph construction interface to convert the framework's internal model graph into the NNRt internal model graph.

### Operator

The basic computational unit in a neural network model, such as convolution, pooling, and activation functions. NNRt currently supports most common operators, and their specific implementations reside in the AI hardware driver.

### Operator Type

An enumeration value that identifies the function of an operator. For example, OH_NN_OPS_ADD indicates an addition operator and is used to specify the operator type when adding an operator.

## P

### Performance Mode

A hardware configuration option provided by NNRt, including modes such as extreme performance, high performance, balanced power consumption, and low power consumption, used to adjust the balance between performance and power consumption during inference.

### Priority

Execution priority configuration for model computation, which determines the scheduling order of inference tasks on the hardware.

## Q

### Quantization Parameter

A parameter used to specify the quantization information of a tensor, including the scale factor and zero point. It specifies the quantization configuration of a tensor during model construction.

## R

### Runtime

The execution environment during program runtime, providing basic services such as program loading, memory management, and task scheduling.

## S

### Shared Memory

A memory region that can be accessed by different processes or devices. NNRt implements "zero-copy" of input and output data by allocating shared memory on the AI hardware driver.

### Synchronous Inference

An inference execution mode in which the caller blocks after submitting an inference request and waits for the inference to complete and return the result. Compared with asynchronous inference, it is simpler to implement but may reduce system throughput.

## T

### Tensor

A multidimensional array that serves as the basic representation of data in a neural network model, including input data, output data, weight parameters, and so on. A tensor is the basic carrier for operator computation.

### Tensor Data Buffer

The memory area that stores the actual data of a tensor. After obtaining the pointer through the OH_NNTensor_GetDataBuffer interface, you can perform read and write operations.

## Z

## Zero-copy

A technique for passing data from one memory region to another without CPU involvement in the copy operation. NNRt implements zero-copy for input and output data through shared memory on the AI hardware driver to improve inference performance.