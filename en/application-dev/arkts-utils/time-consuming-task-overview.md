---
kits: ["ArkTS"]
description: "Introduces the classification and handling strategies for concurrency in time-consuming tasks: typical business operations such as image/video encoding and decoding, compression and decompression, JSON parsing, model computation, network download, and database operation are categorized as CPU-intensive tasks, I/O-intensive tasks, and synchronous tasks, and should be placed in subthreads to avoid lag and frame drops."
keywords: [time-consuming task, CPU-intensive, I/O-intensive, synchronous task, video encoding and decoding, compression and decompression, JSON parsing, network download, database operation]
doctype: guide
status: active
---

# Overview of Concurrency in Time-Consuming Tasks
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:50:52.508Z pushedAt=2026-11-12T13:36:49.752Z nl=1 -->


Time-consuming tasks are those that take a long time to complete. If executed in the UI main thread, they can cause application lag, frame drops, and slow response times. Typical examples include CPU intensive tasks, I/O intensive tasks, and synchronous tasks.


Typical service scenarios are as follows:


| Service Scenario| Description| Is CPU Intensive Task| Is I/O Intensive Task| Is Synchronous Task|
| -------- | -------- | -------- | -------- | -------- |
| Image/video encoding and decoding | Simply encode or decode an image or video and then display it. | Yes | Yes | No |
| Video export after editing | Encode and compress the edited video, and then export the file. | Yes | Yes | Yes |
| Compression and decompression| Decompressing local archives or compressing local files.| Yes| Yes| No|
| JSON parsing| Serializing and deserializing JSON strings.| Yes| No| No|
| Model computation| Performing data analysis using models.| Yes| No| No|
| Network download| Downloading resources, images, and files via intensive network requests.| No| Yes| No|
| Database operation | Save chat records, page layout information, music list information, and so on to the database; read the database to display related information when the application starts for the second time; and perform other synchronous transaction operations. | No | Yes | Yes |
| Synchronous file content read/write processing | Synchronously read file content and process it in place. | No | Yes | Yes |
