# smallEstore
这是使用epoll的一个分支，写的很菜。
在Linux arm64上面开发的，不知道在其他架构上会不会有bug。
> 当前分支重构了整个模型  

**目前仍在开发当前项目的后端部分**
**通信协议-键值对数据(string_to_string)**
### Header：
| Field | Length | Type | Meaning |
|-|-|-|-|
| MagicNumber | 4 bytes | UInt32 | 魔数（固定为1234）|
| Size | 4 bytes | UInt32 | 包大小，不包括头部 |
| Type | 4 bytes | UInt32 | 包类型 |
| Padding | 4 bytes | UInt32 | 填充（固定为0）|

### Types:
| Number | Meaning |
|-|-|
| 0 | Put请求 |
| 1 | Delete请求 |
| 2 | Get请求 |
| 3 | Put响应 |
| 4 | Delete响应 |
| 5 | Get响应 |

### Put Request Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Key Size | 4 bytes | UInt32 | Key的长度 |
| Key | N bytes | Byte[] | Key |
| Value Size | 4 bytes | UInt32 | Value的长度 |
| Value | N bytes | Byte[] | Value |

### Delete Request Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Key Size | 4 bytes | UInt32 | Key的长度 |
| Key | N bytes | Byte[] | Key |

### Get Request Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Key Size | 4 bytes | UInt32 | Key的长度 |
| Key | N bytes | Byte[] | Key |

### Put Response Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Status | 1 byte | Bool | 是否成功 |

### Delete Response Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Status | 1 byte | Bool | 是否成功 |

### Get Response Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Value Size | 4 bytes | UInt32 | Value的长度 |
| Value | N bytes | Byte[] | Value |

**默认端口**:1434

**通信协议-用户数据(仍在计划中)**
###### Header：
| Field | Length | Type | Meaning |
|-|-|-|-|
| MagicNumber | 4 bytes | UInt32 | 魔数（固定为1710）|
| Size | 4 bytes | UInt32 | 包大小，不包括头部 |
| Type | 4 bytes | UInt32 | 包类型 |
| Padding | 4 bytes | UInt32 | 填充（固定为0）|
###### Types:
| Number | Meaning |
|-|-|
| 0 | Register请求 |
| 1 | Login请求 |
| 2 | Register响应 |
| 3 | Login响应 |
###### Register Request Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Username Size | 4 bytes | UInt32 | Username的长度 |
| Username | N bytes | Byte[] | Username |
| Password Size | 4 bytes | UInt32 | Password的长度 |
| Password | N bytes | Byte[] | Password |
###### Login Request Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Username Size | 4 bytes | UInt32 | Username的长度 |
| Username | N bytes | Byte[] | Username |
| Password Size | 4 bytes | UInt32 | Password的长度 |
| Password | N bytes | Byte[] | Password |
###### Register Response Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Status | 1 byte | Bool | 是否成功 |
###### Login Response Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Status | 1 byte | Bool | 是否成功 |

**通信协议-图片数据(仍在计划中)**
###### Header：
| Field | Length | Type | Meaning |
|-|-|-|-|
| MagicNumber | 4 bytes | UInt32 | 魔数（固定为1712）|
| Size | 4 bytes | UInt32 | 包大小，不包括头部 |
| Type | 4 bytes | UInt32 | 包类型 |
| Padding | 4 bytes | UInt32 | 填充（固定为0）|
###### Types:
| Number | Meaning |
|-|-|
| 0 | Upload请求 |
| 1 | Download请求 |
| 2 | Upload响应 |
| 3 | Download响应 |
###### Upload Request Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Image Size | 4 bytes | UInt32 | Image的长度 |
| Image | N bytes | Byte[] | Image |
###### Download Request Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Image Size | 4 bytes | UInt32 | Image的长度 |
| Image | N bytes | Byte[] | Image |
###### Upload Response Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Status | 1 byte | Bool | 是否成功 |
###### Download Response Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Status | 1 byte | Bool | 是否成功 |

**通信协议-商品数据(仍在计划中)**
###### Header：
| Field | Length | Type | Meaning |
|-|-|-|-|
| MagicNumber | 4 bytes | UInt32 | 魔数（固定为1714）|
| Size | 4 bytes | UInt32 | 包大小，不包括头部 |
| Type | 4 bytes | UInt32 | 包类型 |
| Padding | 4 bytes | UInt32 | 填充（固定为0）|
###### Types:
| Number | Meaning |
|-|-|
| 0 | Upload请求 |
| 1 | Download请求 |
| 2 | Upload响应 |
| 3 | Download响应 |
###### Upload Request Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Product Size | 4 bytes | UInt32 | Product的长度 |
| Product | N bytes | Byte[] | Product |
###### Download Request Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Product Size | 4 bytes | UInt32 | Product的长度 |
| Product | N bytes | Byte[] | Product |
###### Upload Response Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Status | 1 byte | Bool | 是否成功 |
###### Download Response Body:
| Field | Length | Type | Meaning |
|-|-|-|-|
| Status | 1 byte | Bool | 是否成功 |

*有待进一步开发*