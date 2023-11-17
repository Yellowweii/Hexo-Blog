---
abbrlink: 19412
title: React组件在什么时候会重新渲染
tags:
  - React
categories:
  - React基本原理
date: 2023-11-17 11:07:20
cover: https://www.yellowwei.cn/img/2023-11-17.jpg
---

![](https://www.yellowwei.cn/img/640.jpg)

> 当我们使用 React 编写组件时，组件的重新渲染是一个重要的概念。重新渲染是指 React 组件在特定情况下会重新执行其渲染函数，更新用户界面以反映最新的数据。很多情况下，组件不必要的重新渲染会严重影响性能，所以要充分了解触发组件重新渲染的条件。

# Props 变化

> 在 React 中，组件的 props 是父组件传递给子组件的数据。当这些 props 发生变化时，子组件将重新渲染以反映最新的数据。

```JSX
// 父组件
const ParentComponent = () => {
  const [value, setValue] = useState(0);

  return <ChildComponent prop={value} />;
};

// 子组件
const ChildComponent = React.memo(({ prop }) => {
  // prop发生变化时，会触发重新渲染
  return <p>{prop}</p>;
});
```

# State 变化

> React 中的状态是通过 useState 来管理的。当使用 setState 函数更新状态时，组件将重新渲染。

```JSX

const Counter = () => {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1); // count发生变化时，组件重新渲染
  };

  return (
    <div>
      <p>{count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
};
```

# Context 变化

> React Context 允许我们在组件树中传递数据而不必一级一级手动传递。当 Context 的值发生变化时，订阅了该 Context 的组件将重新渲染。

```JSX

const MyComponent = () => {
  const contextValue = useContext(MyContext); // MyContext的值发生变化时，组件重新渲染

  // ...
};
```

# 使用 forceUpdate

> 虽然不推荐使用 forceUpdate，但在某些情况下，你可能需要强制组件重新渲染。forceUpdate 方法将会导致组件的 render 方法被调用。

```JSX

const MyComponent = () => {
  const forceUpdate = useForceUpdate();

  const handleClick = () => {
    // 强制组件重新渲染
    forceUpdate();
  };

  // ...
};
```

# 父组件重新渲染

> 当一个子组件嵌套在一个父组件中时，父组件重新渲染，子组件也会重新渲染。

```JSX

const ParentComponent = () => {
  // 状态变量 count
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Parent Component Count: {count}</p>
      <ChildComponent />
      <button onClick={() => setCount(count + 1)}>Increment Parent</button>
    </div>
  );
};

// 子组件
const ChildComponent = () => {
  console.log("Child Component Rendered");

  return <p>Child Component</p>;
};
```

# 总结

> 这些情况涵盖了导致 React 函数式组件重新渲染的主要场景。React 通过虚拟 DOM 检测这些变化，从而实现了高效的更新，确保用户界面保持最新。理解这些重新渲染的情况有助于我们更好地优化和设计 React 应用程序。
