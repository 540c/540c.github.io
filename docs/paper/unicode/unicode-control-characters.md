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

| 码点     | 名称                      | 用途 |
| -------- | ------------------------- | ---- |
| `U+2000` | EN QUAD                   |      |
| `U+2001` | EM QUAD                   |      |
| `U+2002` | EN SPACE                  |      |
| `U+2003` | EM SPACE                  |      |
| `U+2004` | THREE-PER-EM SPACE        |      |
| `U+2005` | FOUR-PER-EM SPACE         |      |
| `U+2006` | SIX-PER-EM SPACE          |      |
| `U+2007` | FIGURE SPACE              |      |
| `U+2008` | PUNCTUATION SPACE         |      |
| `U+2009` | THIN SPACE                |      |
| `U+200A` | HAIR SPACE                |      |
| `U+202F` | NARROW NO-BREAK SPACE     |      |
| `U+205F` | MEDIUM MATHEMATICAL SPACE |      |

### 格式符 Format characters

| 码点     | 名称                       | 用途 |
| -------- | -------------------------- | ---- |
| `U+00A0` | NO-BREAK SPACE             |      |
| `U+061C` | ARABIC LETTER MARK         |      |
| `U+200B` | ZERO WIDTH SPACE           |      |
| `U+200C` | ZERO WIDTH NON-JOINER      |      |
| `U+200D` | ZERO WIDTH JOINER          |      |
| `U+200E` | LEFT-TO-RIGHT MARK         |      |
| `U+200F` | RIGHT-TO-LEFT MARK         |      |
| `U+202A` | LEFT-TO-RIGHT EMBEDDING    |      |
| `U+202B` | RIGHT-TO-LEFT EMBEDDING    |      |
| `U+202C` | POP DIRECTIONAL FORMATTING |      |
| `U+202D` | LEFT-TO-RIGHT OVERRIDE     |      |
| `U+202E` | RIGHT-TO-LEFT OVERRIDE     |      |
| `U+2060` | WORD JOINER                |      |
| `U+2066` | LEFT-TO-RIGHT ISOLATE      |      |
| `U+2067` | RIGHT-TO-LEFT ISOLATE      |      |
| `U+2068` | FIRST STRONG ISOLATE       |      |
| `U+2069` | POP DIRECTIONAL ISOLATE    |      |
| `U+FEFF` | ZERO WIDTH NO-BREAK SPACE  |      |

### 分隔符 Separators

| 码点     | 名称                | 用途 |
| -------- | ------------------- | ---- |
| `U+2028` | LINE SEPARATOR      |      |
| `U+2029` | PARAGRAPH SEPARATOR |      |

### 隐藏运算符 Invisible operators

| 码点     | 名称                 | 用途 |
| -------- | -------------------- | ---- |
| `U+2061` | FUNCTION APPLICATION |      |
| `U+2062` | INVISIBLE TIMES      |      |
| `U+2063` | INVISIBLE SEPARATOR  |      |
| `U+2064` | INVISIBLE PLUS       |      |

## 变体选择符 Variation Selector

**VS1-VS16**被定义在基本区（BMP），码位范围为U+FE00-U+FE0F，被称为通用变体选择符（General-use Variation Selectors）

**VS17-VS256**被定义在第14平面，即特别用途补充平面（Supplementary Special-purpose Plane，SSP），码位范围为U+E0100-U+E01EF，仅可用于表意文字变体序列（IVS）。

| 码点     | 名称                 | 用途 |
| -------- | -------------------- | ---- |
| `U+FE00` | VARIATION SELECTOR-1 |      |
| `U+FE01` | VARIATION SELECTOR-2 |      |
| `U+FE02` | VARIATION SELECTOR-3 |      |
| `U+FE03` | VARIATION SELECTOR-4 |      |
| `U+FE04` | VARIATION SELECTOR-5 |      |
| `U+FE05` | VARIATION SELECTOR-6 |      |
| `U+FE06` | VARIATION SELECTOR-7 |      |
| `U+FE07` | VARIATION SELECTOR-8 |      |
| `U+FE08` | VARIATION SELECTOR-9 |      |
| `U+FE09` | VARIATION SELECTOR-10 |      |
| `U+FE0A` | VARIATION SELECTOR-11 |      |
| `U+FE0B` | VARIATION SELECTOR-12 |      |
| `U+FE0C` | VARIATION SELECTOR-13 |      |
| `U+FE0D` | VARIATION SELECTOR-14 |      |
| `U+FE0E` | VARIATION SELECTOR-15 |      |
| `U+FE0F` | VARIATION SELECTOR-16 |      |


## 控制图片 Control Pictures

