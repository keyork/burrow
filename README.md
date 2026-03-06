# burrow

基于 Golang 的 RabbitMQ 消息发送与查看工具

## 功能

- **发送消息**：向 RabbitMQ 队列发送 JSON 格式消息
- **查看消息**：实时监听并消费队列中的消息

## 环境要求

- Go 1.16+
- RabbitMQ Server

## 安装

```bash
go mod tidy
```

## 配置

默认连接配置：

- 地址：`localhost:5672`
- 用户名：`guest`
- 密码：`guest`
- 队列：`test-queue`（持久化）

如需修改，请编辑 `send.go` 和 `consume.go` 中的连接字符串。

## 使用方法

### 发送消息

```bash
go run send.go
```

发送的消息格式：

```json
[{
  "appName": "应用名",
  "timestamp": 1234567890123,
  "filename": "文件名.pdf"
}]
```

### 批量发送

```bash
./send_multi.sh
```

批量发送 20 条消息。

### 查看消息

```bash
go run consume.go
```

程序将持续监听队列并打印收到的消息。按 `CTRL+C` 退出。

## 依赖

- [github.com/rabbitmq/amqp091-go](https://github.com/rabbitmq/amqp091-go) - RabbitMQ Go 客户端库

## 许可证

MIT License
