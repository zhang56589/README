项目一：room-booking-service 企业内部资源预约管理平台
企业内部资源预约管理平台，前后端分离分布式预约平台
技术栈：SpringBoot3.4、Spring Cloud Alibaba、Nacos、RocketMQ、MySQL、Redisson
面向企业内部会议室资源预约审批场景，支持多实例集群部署。
• 独立负责预约核心模块，设计并发预约冲突控制方案，实现异步消息通知。
• Redisson 分布式锁 + MySQL 行锁双重保障，解决集群并发预约资源争抢冲突。
• Nacos 完成服务注册发现；RocketMQ 异步推送审批通知，削峰解耦，提升系统稳定性。

项目二：react-agent-secure 安全可控 ReAct 智能体系统
自研轻量安全可控 ReAct 智能 Agent，无重型框架依赖
技术栈：Python、pytest
自主实现 ReAct 推理循环，不依赖 LangChain，便于安全审计与权限管控。
• 手写 ReAct 主推理循环，自定义工具调用协议；实现文件访问控制，增加路径穿越防护模块。
• 封装网页搜索、安全文件读取工具；支持上下文摘要压缩、JSON 断点续跑、轮转日志、爬虫节流缓存。
• pytest 单元测试覆盖协议解析与安全校验逻辑，保障自动化回归。

项目三：offline-report-service 大数据离线报表任务服务
定时任务驱动的离线报表导出服务，支撑大批量业务数据统计与文件下载
技术栈：SpringBoot2.7、EasyExcel、Quartz、Redis、MySQL
• Quartz 实现分布式定时任务，通过锁机制避免集群任务重复执行。
• EasyExcel 流式读写，规避大数据导出引发的 OOM；Redis 缓存统计中间结果，降低数据库压力。
• 任务状态持久化，支持失败重试，完善异常处理机制。

项目四：game-strategy-platform 游戏攻略分享平台
传统 XML 配置式 SSM 游戏攻略社区，全程零注解，所有 Bean/AOP/Filter 通过 XML 配置
技术栈：Spring5、SpringMVC5、JdbcTemplate、MySQL8、Druid、JSP、Tomcat9
支持游客浏览、用户发布攻略、管理员内容审核与用户管理。
• 自定义 XSS、CSRF、权限校验 Filter，通过 DelegatingFilterProxy 托管，实现输入过滤、CSRF 校验、水平越权防护。
• XML 声明式 AOP 切面，拦截 Service 层自动写入审计日志，规避 AOP 递归拦截问题。
• 加盐 MD5 密码方案，完成新旧密码平滑迁移；实现攻略人工审核流程，未审核内容前台不可见。

项目五：swift-link-service 分布式短链接跳转服务
分布式短链接跳转服务，面向营销短信、渠道推广场景，支持多实例集群部署
技术栈：Java17、SpringBoot3.2、SpringCloudAlibaba、MySQL8、Redis7、Redisson、MyBatis-Plus、Nacos
提供短链生成、302 跳转、PV/UV 访问统计、过期失效、安全风控能力。
• 短码：雪花算法 + Base62 编码，Redis List 预生成短码池；Redisson 分层锁 + MySQL 唯一索引保证短码全局唯一。
• 缓存：Cache-Aside 架构，空值缓存防穿透、重建锁防热点击穿、TTL 随机抖动防止雪崩，状态变更主动失效缓存。
• 安全限流：Redis+Lua 原子脚本实现 IP / 短码双层限流；IP / 域名黑名单、内网地址拦截，防御开放重定向漏洞。
• 异步统计：独立线程池异步记录访问日志，Hash 统计 PV、HyperLogLog 估算 UV，定时任务幂等落库。
• 工程化：全局异常处理、统一返回体、Nacos 配置，编写单元测试，提供 SQL 脚本与集群部署方案。
