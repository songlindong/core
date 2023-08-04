## Vue3初始化流程分析
 - 应用程序实例创建过程 -> createApp()
  - 问题：如何创建实例，实例长什么样？
    - 创建实例：renderer.createApp()
    - 实例：{use(){}, component(){}, mount(){}}
 - 挂载过程   app.mount()
  - 问题：挂载都做了什么？
   - 创建根节点vnode
   - 执行render(虚拟dom生成真实dom)
    - 第一步生成vnode传递给patch函数转换为dom
    - 追加到宿主元素

- 总结：传入组件数据和状态转换为dom，并追加到宿主元素

### 思考
- 初始化方式的变化及原因

## Vue3更新流程分析
- setupRenderEffect建立更新机制
 - 当前组件响应式数据发生变化重新执行更新函数
 - 内部会调用patch

## Vue3 Composition API探究
包括：setup函数、生命周期钩子、getCurrentInstance、
Provide/Inject
动机：可维护性、逻辑复用

体验： 结合reactivity、生命周期钩子、属性/上下文

问题：
- setup函数执行的时刻，为什么没有created钩子？
 - mount -> render -> patch -> processComponent -> 
 moumtComponent -> 
  - 创建组件实例
  - 组件初始化setupComponent(instance)

- 回答：
 - 执行时刻早于beforeCreated和created之类的传统生命周期钩子。实际上在setup函数执行的时候，组件实例已经创建了，所以在setup中去处理beforeCreate和created是没有意义的
- 传入setup参数中，分别是props和ctx，它们从何而来，又是什么？
- 如果和data这些数据发生冲突，它们呢能共存吗？Vue3处理时的行为


## Vue3 Reactivity API探究
