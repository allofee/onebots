# 标准动作

## `get_self_info` 获取机器人自身信息

### 请求参数

无。

### 响应数据

| 字段名                | 数据类型   | 默认值 | 说明                    |
|--------------------|--------|-----|-----------------------|
| `user_id`          | string | -   | 机器人用户 ID              |
| `user_name`        | string | -   | 机器人名称/姓名/昵称           |
| `user_displayname` | string | -   | 机器人账号设置的显示名称，若无则为空字符串 |

### 请求示例

```json
{
  "action": "get_self_info",
  "params": {}
}
```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": {
    "user_id": "123456",
    "user_name": "我是大笨蛋",
    "user_displayname": ""
  },
  "message": ""
}
```

## `get_user_info` 获取用户信息

### 请求参数

| 字段名       | 数据类型   | 默认值 | 说明                  |
|-----------|--------|-----|---------------------|
| `user_id` | string | -   | 用户 ID，可以是好友，也可以是陌生人 |

### 响应数据

| 字段名                | 数据类型   | 默认值 | 说明                      |
|--------------------|--------|-----|-------------------------|
| `user_id`          | string | -   | 用户 ID                   |
| `user_name`        | string | -   | 用户名称/姓名/昵称              |
| `user_displayname` | string | -   | 用户设置的显示名称，若无则为空字符串      |
| `user_remark`      | string | -   | 机器人账号对该用户的备注名称，若无则为空字符串 |

### 请求示例

```json
{
  "action": "get_user_info",
  "params": {
    "user_id": "123456"
  }
}
```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": {
    "user_id": "123456",
    "user_name": "我是大笨蛋",
    "user_displayname": "",
    "user_remark": "一个自称大笨蛋的人"
  },
  "message": ""
}
```

## `get_friend_list` 获取好友列表

获取机器人的关注者或好友列表。

### 请求参数

无请求参数。

### 响应数据

好友信息列表，数据类型为 ``list[resp[`get_user_info`]]``。

### 请求示例

```json
{
  "action": "get_friend_list",
  "params": {}
}
```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": [
    {
      "user_id": "123456",
      "user_name": "我是大笨蛋",
      "user_displayname": "",
      "user_remark": "一个自称大笨蛋的人"
    },
    {
      "user_id": "654321",
      "user_name": "我是小笨蛋",
      "user_displayname": "",
      "user_remark": "一个自称小笨蛋的人"
    }
  ],
  "message": ""
}
```

## `get_group_info` 获取群信息

### 请求参数

| 字段名        | 数据类型   | 默认值 | 说明   |
|------------|--------|-----|------|
| `group_id` | string | -   | 群 ID |

### 响应数据

| 字段名          | 数据类型   | 默认值 | 说明   |
|--------------|--------|-----|------|
| `group_id`   | string | -   | 群 ID |
| `group_name` | string | -   | 群名称  |

### 请求示例

```json
{
  "action": "get_group_info",
  "params": {
    "group_id": "123456"
  }
}
```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": {
    "group_id": "123456",
    "group_name": "一群大笨蛋"
  },
  "message": ""
}
```

## `get_group_list` 获取群列表

获取机器人加入的群列表。

### 请求参数

无。

### 响应数据

群信息列表，数据类型为 ``list[resp[`get_group_info`]]``。

### 请求示例

```json
{
  "action": "get_group_list",
  "params": {}
}
```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": [
    {
      "group_id": "123456",
      "group_name": "一群大笨蛋"
    },
    {
      "group_id": "654321",
      "group_name": "一群大笨蛋2群"
    }
  ],
  "message": ""
}
```

## `get_group_member_info` 获取群成员信息

### 请求参数

| 字段名        | 数据类型   | 默认值 | 说明    |
|------------|--------|-----|-------|
| `group_id` | string | -   | 群 ID  |
| `user_id`  | string | -   | 用户 ID |

### 响应数据

| 字段名                | 数据类型   | 默认值 | 说明                          |
|--------------------|--------|-----|-----------------------------|
| `user_id`          | string | -   | 用户 ID                       |
| `user_name`        | string | -   | 用户名称/姓名/昵称                  |
| `user_displayname` | string | -   | 用户设置的群内显示名称或账号显示名称，若无则为空字符串 |

### 请求示例

```json
{
  "action": "get_group_member_info",
  "params": {
    "group_id": "123456",
    "user_id": "3847573"
  }
}
```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": {
    "user_id": "3847573",
    "user_name": "我是大笨蛋",
    "user_displayname": "本群最菜的"
  },
  "message": ""
}
```

## `get_group_member_list` 获取群成员列表

### 请求参数

| 字段名        | 数据类型   | 默认值 | 说明   |
|------------|--------|-----|------|
| `group_id` | string | -   | 群 ID |

### 响应数据

群成员信息列表，数据类型为 ``list[resp[`get_group_member_info`]]``。

### 请求示例

```json
{
  "action": "get_group_member_list",
  "params": {
    "group_id": "123456"
  }
}
```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": [
    {
      "user_id": "111222333",
      "user_name": "我是大笨蛋",
      "user_displayname": "本群最菜的"
    },
    {
      "user_id": "444555666",
      "user_name": "我是小笨蛋",
      "user_displayname": "本群最强的"
    }
  ],
  "message": ""
}
```

## `set_group_name` 设置群名称

### 请求参数

| 字段名          | 数据类型   | 默认值 | 说明   |
|--------------|--------|-----|------|
| `group_id`   | string | -   | 群 ID |
| `group_name` | string | -   | 新群名称 |

### 响应数据

无。

### 请求示例

```json
{
  "action": "set_group_name",
  "params": {
    "group_id": "2452352435",
    "group_name": "一个非常普通的群名"
  }
}
```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": null,
  "message": ""
}
```

## `leave_group` 退出群

### 请求参数

| 字段名        | 数据类型   | 默认值 | 说明   |
|------------|--------|-----|------|
| `group_id` | string | -   | 群 ID |

### 响应数据

无。

### 请求示例

```json
{
  "action": "leave_group",
  "params": {
    "group_id": "2452352435"
  }
}
```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": null,
  "message": ""
}
```

## `get_guild_info` 获取群组信息

### 请求参数

| 字段名        | 数据类型   | 默认值 | 说明    |
|------------|--------|-----|-------|
| `guild_id` | string | -   | 群组 ID |

### 响应数据

| 字段名          | 数据类型   | 默认值 | 说明    |
|--------------|--------|-----|-------|
| `guild_id`   | string | -   | 群组 ID |
| `guild_name` | string | -   | 群组名称  |

### 请求示例

```json
{
  "action": "get_guild_info",
  "params": {
    "guild_id": "123456"
  }
}
```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": {
    "guild_id": "12345",
    "guild_name": "一群大笨蛋"
  },
  "message": ""
}
   ```

## `get_guild_list` 获取群组列表

获取机器人加入的群组列表。

### 请求参数

无。

### 响应数据

群组信息列表，数据类型为 ``list[resp[`get_guild_info`]]``。

### 请求示例

```json
{
  "action": "get_guild_list",
  "params": {}
}
   ```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": [
    {
      "guild_id": "12345",
      "guild_name": "一群大笨蛋"
    },
    {
      "guild_id": "54321",
      "guild_name": "一群大笨蛋2群"
    }
  ],
  "message": ""
}
   ```

## `set_guild_name` 设置群组名称

### 请求参数

| 字段名          | 数据类型   | 默认值 | 说明    |
|--------------|--------|-----|-------|
| `guild_id`   | string | -   | 群组 ID |
| `guild_name` | string | -   | 新群组名称 |

### 响应数据

无。

### 请求示例

```json
{
  "action": "set_guild_name",
  "params": {
    "guild_id": "12345",
    "guild_name": "一个非常普通的群名"
  }
}
   ```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": null,
  "message": ""
}
   ```

## `get_guild_member_info` 获取群组成员信息

### 请求参数

| 字段名        | 数据类型   | 默认值 | 说明    |
|------------|--------|-----|-------|
| `guild_id` | string | -   | 群组 ID |
| `user_id`  | string | -   | 用户 ID |

### 响应数据

| 字段名                | 数据类型   | 默认值 | 说明                           |
|--------------------|--------|-----|------------------------------|
| `user_id`          | string | -   | 用户 ID                        |
| `user_name`        | string | -   | 用户名称/姓名/昵称                   |
| `user_displayname` | string | -   | 用户设置的群组内显示名称或账号显示名称，若无则为空字符串 |

### 请求示例

```json
{
  "action": "get_guild_member_info",
  "params": {
    "guild_id": "12345",
    "user_id": "3847573"
  }
}
   ```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": {
    "user_id": "3847573",
    "user_name": "我是大笨蛋",
    "user_displayname": "本群最菜的"
  },
  "message": ""
}
   ```

## `get_guild_member_list` 获取群组成员列表

### 请求参数

| 字段名        | 数据类型   | 默认值 | 说明    |
|------------|--------|-----|-------|
| `guild_id` | string | -   | 群组 ID |

### 响应数据

群组成员信息列表，数据类型为 ``list[resp[`get_guild_member_info`]]``。

### 请求示例

```json
{
  "action": "get_guild_member_list",
  "params": {
    "guild_id": "123456"
  }
}
   ```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": [
    {
      "user_id": "111222333",
      "user_name": "我是大笨蛋",
      "user_displayname": "本群最菜的"
    },
    {
      "user_id": "444555666",
      "user_name": "我是小笨蛋",
      "user_displayname": "本群最强的"
    }
  ],
  "message": ""
}
   ```

## `leave_guild` 退出群组

### 请求参数

| 字段名        | 数据类型   | 默认值 | 说明    |
|------------|--------|-----|-------|
| `guild_id` | string | -   | 群组 ID |

### 响应数据

无。

### 请求示例

```json
{
  "action": "leave_guild",
  "params": {
    "guild_id": "12345"
  }
}
   ```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": null,
  "message": ""
}
   ```

## `get_channel_info` 获取频道信息

### 请求参数

| 字段名          | 数据类型   | 默认值 | 说明    |
|--------------|--------|-----|-------|
| `guild_id`   | string | -   | 群组 ID |
| `channel_id` | string | -   | 频道 ID |

### 响应数据

| 字段名            | 数据类型   | 默认值 | 说明    |
|----------------|--------|-----|-------|
| `channel_id`   | string | -   | 频道 ID |
| `channel_name` | string | -   | 频道名称  |

### 请求示例

```json
{
  "action": "get_channel_info",
  "params": {
    "guild_id": "123456",
    "channel_id": "12"
  }
}
   ```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": {
    "channel_id": "12",
    "channel_name": "笨蛋频道"
  },
  "message": ""
}
   ```

## `get_channel_list` 获取频道列表

获取指定群组中机器人可见的频道列表。

### 请求参数

| 字段名           | 数据类型   | 默认值     | 说明               |
|---------------|--------|---------|------------------|
| `guild_id`    | string | -       | 群组 ID            |
| `joined_only` | bool   | `false` | 只获取机器人账号已加入的频道列表 |

### 响应数据

频道信息列表，数据类型为 ``list[resp[`get_channel_info`]]``。

### 请求示例

```json
{
  "action": "get_channel_list",
  "params": {
    "guild_id": "12345"
  }
}
   ```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": [
    {
      "channel_id": "12",
      "channel_name": "笨蛋频道"
    },
    {
      "channel_id": "13",
      "channel_name": "聪明频道"
    }
  ],
  "message": ""
}
   ```

## `set_channel_name` 设置频道名称

### 请求参数

| 字段名            | 数据类型   | 默认值 | 说明    |
|----------------|--------|-----|-------|
| `guild_id`     | string | -   | 群组 ID |
| `channel_id`   | string | -   | 频道 ID |
| `channel_name` | string | -   | 新频道名称 |

### 响应数据

无。

### 请求示例

```json
{
  "action": "set_channel_name",
  "params": {
    "guild_id": "12345",
    "channel_id": "13",
    "channel_name": "笨蛋频道2"
  }
}
   ```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": null,
  "message": ""
}
   ```

## `get_channel_member_info` 获取频道成员信息

### 请求参数

| 字段名          | 数据类型   | 默认值 | 说明    |
|--------------|--------|-----|-------|
| `guild_id`   | string | -   | 群组 ID |
| `channel_id` | string | -   | 频道 ID |
| `user_id`    | string | -   | 用户 ID |

### 响应数据

| 字段名                | 数据类型   | 默认值 | 说明                           |
|--------------------|--------|-----|------------------------------|
| `user_id`          | string | -   | 用户 ID                        |
| `user_name`        | string | -   | 用户名称/姓名/昵称                   |
| `user_displayname` | string | -   | 用户设置的频道内显示名称或账号显示名称，若无则为空字符串 |

### 请求示例

```json
{
  "action": "get_channel_member_info",
  "params": {
    "guild_id": "12345",
    "channel_id": "12",
    "user_id": "3847573"
  }
}
   ```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": {
    "user_id": "3847573",
    "user_name": "我是大笨蛋",
    "user_displayname": "本群最菜的"
  },
  "message": ""
}
   ```

## `get_channel_member_list` 获取频道成员列表

### 请求参数

| 字段名          | 数据类型   | 默认值 | 说明    |
|--------------|--------|-----|-------|
| `guild_id`   | string | -   | 群组 ID |
| `channel_id` | string | -   | 频道 ID |

### 响应数据

频道成员信息列表，数据类型为 ``list[resp[`get_channel_member_info`]]``。

### 请求示例

```json
{
  "action": "get_channel_member_list",
  "params": {
    "guild_id": "123456",
    "channel_id": "12"
  }
}
   ```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": [
    {
      "user_id": "111222333",
      "user_name": "我是大笨蛋",
      "user_displayname": "本群最菜的"
    },
    {
      "user_id": "444555666",
      "user_name": "我是小笨蛋",
      "user_displayname": "本群最强的"
    }
  ],
  "message": ""
}
   ```

## `leave_channel` 退出频道

### 请求参数

| 字段名          | 数据类型   | 默认值 | 说明    |
|--------------|--------|-----|-------|
| `guild_id`   | string | -   | 群组 ID |
| `channel_id` | string | -   | 频道 ID |

### 响应数据

无。

### 请求示例

```json
{
  "action": "leave_channel",
  "params": {
  "guild_id": "12345",
  "channel_id": "12"
  }
}
   ```

### 响应示例

```json
{
  "status": "ok",
  "retcode": 0,
  "data": null,
  "message": ""
}
   ```

# 扩展动作