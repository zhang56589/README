# Backend & Security Portfolio
> Personal resume projects, covering distributed service, scheduling platform, security agent, monitoring & alert, legacy SSM system, big data offline task.
> 后端 & 安全方向个人作品集，用于简历展示。

## 1. room-booking-service
**Resource Scheduling Platform｜企业内部资源预约中台**
Tech Stack: SpringBoot, MyBatis, MySQL, Vue3, Element Plus

- 设计插件化资源调度模型，抽象资源类型、资源实例、调度插件三层架构，统一抽象会议室、工位、算力等可调度资源
- 实现 `TIME_EXCLUSIVE` 时段独占校验插件，新增同类资源无需修改核心调度逻辑，提升横向扩展能力
- 完整实现预约生命周期：提交、审批、取消、过期自动失效；定时任务自动回收超时未审批预约
- 数据库分层设计，单表统一承载多类型资源，业务表与资源抽象层解耦；采用软删除保证审计可追溯，附带初始化演示 SQL
- 前后端分离架构，后端提供标准化预约、查询、审批接口；前端实现资源浏览、预约表单、预约记录管理页面

👉 [View Repo](https://github.com/zhang56589/room-booking-service)

## 2. react-agent-secure
**Secure Controllable ReAct Agent｜安全可控 ReAct 智能体**
Tech Stack: Python, pytest

- 从零实现 ReAct 推理主循环，自定义工具调用协议，轻量无重型框架依赖，便于安全审计与权限管控
- 内置路径穿越防护模块，对文件访问能力做严格权限隔离；封装网页搜索、安全文件读取工具
- 支持上下文摘要压缩、JSON 断点续跑、轮转日志、爬虫节流缓存机制
- 基于 pytest 编写单元测试，覆盖协议解析、安全校验逻辑，支持自动化回归

👉 [View Repo](https://github.com/zhang56589/react-agent-secure)

## 3. offline-report-service
**Offline Report Task Service｜大数据离线报表任务服务**
Tech Stack: SpringBoot 2.7, EasyExcel, Quartz, Redis, MySQL

- 基于 Quartz 实现分布式定时任务，使用分布式锁避免集群节点重复调度
- EasyExcel 流式读写，解决大批量导出 OOM 问题；Redis 缓存统计中间结果，降低数据库压力
- 任务状态持久化，支持失败重试，完善异常捕获与容错处理

👉 [View Repo](https://github.com/zhang56589/offline-report-service)

## 4. game-strategy-platform
**Game Strategy Sharing Platform｜游戏攻略分享社区**
Tech Stack: Spring5, SpringMVC5, JdbcTemplate, MySQL8, Druid, JSP, Tomcat9
> Feature: Pure XML configuration, zero annotation for Bean / AOP / Filter

- 自定义 XSS、CSRF、权限校验 Filter，通过 DelegatingFilterProxy 注册，实现输入过滤、CSRF 校验、水平越权防护
- XML 声明式 AOP，拦截 Service 层自动写入审计日志，规避 AOP 自调用递归拦截问题
- 实现加盐 MD5 密码方案，支持新旧密码平滑迁移；搭建内容人工审核流程，未审核内容前台隔离

👉 [View Repo](https://github.com/zhang56589/game-strategy-platform)

## 5. swift-link-service
**Distributed Short Link Service｜分布式短链接跳转服务**
Tech Stack: Java17, SpringBoot3.2, SpringCloudAlibaba, MySQL8, Redis7, Redisson, MyBatis-Plus, Nacos

- 雪花算法 + Base62 生成短码，Redis 预生成短码池；Redisson 分层锁 + MySQL 唯一索引保障短码全局唯一
- Cache-Aside 缓存方案：空值缓存防穿透、重建锁防热点击穿、TTL 随机抖动规避缓存雪崩，数据变更主动失效缓存
- Redis+Lua 原子脚本实现 IP / 短码双层限流；配置 IP、域名黑名单，拦截内网地址，防范开放重定向漏洞
- 独立线程池异步埋点访问日志，Hash 统计 PV、HyperLogLog 估算 UV，定时任务幂等落库
- 全局异常处理器、统一返回体规范，Nacos 配置中心管理配置；附带单元测试、初始化 SQL、集群部署文档

👉 [View Repo](https://github.com/zhang56589/swift-link-service)

## 6. monitor-alert-platform
**Business Metric Monitor & Alert Platform｜业务指标监控告警平台**
Tech Stack: SpringBoot3.4, RocketMQ, Redis, Redisson, MySQL, Vue3

- 定时拉取业务指标，MySQL 持久化 + Redis 热缓存；利用唯一键 + `ON DUPLICATE KEY UPDATE` 保证采集幂等，防止集群脏数据
- 支持多指标规则配置、连续命中判定、告警静默窗口收敛；基于 ruleId + 时间窗口生成唯一告警编号，抑制告警风暴，指标恢复自动解除告警
- Redisson 分布式锁保证集群检测任务互斥；RocketMQ 解耦告警检测与推送，对接钉钉机器人（加签支持）、邮件渠道
- 告警通知表采用 alert_no + channel 联合唯一键，保证 MQ 重复消费不重复推送；支持 Redis 异常时缓存降级回源 MySQL
- Vue3 + ElementPlus 实现指标看板、告警规则配置、告警历史页面；REST API 对外暴露，支持 Docker 一键部署

👉 [View Repo](https://github.com/zhang56589/monitor-alert-platform)

---

## About Me
Backend developer focusing on distributed system, middleware, web security and observability.
If you are interested, welcome to contact me.
