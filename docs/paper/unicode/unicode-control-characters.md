# Unicode 控制字符

## 前言

由于 Unicode 控制字符承担了一些本因由排版解决的职责，反而带来了一些「所见非所得」的视觉安全问题……

## ISO 6429控制字符C0与C1

### C0 controls

控制字符 U+0000..U+001F 和 U+007F 来自ASCII码兼容而来。

### C1 controls

ISO 8859 中又定义了 U+0080..U+009F。

## 行间标注

3个格式化字符用于支持旁注标记（U+FFF9、U+FFFA、U+FFFB）。

## 双向文本控制

Unicode支持从左到右、从右到左，或者其混合排版，而不需要任何特殊字符。但为了处理一些特殊情形，Unicode定义了12个字符（U+061C、U+200E、U+200F、U+202A、U+202B、U+202C、U+202D、U+202E、U+2066、U+2067、U+2068、U+2069）以帮助控制嵌入式双向文本最大125层深。

### 空格 Spaces

| 码点     | 名称 | 用途 |
| -------- | ---- | ---- |
| `U+2000` |      |      |
| `U+2001` |      |      |
| `U+2002` |      |      |
| `U+2003` |      |      |
| `U+2004` |      |      |
| `U+2005` |      |      |
| `U+2006` |      |      |
| `U+2007` |      |      |
| `U+2008` |      |      |
| `U+2009` |      |      |
| `U+200A` |      |      |
| `U+202F` |      |      |
| `U+205F` |      |      |

### 格式符 Format characters

| 码点     | 名称                       | 用途 |
| -------- | -------------------------- | ---- |
| `U+200B` | Zero Width Space           |      |
| `U+200C` | Zero Width Non-Joiner      |      |
| `U+200D` | Zero Width Joiner          |      |
| `U+200E` | Left-To-Right Mark         |      |
| `U+200F` | Right-To-Left Mark         |      |
| `U+202A` | Left-To-Right Embedding    |      |
| `U+202B` | Right-To-Left Embedding    |      |
| `U+202C` | Pop Directional Formatting |      |
| `U+202D` | Left-To-Right Override     |      |
| `U+202E` | Right-To-Left Override     |      |
| `U+2060` | Word Joiner Unicode        |      |
| `U+2066` | Left-To-Right Isolate      |      |
| `U+2067` | Right-To-Left Isolate      |      |
| `U+2068` | First Strong Isolate       |      |
| `U+2069` | Pop Directional Isolate    |      |

### 分隔符 Separators

| 码点     | 名称 | 用途 |
| -------- | ---- | ---- |
| `U+2028` |      |      |
| `U+2029` |      |      |

### 隐藏运算符 Invisible operators

| 码点     | 名称 | 用途 |
| -------- | ---- | ---- |
| `U+2061` |      |      |
| `U+2062` |      |      |
| `U+2063` |      |      |
| `U+2064` |      |      |
| `U+2065` |      |      |

## 通用变体选择符

## 控制图片 Control Pictures

