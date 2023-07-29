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


