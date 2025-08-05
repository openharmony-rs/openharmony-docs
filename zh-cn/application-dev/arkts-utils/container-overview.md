# 容器类库概述
<!--Kit: ArkTS-->
<!--Subsystem: commonlibrary-->
<!--Owner: @xliu-huanwei; @shilei123; @huanghello; @yuanyao14; @lzj0614-->
<!--SE: @yuanyao14-->
<!--TSE: @kirl75; @zsw_zhushiwei-->

容器类库用于存储各种数据类型的元素，提供一系列处理数据的方法，作为纯数据结构容器具有一定的优势。

容器类采用静态语言方式实现，限制存储位置和属性，确保每种类型的数据都能在完成自身功能的同时去除冗余逻辑，从而实现高效的数据访问，提升应用性能。

当前提供了线性和非线性两类容器。[线性容器](linear-container.md)和[非线性容器](nonlinear-container.md)均非多线程安全的。
