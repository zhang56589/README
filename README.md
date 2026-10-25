# Backend & Security Portfolio
> Personal resume projects, covering resource scheduling, legacy SSM security, offline batch task, secure agent, distributed short link.
> 后端 & 安全方向个人作品集，用于简历展示。

## 1. resource-booking-platform
**Resource Scheduling Platform｜企业内部资源预约中台**
Tech Stack: SpringBoot, MyBatis, MySQL, Vue3, Element Plus

- 设计插件化资源调度模型，抽象「资源类型 / 资源实例 / 调度插件」三层架构，统一承载会议室、工位、算力等可调度资源
- 实现 `TIME_EXCLUSIVE` 时段独占校验插件，新增同类资源无需修改核心调度逻辑，提升横向扩展能力
- 完整实现预约生命周期：提交、审批、取消、过期自动失效；定时任务回收超时未审批预约
- 数据库分层设计，单表统一承载多类型资源，业务表与资源抽象层解耦；软删除保证审计可追溯，附初始化演示 SQL
- 前后端分离，后端提供标准化预约/查询/审批接口，前端实现资源浏览、预约表单、记录管理页面

👉 [View Repo](https://github.com/zhang56589/resource-booking-platform)

## 2. game-guide-community
**Game Strategy Sharing Platform｜游戏攻略分享社区**
Tech Stack: Spring5, SpringMVC5, JdbcTemplate, MySQL8, Druid, JSP, Tomcat9
> Feature: Pure XML configuration, zero annotation for Bean / AOP / Filter

- 自定义 XSS、CSRF、权限校验 Filter，通过 DelegatingFilterProxy 注册，实现输入过滤、CSRF 校验、水平越权防护
- XML 声明式 AOP 拦截 Service 层自动写入审计日志；针对 AOP 自调用导致拦截失效的问题，通过暴露代理对象重构调用链解决
- 实现加盐 MD5 密码方案，支持新旧密码平滑迁移；搭建内容人工审核流程，未审核内容前台隔离

👉 [View Repo](https://github.com/zhang56589/game-guide-community)

## 3. offline-report-service
**Offline Report Task Service｜大数据离线报表任务服务**
Tech Stack: SpringBoot 2.7, EasyExcel, Quartz, Redis, MySQL

- 基于 Quartz 实现分布式定时任务，使用分布式锁避免集群节点重复调度
- EasyExcel 流式读写解决大批量导出 OOM 问题；Redis 缓存统计中间结果，降低数据库压力
- 任务状态持久化，支持失败重试，完善异常捕获与容错处理

👉 [View Repo](https://github.com/zhang56589/offline-report-service)

## 4. secure-react-agent
**Secure Controllable ReAct Agent｜安全可控 ReAct 智能体**
Tech Stack: Python, pytest

- 从零实现 ReAct 推理主循环，自定义工具调用协议，轻量无重型框架依赖，便于安全审计
- 内置路径穿越防护模块，对文件访问能力做权限隔离；封装网页搜索、安全文件读取工具
- 基于 pytest 编写单元测试，覆盖协议解析与安全校验逻辑

👉 [View Repo](https://github.com/zhang56589/secure-react-agent)

## 5. swift-link-service
**Distributed Short Link Service｜分布式短链接跳转服务**
Tech Stack: Java17, SpringBoot3.2, MySQL8, Redis7, MyBatis-Plus

- 雪花算法 + Base62 生成短码，MySQL 唯一索引兜底并发场景下的短码全局唯一
- Cache-Aside 缓存方案，空值缓存防止缓存穿透

👉 [View Repo](https://github.com/zhang56589/swift-link-service)

---

## About Me
Backend developer focusing on distributed system, middleware, web security and observability.
If you are interested, welcome to contact me.
