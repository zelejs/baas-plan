## 计划服务

所有 BaaS 服务仅定义关键逻辑字段，其他实体字段由表单提供, 提询时聚合表单数据

- baas_t_plan

### 1 计划关键字段

| 属性            | 数据类型     | 备注                                   |
| --------------- | ------------ | -------------------------------------- |
| id              | long         | 计划表索引ID                           |
| plan_id         | varchar(50)  | 计划ID                                 |
| create_at       | datetime     | 计划创建时间                           |
| update_at       | datetime     | 计划更新时间                           |
| start_time      | datetime     | 计划开始时间                           |
| end_time        | datetime     | 计划结束时间                           |
| times           | int          | 总次数                                 |
| frequency       | int          | 时间单位内的频次                       |
| frequency_unit  | varchar      | per [SEC, MIN, HOUR, DAY, MONTH, YEAR] |
| plan_entity_id  | long         | 计划内容ID （子表或表单）              |
| user_ref_id     | long         | 用户表索引 ID                          |
| user_id         | varchar(50)  | 用户ID                                 |
| job_cron_format | varchar(100) | 自动生成计划的CRON格式计划             |
|                 |              |                                        |

#### 1.1 计划对象关键字段

| 属性        | 数据类型    | 备注             |
| ----------- | ----------- | ---------------- |
| id          | long        | 计划表索引ID     |
| plan_ref_id | long        | 计划表ID         |
| plan_id     | varchar(50) | 计划编号         |
| create_at   | datetime    | 计划对象生成时间 |
|             |             |                  |


### 2 API

| 服务         | API                                  | 说明                                                                   |
| ------------ | ------------------------------------ | ---------------------------------------------------------------------- |
| 生成计划对象 | POST /api/baas/plan/plans/action/new | 即时生成计划对象，当前时间不在时间段内，不会生成；在时间段内，生成计划 |
|              |                                      |                                                                        |
