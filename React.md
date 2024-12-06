### 1. React state和props区别是什么 ?

|          |       state        |                    props                    |
| :------: | :----------------: | :-----------------------------------------: |
|   定义   | 状态，用于可变数据 |             属性，只读不可修改              |
| 更改方式 |      setState      |                 父组件传递                  |
| 使用场景 |    管理动态数据    |        父传子，便于不同组件共享数据         |
| 生命周期 |  变化的，可以修改  | 父组件重新渲染，子组件接收新的props重新渲染 |

### 2. 什么是 Redux？

**核心概念**

1. Store: 存储整个应用的状态树
2. Action: 描述发生什么事情的js对象
3. Reducer: 纯函数，接受当前的状态和Action作为参数，返回一个新的状态
4. Dispatch: 发送Action给Store方法，通过调用`store.dispatch(action)`，触发状态更新
5. Middleware: 处理Action发送后到达Reducer之间的逻辑

**优点**

1. 集中化状态管理
2. 通过Reducers函数处理状态变化，便于调试
3. 开发工具多
4. 可通过中间件扩展和增强功能

**使用方法**

通过`React-Redux库`，使用`Provider`和`connect`函数

### 3. element和component区别

|      |           element           |                     component                     |
| :--: | :-------------------------: | :-----------------------------------------------: |
| 定义 |    描述UI的对象，不可变     |    具有状态和行为的功能模块，可以**接受props**    |
| 类型 | 原生HTML元素/用户自定义组件 | 无状态的函数组件/有状态的类组件，可以**返回元素** |
| 用途 |       描述UI某一部分        |      封装逻辑和视图，管理状态，**可复用性**       |
|      |       仅**静态**描述        |             有**状态和生命周期**概念              |

### 4. 如何在React中时使用样式

1. **内联样式**：jsx中通过style属性传递
2. **css传统样式表**：.css，通过import引入
3. **css Modules**：限制在组件范围内
4. **Styled Components**： 允许使用js写样式
5. **Emotion**：类似4
6. **Tailwind CSS**：在jsx中结合使用className
7. **Sass/Less**：预处理器，通过Webpack

### 5. 简述React有什么特点

1. **组件化**：将UI拆分成独立、可重用的组件，便于维护和管理
2. **虚拟DOM**：优化渲染性能，状态变化时，先在虚拟中计算实际DOM的最小变更
3. **单向数据流**：父组件通过props将数据传递给子组件
4. **声明式编程**：以此构建UI
5. **状态管理**：允许通过local state、context API以及外部库进行状态管理
6. **生态系统丰富**：包括路由、状态管理等
7. **跨平台**：支持Web和React Native，可用于开发移动应用
8. **结合Hooks**

### 6. key的作用

1. **唯一标识**：一个字符串或数字，用于标识列表中的每个元素，帮助React识别那些元素改变、添加或删除
2. **优化渲染**：遇到元素变化时，只更新变化的部分，提高性能，与视觉效果无关
3. **保持组件状态**：当列表中某个元素有输入框且重排位置，可以保持住数据不丢失

如何使用？

```tsx
const items = ['Apple', 'Banana', 'Cherry'];

const itemList = items.map((item, index) => (
  <li key={item}>{item}</li>
));
```

需要使用唯一ID

### 7. setState调用后发生了什么？是同步还是异步？

1. **状态更新请求**：标记组件的状态为需要更新，并合并状态
2. **重新渲染**：将更新请求推入一个批处理队列，不会立刻渲染
3. **合并状态**：将其与当前状态合并
4. **异步处理**：会将多个状态更新合并为一个批量更新，减少渲染次数
5. **生命周期方法**：执行相应的生命周期方法，如componentDidUpdate,并触发组件的重新渲染
6. **重新渲染与DOM更新**：计算最小的DOM更新并应用这些变化，以实现高效的UI更新

### 8. 为什么使用Hook？

1. **状态与副作用管理**
2. **提高代码复用性**：创建自定义Hooks，共享业务逻辑
3. **简化组件结构**：减少组件的嵌套层级
4. **更好的组合性**：逻辑分散到多个Hooks，需要的地方组合
5. **避免this的问题**：不需要处理this的绑定问题，使状态和方法的访问变得更加直接和清晰
6. **更好的性能优化**：使React组件的更新和重渲染逻辑更精细化

### 9. 类组件和函数组件的区别

|              |                类组件                 |              函数组件              |
| :----------: | :-----------------------------------: | :--------------------------------: |
|   声明方式   |    ES6语法，继承自React.Component     |    简单的js函数，接受props参数     |
|   状态管理   | 内部管理，如this.state和this.setState |        useState等hooks管理         |
| 生命周期方法 |                  有                   | 无，但用useEffect Hook来处理副作用 |
|     性能     |      实例化和生命周期管理，较重       |               轻量级               |
|  理解和使用  |   复杂的生命周期和深层嵌套比较复杂    |              简洁易懂              |
|    Hooks     |                  无                   |                可以                |
|  先后兼容性  |              适合旧项目               |     适合新项目，React 16.8之后     |

### 10. 如何避免不必要的render?

1. **Pure Component**：进行浅比较，只有在变化时才重新渲染
2. **React.memo**：函数组件，允许自定义比较函数决定组件是否需要更新
3. **shouldComponentUpdate**：类组件，实现生命周期方法手动控制组件是否渲染
4. **useMemo和useCallback**：缓存计算结果和函数，只有在依赖项变化时才更新
5. **控制状态提升**：状态放在尽量低的层级，局部状态控制
6. **使用Context**：选择性重构Context提供值，避免不必要的渲染
7. **避免匿名函数再渲染**
8. **防止不必要的props变化**，设计良好的prop结构
9. **使用key属性**：有助于识别元素的变化，减少重渲染

### 11.  Redux原理和工作流程

**原理：**

1. 维护一个全局状态树，是整个应用的唯一数据源
2. 状态只读，唯一可以改变状态是触发一个动作
3. 状态的变化由纯函数处理，接受当前的状态和一个动作，并返回一个新的状态

**工作流程：**

1. 通过`createStore`创建一个Redux store，并把根reducer传给它
2. 定义一个Action，必须要有一个type属性，描述动作类型
3. 定义Reducer，接受当前状态和一个action，并返回新的状态
4. 通过`store.dispatch()`方法发送一个action，通知Redux需要更改状态
5. 更新Stare，根据接受的action返回新的状态树
6. 组件通过`store.subscribe()`来获得状态更新通知
7. 使用react-redux提供的Provider组件将Redux store提供给React组件，组件通过connect或者hook来访问和操作Redux store状态

### 12. 哪些方法会触发React重新渲染？重新渲染render会做什么？

**触发重新渲染：**

1. **状态更新**：调用组件的`setState`方法
2. **属性变化**：父组件的`props`发生变化
3. **上下文变化**：使用`Context API`时
4. **强制更新**：调用组件的`forceUpdate`方法
5. **React.memo**：`props`比较失败

**render方法做什么：**

1. **计算虚拟DOM**
2. **比较虚拟DOM**
3. **更新真实DOM**
4. **调用生命周期方法**：类组件
5. **调用现有Hooks**：函数组件
6. **执行副作用**

### 13. React Hook的理解和实现原理

**理解：**

1. **状态管理**：通过`useState`，创建状态变量
2. **副作用处理**：通过`useEffect`，控制组件更新或卸载时的清理行为
3. **自定义Hook**：创建自己的Hooks，封装共享逻辑
4. **规则**：只能在最顶层调用Hooks，不能在循环、条件、嵌套函数调用；只能在React函数组件或自定义Hook调用

**实现原理：**

1. **调用栈**：每次组件渲染，Hooks根据调用顺序被注册和更新
2. **Fiber架构**：每次渲染，在fiber节点上关联状态和副作用
3. **状态存储**：`useState`会在组件某个内部结构存储状态，每次渲染时，React会返回对应的状态值和更新函数
4. **效应的调度**：`useEffect`会在组件首次渲染和更新后运行副作用函数

### 14. 父子组件的通信方式

1. **props**：单向数据流的基本方式，父->子
2. **回调函数**：回调函数作为props传给子组件，用于子组件向父组件发送数据或通知父组件发生改变
3. **Context API**：多个组件需要共享数据或函数
4. **Refs**：父组件直接访问子组件的实例，但增加耦合度，少用
5. **状态提升**：多个子组件需要共享状态，状态提升到最近的公共父组件

### 15. 虚拟DOM的概念和机制

**概念：**

对真实DOM的抽象表示，是一个轻量级的js对象，并不与浏览器实际DOM交互，允许开发者在内存中操作，而非频繁修改真实DOM，从而提高性能。

**机制：**

1. **创建虚拟DOM**：定义React组件时，将组件结构转化为一个虚拟DOM树
2. **render过程**：组件发生变化，调用render，生成新的虚拟DOM
3. **比较差异**：用一种高效Diff算法对比新旧虚拟DOM树
4. **批量更新**：根据差异化结果，最小化对真实DOM的操作，仅更新变化的部分，而不是整个DOM
5. **更新真实DOM**

### 16. 解释React组件的生命周期方法

**挂载：**

组件被创建到放入DOM中

主要生命周期方法

- `consrtuctor(props)`：构造函数，初始化和绑定方法
- `static getDerivedStateFromProps(props, state)`：根据props更新state
- `render`：必须实现，返回一个React元素
- `componentDidMount`：组件已经挂载后调用

**更新：**

当前组件state或props发生变化，重新渲染

主要生命周期方法：

- `static getDerivedStateFromProps(props, state) `：根据props更新state
- `shouldComponentUpdate(nextProps, nextState)`：决定组件是否应该更新，返回布尔值
- `render`：必须实现，返回一个React元素
- `getSnapshotBeforeUpdate(prevProps, prevState)`：更新被渲染DOM之前调用
- `componentDidUpdate(prevProps, prevState, snapshot)`：组件更新完成后调用

**卸载：**

组件从DOM中移除

- `componentWillUnmount()`：清理，如取消订阅和清除定时器

### 17. 为什么调用setState而不是直接改变state

1. **状态管理**：直接修改state可能导致组件无法感知到状态的变化，从而不会重新渲染
2. **异步更新**：React会在需要时批量处理状态更新以优化性能，直接用state可能导致不一致的组件渲染
3. **生命周期管理**：确保在状态变更后，执行正确的组件生命周期方法
4. **不可变性**：`state` 的不可变性原则，更容易追踪变化
5. **合并更新**：与当前状态合并

### 18. 生命周期调用方法的顺序

**挂载：**

constructor` -> `getDerivedStateFromProps` -> `render` -> `componentDidMount

初始化状态和绑定方法->根据props更新state->返回要渲染的JSX->组件挂载后立即调用

**更新：**

getDerivedStateFromProps` -> `shouldComponentUpdate` -> `render` -> `getSnapshotBeforeUpdate` -> `componentDidUpdate

根据props更新state->决定组件是否渲染->生成新的JSX->在最后一次渲染前调用->更新完立刻调用

**卸载：**

componentWillUnmount

销毁