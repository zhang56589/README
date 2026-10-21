项目一：room-booking-service 企业内部资源预约管理平台
分布式企业会议室预约审批平台，前后端分离，支持多实例集群部署
技术栈：SpringBoot3.4、Spring Cloud Alibaba、Nacos、RocketMQ、MySQL、Redisson  
・独立负责预约核心模块，设计并发预约冲突控制方案，实现审批消息异步通知。
・采用 Redisson 分布式锁 + MySQL 行锁双重防护，解决集群场景下资源预约并发争抢冲突。
・Nacos 实现服务注册与配置管理；RocketMQ 异步解耦审批通知，削峰填谷，提升系统稳定性。

项目二：react-agent-secure 安全可控 ReAct 智能体系统
自研轻量安全 ReAct 智能 Agent，无重型框架依赖，便于安全审计与权限管控
技术栈：Python、pytest  
・手写 ReAct 主推理循环，自定义工具调用协议，实现文件访问控制，增加路径穿越防护模块。
・封装网页搜索、安全文件读取工具；支持上下文摘要压缩、JSON 断点续跑、轮转日志、爬虫节流缓存。
・使用 pytest 编写单元测试，覆盖协议解析与安全校验逻辑，保障自动化回归测试。

项目三：offline-report-service 大数据离线报表任务服务
定时任务驱动的离线报表导出服务，支撑大批量业务数据统计与文件下载
技术栈：SpringBoot2.7、EasyExcel、Quartz、Redis、MySQL  
・基于 Quartz 实现分布式定时任务，通过分布式锁防止集群多节点重复执行任务。
・使用 EasyExcel 流式读写，避免大数据导出场景 OOM；Redis 缓存统计中间结果，降低数据库查询压力。
・任务状态持久化存储，支持失败重试，完善异常捕获与处理机制。

项目四：game-strategy-platform 游戏攻略分享平台
基于 XML 配置式 SSM 社区系统，全程零注解，Bean、AOP、Filter 全部通过 XML 配置
技术栈：Spring5、SpringMVC5、JdbcTemplate、MySQL8、Druid、JSP、Tomcat9  
・自定义 XSS、CSRF、权限校验 Filter，通过 DelegatingFilterProxy 托管，完成输入过滤、CSRF 校验、水平越权防护。
・通过 XML 声明式 AOP 切面，拦截 Service 层自动写入审计日志，规避 AOP 递归拦截问题。
・实现加盐 MD5 密码方案，完成新旧密码平滑迁移；搭建攻略人工审核流程，未审核内容前台不可见。

项目五：swift-link-service 分布式短链接跳转服务
面向营销短信、渠道推广场景的分布式短链接服务，支持多实例集群部署
技术栈：Java17、SpringBoot3.2、SpringCloudAlibaba、MySQL8、Redis7、Redisson、MyBatis-Plus、Nacos  
・雪花算法 + Base62 生成短码，Redis 预生成短码池；Redisson 分层锁 + MySQL 唯一索引保证短码全局唯一。
・采用 Cache-Aside 缓存架构，空值缓存防穿透、重建锁防热点击穿、TTL 随机抖动避免缓存雪崩，数据变更主动失效缓存。
・Redis+Lua 原子脚本实现 IP / 短码双层限流；配置 IP、域名黑名单，拦截内网地址，防御开放重定向漏洞。
・独立线程池异步记录访问日志，Hash 统计 PV、HyperLogLog 估算 UV，定时任务幂等落库。
・实现全局异常处理、统一返回体、Nacos 配置管理，编写单元测试，提供 SQL 脚本与集群部署方案。

项目六：monitor-alert-platform 业务指标监控告警平台
独立开发业务指标监控告警平台，实现指标采集、阈值检测、告警收敛、多渠道推送，支持集群部署
技术栈：SpringBoot3.4、RocketMQ、Redis、Redisson、MySQL、Vue3  
・定时拉取业务指标，MySQL 持久化 + Redis 热缓存，利用唯一键 + ON DUPLICATE KEY UPDATE 实现指标采集幂等，避免集群重复采集产生脏数据。
・支持多指标规则配置、连续命中判定、静默窗口告警收敛；通过 ruleId + 时间窗口生成唯一告警编号，抑制告警风暴，指标回落自动恢复告警。
・Redisson 分布式锁保证集群检测任务互斥；RocketMQ 解耦告警检测与消息推送，对接钉钉机器人（支持加签）、邮件推送。
・告警通知表采用 alert_no+channel 联合唯一键，保证 MQ 重复消费不产生重复推送；设计缓存降级，Redis 异常自动回源 MySQL。
・Vue3+ElementPlus 开发指标看板、告警规则配置、告警历史页面，提供 REST 接口，支持 Docker 一键部署。
