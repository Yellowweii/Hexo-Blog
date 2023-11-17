---
title: 对Framer Motion的理解
tags:
  - Framer Motion
categories:
  - React动画库
cover: 'https://www.yellowwei.cn/img/2023-11-14.jpg'
abbrlink: 7841
date: 2023-11-14 19:54:30
---

# 什么是 Framer Motion

> Framer Motion 是一个用于 React 应用程序的动画库，它提供了一套简单而强大的工具，用于实现在 Web 应用中创建流畅的动画和交互效果。

# 声明式动画

> Framer Motion 支持声明式的动画定义。通过在组件中使用 JSX 语法，你可以轻松地声明需要应用的动画效果，而不必直接操作 DOM 或编写复杂的动画代码。

```JSX
import { motion } from "framer-motion";

const ExampleComponent = () => {
  return (
    <motion.div animate={{ x: 100, opacity: 0.5 }}>
      Hello, Framer Motion!
    </motion.div>
  );
};

```

# Variants

> 通过 variants 属性，你可以定义一组状态变化，并在动画中切换这些状态。这样可以更灵活地管理和控制动画效果。

```JSX
const variants = {
  hidden: { opacity: 0 },
  visible: { opacity: 1 },
};

const ExampleComponent = () => {
  return (
    <motion.div variants={variants} initial="hidden" animate="visible">
      Hello, Framer Motion!
    </motion.div>
  );
};

```

# 过渡

> Framer Motion 支持过渡效果，你可以定义元素从一个状态平滑过渡到另一个状态的动画效果。

```JSX
const ExampleComponent = () => {
  return (
    <motion.div
      initial={{ opacity: 0 }}
      animate={{ opacity: 1 }}
      transition={{ duration: 1 }}
    >
      Hello, Framer Motion!
    </motion.div>
  );
};

```

# Layout动画

> Framer Motion 允许你轻松实现与布局相关的动画，例如元素的位置、大小等变化。

```JSX
const ExampleComponent = () => {
  return (
    <motion.div layout>
      <p>Content</p>
    </motion.div>
  );
};

```
