# 代码不朽 编写可维护软件的10大要则

## 第一章 简介

### 1.1 什么是可维护性？

国际标准ISO/IEC 25010:2011将软件质量划分为八个特征：可维护性、功能可适性、性能效率、兼容性、可使用性、可靠性、安全性、可移植性。

软件维护的四种方式：

- 发现并修复bug（纠正性维护）
- 系统需要去适应操作环境的改变（可适应性维护）
- 系统用户有新的需求，或者对之前的需求有变化（完善性维护）
- 确定可以改进质量或者预防将来可能产生的bug的方法（预防性维护）

### 1.2 为什么维护性很重要？

- 低可维护性会对业务造成严重影响
- 可维护性是其他质量特征的推动者

### 1.3 本书的三个基本理论

1. 简单的原则最有助于提高可维护性
1. 可维护性不是开发完成后才去考虑的，而应该是在项目开发的一开始就加以考虑。每一个人的贡献都应当计算在内。
1. 对各原则的违背会带来不同的影响，有些严重程度甚于其他。一个软件系统越遵守原则，可维护性越高。

### 1.6 可维护性原则的概述

- **编写短小的代码单元**。短小的代码单元更易于分析、测试和重用。
- **编写简单的代码单元**。拥有更少决策点的代码单元更易于分析和测试。
- **不写重复代码**。任何时候都应该避免源代码重复使用，因为修改时就需要对每处代码都进行修改。重复代码也是产生回归bug的一个来源。
- **保持代码单元的接口简单**。含有更少参数的代码单元更易于测试和重用。
- **分离模块之间的关注点**。松耦合的模块更易于修改，也利于构建更加模块化的系统。
- **架构组件松耦合**。系统的顶层组件之间越是松耦合，越易于修改，也利于构建更加模块化的系统。
- **保持架构组件之间的平衡**。一个平衡度很好的架构拥有不多不少的组件、统一的代码规模以及最大程度的模块化，并通过隔离关注点使得修改变得很容易。
- **保持小规模代码库**。大型系统之所以难以维护，因为需要分析、修改并测试更多的代码。同样，大型系统中维护每一行代码的效率也比小型系统要低。
- **自动化开发部署和测试**。自动化测试可以得到对修改的有效性的即时反馈。手工测试无法形成规模。
- **编写简洁的代码**。代码库中存在越多的TODO、无用代码等遗留产物，新的团队成员就越难高效工作，从而影响维护工作的效率。

## 编写短小的代码单元

原则：

- 代码单元的长度应该限制在15行代码以内。
- 为此首先不要编写超过15行代码的单元，或者将长的单元分解成多个更短的单元，直到每个单元都不超过15行代码。
- 该原则能提高可维护性的原因在于，短小的代码单元易于理解、测试及重用。

### 2.2 如何使用本原则

- 当编写一个新的代码单元时
- 当向代码单元中添加新功能时
- 使用重构技巧来应用原则：
  + 重构技巧：提取方法
  + 重构技巧：将方法替换为方法对象*

*注： 在提取方法时，可能会有大量的局部变量需要作为参数传递，此时可以将方法替换为方法对象，需要提取的方法则作为这个类的方法，部分参数可以转换为类的属性，这样就不需要在调用时传递了。

## 第3章 编写简单的代码单元

- 限制每个代码单元分支点的数量不超过4个。
- 你应该将负载的代码单元拆分成多个简单的单元，避免多个复杂的单元在一起。
- 该原则能提高可维护性的原因在于，分支点越少，代码单元越容易被修改和测试。

分支点包括：`if`,`case`,`?`,`&&,||`,`while`,`for`,`catch`

## 第4章 不写重复代码

原则：

- 不要复制代码
- 你应该编写可重用的、通用的代码，并且/或者调用已有的代码
- 该原则能提高可维护性的原因在于，如果复制代码，就需要在多个地方修复bug，这样做不近低效，而且容易出错。

编码是为了发现特定问题的通用方案。你应该重用（通过调用）代码库中已有的、通用的方法，或者让已有方法变得更加通用。

“**重复代码**”的定义：一段至少6行都相同的代码（不包括空行和注释）。

### 4.2 如何使用本原则

1. 提取方法
1. 提取到父类

## 第5章 保持代码单元的接口简单

原则：

- 限制每个代码单元的参数不能超过4个。
- 你应该将多个参数提取成对象。
- 该原则能提高可维护性的原因在于，较少的参数可以让代码单元更容易理解和重用。

## 第6章 分离模块之间的关注点

原则：

- 避免形成大型模块，以便能达到模块之间的松耦合。
- 你应该将不同的职责分给不同的模块，并且隐藏接口内部的实现细节。
- 该原则能提高可维护性的原因在于，相比起紧耦合的代码库来说，对松耦合代码库的修改更容易监督和执行。

## 第7章 架构组件松耦合

原则：

- 顶层组件之间应该做到松耦合。
- 你应该尽可能减少当前模块中需要暴露给其他组件中模块的相关代码。
- 该原则能提高可维护性的原因在于，独立的组件可以单独进行维护。

## 第8章 保持架构组件之间的平衡

原则：

- 你需要平衡代码中顶层组件的数量和体积。
- 你应该保持源代码中组件的数量接近于9（例如，在6和12之间），并且这些组件的体积基本一致。
- 该原则能提高可维护性的原因在于，平衡的组件可以帮助定位代码，并且允许独立对组件进行维护。

## 第9章 保持小规模代码库

原则：

- 保持代码库规模尽可能小。
- 你应该控制代码库增长，并主动减少系统的代码体积。
- 该原则能提高可维护性的原因在于，拥有小型的代码、项目和团队是成功的一个因素。

## 第10章 自动化开发部署和测试

原则：

- 对你的代码进行自动化测试。
- 你应该通过使用测试框架来编写自动化测试。
- 该原则能提高可维护性的原因在于，自动化测试让开发过程可预测并且能够降低风险。

## 第11章 编写简洁的代码

原则：

- 编写简洁的代码。
- 你不应该在完成开发工作后留下代码怀味道。
- 该原则能提高软件可维护性的原因在于，简洁的代码是可维护的代码。

如何使用本原则：

1. 不要编写单元级别的代码坏味道。
    - 过长的代码单元❌
    - 复杂的代码单元❌
    - 长接口的代码单元（参数过多）❌
1. 不要编写不好的注释。
1. 不要注释代码。
1. 不要保留废弃代码。
1. 不要使用过长的标识符名称。
1. 不要使用魔术常量。
1. 不要使用未正确处理的异常。
    - 应该捕获一切异常。
    - 应该捕获特定异常，不要捕获通用如Exception，RuntimeException
    - 在展示给终端用户之前，先将特定的异常信息转换成通用的信息。
