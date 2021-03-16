# [Monorepos: Please don’t!](https://medium.com/@mattklein123/monorepos-please-dont-e9a279be011b)

- Monorepo 对立的是 Polyrepo
- Monorepo 并没有想象中有收益
    - 轻松协作与代码共享
        - 但提效的前提是
            - 有虚拟文件系统（ VFS ）支持，允许部分代码在本地显示
            - 完善的源代码索引 / 搜索 / 发现服务
    - 单一构建、无依赖管理
        - 肯定不会去 rebuild 整个工程，因此依赖于复杂的构建系统
            - Google 的 Bazel/Blaze 和 Facebook 的 Buck
                - 内部跟踪依赖关系并构建有向无环图（ DAG ）
    - 代码重构很容易 / 原子提交
        - 作者认为整体操作 / 需要相互依赖重构的概率很低
- Monorepo 独有的缺点：
    - 紧密耦合
        - 边界不清晰，没有物理隔离是脆弱的
            - 大型项目尤为重要，应当去考虑职责
    - 不利于使用 OSS
        - 追踪和代码流动控制
    - VCS 可扩展性
        - Git 会慢
- 个人观点：
    - 大型 Monorepo 需要良好的基础设施支持
    - 应用级别的项目谨慎使用 Monorepo，从业务到源码再到产物上通常都需要有明确的边界，Mono 容易使其变模糊
    - 基础库可能会适合用 Monorepo，在协作上会体现出易于共享、沟通、索引的优势，需要做好版本控制
- 代码的组织是一家公司工程文化和领导才能的直接结果体现，与使用 Monorepo 与 Polyrepo 无关