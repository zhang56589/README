项目一：企业内部资源预约管理平台｜前后端分离分布式预约平台
技术栈 ：SpringBoot3.4、Spring Cloud Alibaba、Nacos、RocketMQ、MySQL、Redisson
• 面向企业内部会议室资源预约审批场景，完成系统分布式改造，支持多实例集群部署。
• 独立负责预约核心模块开发，设计并发预约冲突控制方案，实现消息异步通知能力。
• 采用Redisson 分布式锁 + MySQL 行锁双重机制，解决集群环境下多用户并发预约资源冲突问题。
• 基于 Nacos 实现服务注册与发现；使用 RocketMQ 异步推送预约审批通知，削峰解耦，提升系统稳定性。

项目二：安全可控 ReAct 智能体系统
技术栈 ：Python、pytest
• 自研轻量 ReAct 智能 Agent，不依赖 LangChain 重型框架，底层逻辑自主实现，方便安全审计与权限管控。
• 手写 ReAct 推理主循环，自定义工具调用协议；实现文件访问安全控制，开发路径穿越防护模块。
• 封装网页搜索、安全文件读取工具；增加上下文摘要压缩、JSON 断点续跑、轮转日志、爬虫节流缓存能力。
• 编写 pytest 单元测试，覆盖协议解析与安全校验逻辑，保障自动化回归。

项目三：大数据离线报表任务服务
技术栈 ：SpringBoot2.7、EasyExcel、Quartz、Redis、MySQL
• 定时任务驱动的离线报表导出服务，支撑业务大批量数据统计与文件下载。
• 负责定时任务调度、大数据量导出方案设计，优化内存占用与任务异常处理。
• Quartz 实现分布式定时任务，通过锁机制防止集群任务重复执行；EasyExcel 流式读写规避 OOM。
• Redis 缓存统计中间结果，降低 DB 查询压力；任务状态持久化存储，支持失败重试。

项目四：GameStrategyPlatform 游戏攻略分享平台
技术栈 ：Spring5 + SpringMVC5 + JdbcTemplate + MySQL8 + Druid + JSP，Tomcat9， 全程零注解，Bean/AOP/Filter 全部 XML 配置
• 基于传统 SSM 开发游戏攻略社区，支持游客浏览、用户发布攻略、管理员审核与用户管理。
• 自定义 XSS、CSRF、权限校验 3 个 Filter，借助 DelegatingFilterProxy 交由 Spring 托管，实现输入过滤、CSRF 令牌校验、水平越权防护。
• XML 声明式 AOP 切面，拦截 Service 层方法自动写入审计日志，记录操作人、方法、参数、耗时，规避 AOP 递归拦截。
• 实现加盐 MD5 密码方案，兼容存量纯 MD5 老用户，完成新旧密码平滑迁移；设计攻略人工审核流程，未审核内容前台不可见。
• 基于 JdbcTemplate 开发 DAO 层，采用软删除，查询 SQL 增加业务权限过滤，落地多层 Web 安全能力。
