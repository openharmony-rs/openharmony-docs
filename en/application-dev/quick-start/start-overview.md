# Preparations for Development

This document is intended for novices at developing OpenHarmony applications. By building a simple application with page navigation (as shown below), you will better understand the project directory and the typical OpenHarmony application development process.

![en-us_image_0000001364254729](figures/en-us_image_0000001364254729.png)

Before you begin, there are two basic concepts that will help you better understand OpenHarmony: UI framework and application model.


## Basic Concepts


### UI Framework

OpenHarmony provides a UI development framework, known as ArkUI. ArkUI provides a full range of capabilities you may need for application UI development, ranging from components to layout calculation, animation, UI interaction, and rendering capabilities.

ArkUI comes with two development paradigms: ArkTS-based declarative development paradigm (declarative development paradigm for short) and JavaScript-compatible web-like development paradigm (web-like development paradigm for short). You can choose whichever development paradigm that aligns with your practice.

| **Development Paradigm**| **Programming Language**| **UI Update Mode**| **Applicable To**                    | **Intended Audience**                          |
| ---------------- | ------------ | -------------- | -------------------------------- | -------------------------------------- |
| Declarative development paradigm  | ArkTS   | Data-driven  | Applications involving technological sophistication and teamwork| Mobile application and system application developers|
| Web-like development paradigm   | JavaScript      | Data-driven  | Applications with simple UIs and service widgets    | Frontend web developers                       |

For more details, see [About This Kit](../ui/arkui-overview.md).

### Application Model

The application model abstracts the capabilities required by an application and provides components and mechanisms required for running the application. By adhering to a unified model, you can streamline application development, making it more efficient and straightforward. For details, see [Elements of the Application Model](../application-models/application-models.md#elements-of-the-application-model).

Along its evolution, OpenHarmony has provided two application models:

- **Stage model**: This model is supported since API version 9. It is recommended. In this model, classes such as **AbilityStage** and **WindowStage** are provided as the stage of application components and windows. That's why it is named stage model. For details about development based on the stage model, see [Stage Model Development Overview](../application-models/stage-model-development-overview.md). The examples in this topic are all based on the stage model.

- **Feature Ability (FA) model**: This model is supported since API version 7. It is no longer recommended. For details about development based on the FA model, see [FA Model Development Overview](../application-models/fa-model-development-overview.md).  

For details about the differences between the FA model and stage model, see [Application Models](../application-models/application-models.md).

To help you better understand the preceding basic concepts and application development process, **Quick Start** walks you through an example of building your first ArkTS application with two pages in the stage model.


## Tool Preparation

Install the latest version of [DevEco Studio](https://developer.huawei.com/consumer/en/download/).

When you finish tool preparation and basic concept learning, you can set out to [build your first ArkTS application in the stage model](start-with-ets-stage.md).
