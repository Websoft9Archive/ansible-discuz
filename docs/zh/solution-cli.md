# CLI

DiscuzQ 提供了一套功能强大的命令行工具，用于管理站点，升级系统。

```
$ cd /data/wwwroot/discuz
$ php disco
 _____   _                           _____   _
(____ \ (_)                         (____ \ (_)
 _   \ \ _  ___  ____ _   _ _____    _   \ \ _  ___  ____ ___
| |   | | |/___)/ ___) | | (___  )  | |   | | |/___)/ ___) _ \
| |__/ /| |___ ( (___| |_| |/ __/   | |__/ /| |___ ( (__| |_| |
|_____/ |_(___/ \____)\____(_____)  |_____/ |_(___/ \____)___/ 2.3.210202

Usage:
  command [options] [arguments]

Options:
  -h, --help            Display this help message
  -q, --quiet           Do not output any message
  -V, --version         Display this application version
      --ansi            Force ANSI output
      --no-ansi         Disable ANSI output
  -n, --no-interaction  Do not ask any interactive question
  -v|vv|vvv, --verbose  Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for d                                              ebug

Available commands:
  help                         Displays help for a command
  list                         Lists commands
  migrate                      Run the database migrations
 clear
  clear:attachment             清理本地/COS未使用的附件
  clear:avatar                 清理本地/COS未使用的头像
  clear:question               返还过期未回答的问答金额
  clear:thread_draft           清理草稿箱中过期的主题
  clear:video                  清理未发布的主题视频
 db
  db:seed                      Seed the database with records
 finance
  finance:create               Count the financial situation of the previous day.
 invite
  invite:expire                未使用邀请码过期
 key
  key:generate                 生成站点唯一key，用于HASH
 make
  make:migration               Create a new migration file
  make:seeder                  Create a new seeder class
 migrate
  migrate:fresh                Drop all tables and re-run all migrations
  migrate:install              Create the migration repository
  migrate:refresh              Reset and re-run all migrations
  migrate:reset                Rollback all database migrations
  migrate:rollback             Rollback the last database migration
  migrate:status               Show the status of each migration
 order
  order:query                  Check whether the order has been paid
 queue
  queue:failed                 List all of the failed queue jobs
  queue:flush                  Flush all of the failed queue jobs
  queue:forget                 Delete a failed queue job
  queue:listen                 Listen to a given queue
  queue:retry                  Retry a failed queue job
  queue:work                   Start processing jobs on the queue as a daemon
 redPacket
  redPacket:expire             返还过期未回答的红包金额
 reward
  reward:expire                分配过期的剩余悬赏金额
 rsa
  rsa:gen                      生成 OAUTH2 private.key 和 public.key
 schedule
  schedule:run                 Run the scheduled commands
 site
  site:switch                  给设置表添加开关属性
 storage
  storage:link                 创建从“公共/存储”到“存储/应用/公共”的符号链接
 upgrade
  upgrade:avatar               更新用户头像信息
  upgrade:category-permission  初始化分类权限
  upgrade:groupPermissionAdd   追加内容付费场景用户组权限数据
  upgrade:notice               初始化/新增通知类型数据格式
  upgrade:notice-iteration     更新迭代通知数据
  upgrade:ordersExpiredAt      初始化付费注册订单的过期时间
  upgrade:postContent          初始化帖子内容，把原内容转为块编辑器的json数据。需要在迁移之前执行。
  upgrade:settingAdd           追加内容付费场景网站设置数据
  upgrade:split-permissions    Update category permissions.
  upgrade:videoSize            初始化转码成功的视频宽高、时长
```