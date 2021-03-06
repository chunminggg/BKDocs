
### 请求地址

/api/c/compapi/v2/job/save_cron/



### 请求方法

POST


### 功能描述

新建或保存定时作业；新建定时作业，定时任务状态默认为暂停。

### 请求参数


#### 通用参数

| 字段 | 类型 | 必选 |  描述 |
|-----------|------------|--------|------------|
| bk_app_code  |  string    | 是 | 应用 ID     |
| bk_app_secret|  string    | 是 | 安全密钥(应用 TOKEN)，可以通过 蓝鲸智云开发者中心 -&gt; 点击应用 ID -&gt; 基本信息 获取 |
| bk_token     |  string    | 否 | 当前用户登录态，bk_token 与 bk_username 必须一个有效，bk_token 可以通过 Cookie 获取 |
| bk_username  |  string    | 否 | 当前用户用户名，应用免登录态验证白名单中的应用，用此字段指定当前用户 |

#### 接口参数

| 字段            |  类型      | 必选   |  描述      |
|-----------------|------------|--------|------------|
| bk_biz_id       |  long       | 是     | 业务 ID |
| bk_job_id       |  long       | 是     | 要定时执行的作业的作业执行方案 ID |
| cron_id         |  long       | 否     | 定时任务 ID，更新定时任务时，必须传这个值 |
| cron_name       |  string    | 否     | 定时作业名称，新建时必填，修改时选填 |
| cron_expression |  string    | 否     | 定时任务 crontab 的定时规则，新建时必填，修改时选填，各字段含义为：分 时 日 月 周，如: 0/5 * * * ? 表示每 5 分钟执行一次 |

### 请求参数示例

```python
{
    "bk_app_code": "esb_test",
    "bk_app_secret": "xxx",
    "bk_token": "xxx",
    "bk_biz_id": 1,
    "bk_job_id": 100,
    "cron_name": "test",
    "cron_expression": "0/5 * * * ?"
}
```

### 返回结果示例

```python
{
    "result": true,
    "code": 0,
    "message": "success",
    "data": {
        "cron_id": 1
    }
}
```