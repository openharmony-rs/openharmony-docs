# 容器类库概述
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @xliu-huanwei; @shilei123; @huanghello-->
<!--Designer: @yuanyao14-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

容器类库用于存储各种数据类型的元素，提供一系列处理数据的方法，作为纯数据结构容器具备高效处理特性。

容器类使用静态语言实现，限制了存储位置和属性，不支持自定义属性和方法，确保每种类型的数据在实现其功能的过程中避免冗余逻辑，从而实现高效的数据访问，提升应用性能。

当前提供了线性和非线性两类容器。[线性容器](linear-container.md)和[非线性容器](nonlinear-container.md)均非多线程安全的。
