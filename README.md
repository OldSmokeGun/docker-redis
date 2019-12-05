# `redis`

基于官方镜像构建的 `redis` 镜像

### 持久性存储

> 官方镜像默认当前工作目录为：`/data`

#### 使用命令开启持久性存储

```
$ docker run redis-server --appendonly yes
```

如果启用了持久性，则数据存储在 `/data` 中

#### 配置文件开启持久性存储

- 三个主要配置项
    - `appendonly yes|no`：是否开启 `aof`（持久化）
    - `appendfilename "appendonly.aof"`：`aof` 文件名称，存储的目录为 `dir` 配置项
    - `appendfsync always|everysec|no`：`aof` 备份策略
        - `always`：有命令写入立即写入磁盘
        - `everysec`：每秒实现文件的同步，写入磁盘
        - `no`：随机进行文件的同步，同步操作则交给操作系统来负责，通常时间是最长 `30s`
    - `dir ./`：文件存放目录，默认当前工作目录 `/data`