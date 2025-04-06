---
{"type":"javascript","title":"数据类型转换与比较","tags":null,"author":"codertoro","establish":"2025-04-05","update":"2025-04-05","dg-publish":true,"permalink":"/Projects/JavaScript/JavaScript 类型转换和比较规则/","dgPassFrontmatter":true,"created":"2025-04-05T16:30:19.714+08:00","updated":"2025-04-05T16:32:12.346+08:00"}
---

# 1. **数据类型转换**

| 原始值             | 转为布尔值 | 转为数字 | 转为字符串 |
|--------------------|------------|----------|------------|
| `false`            | `false`    | `0`      | `"false"`  |
| `true`             | `true`     | `1`      | `"true"`   |
| `0`                | `false`    | `0`      | `"0"`      |
| `-0`               | `false`    | `-0`     | `"-0"`     |
| `NaN`              | `false`    | `NaN`    | `"NaN"`    |
| `""` (空字符串)    | `false`    | `0`      | `""`       |
| `"123"`            | `true`     | `123`    | `"123"`    |
| `"abc"`            | `true`     | `NaN`    | `"abc"`    |
| `null`             | `false`    | `0`      | `"null"`   |
| `undefined`        | `false`    | `NaN`    | `"undefined"` |
| `[]` (空数组)      | `true`     | `0`      | `""`       |
| `[123]`            | `true`     | `123`    | `"123"`    |
| `{}` (空对象)     | `true`     | `NaN`    | `"[object Object]"` |
| `function() {}`    | `true`     | `NaN`    | `"[object Function]"` |
| `Infinity`         | `true`     | `Infinity` | `"Infinity"` |

---

# 2. **相等性比较（`==`）**

| 左边值      | 右边值      | 结果（`==`） | 说明                                         |
|-------------|-------------|--------------|----------------------------------------------|
| `null`      | `undefined` | `true`       | 特例：`null` 和 `undefined` 相等              |
| `0`         | `false`     | `true`       | `false` 转换为 `0`，比较 `0 == 0`             |
| `""`        | `false`     | `true`       | `""` 转换为 `0`，`false` 转换为 `0`           |
| `"0"`       | `false`     | `true`       | `"0"` 转换为 `0`，`false` 转换为 `0`          |
| `[]`        | `false`     | `true`       | 空数组 `[]` 转换为 `0`，`false` 转换为 `0`    |
| `[]`        | `![]`       | `true`       | 空数组 `[]` 转换为 `false`，所以 `[] == false` |
| `[1]`       | `1`         | `true`       | `[1]` 转换为 `"1"`, `"1"` 转换为 `1`          |
| `{}`        | `[object Object]` | `false` | 对象与字符串不相等                             |
| `null`      | `false`     | `false`      | `null` 只与 `undefined` 相等                   |
| `undefined` | `false`     | `false`      | 同上                                         |

---

# 3. **真假值判断**

| 值               | 布尔值 |
|------------------|--------|
| `false`          | `false` |
| `0`              | `false` |
| `-0`             | `false` |
| `NaN`            | `false` |
| `""` (空字符串)  | `false` |
| `null`           | `false` |
| `undefined`      | `false` |
| `[]` (空数组)    | `true`  |
| `{}` (空对象)   | `true`  |
| `"0"`            | `true`  |
| `Infinity`       | `true`  |
| `function() {}`  | `true`  |

---

# 4. **特殊 JavaScript 行为**

| 表达式           | 结果      | 说明                                    |
|------------------|-----------|-----------------------------------------|
| `typeof null`    | `"object"`| JavaScript 的历史遗留问题              |
| `typeof NaN`     | `"number"`| `NaN` 被认为是数字，尽管它表示“非数字” |
| `NaN === NaN`    | `false`   | `NaN` 是唯一不等于自身的值             |
| `{} + []`        | `"[object Object]"` | 对象字面量会被解析为代码块           |
| `[] + {}`        | `"[object Object]"` | 数组和对象转换为字符串时的行为       |

---

### 📋 小结：

这张表概括了 **JavaScript 类型转换、相等性比较、真假值判断** 和一些 **特殊行为**，可以帮助你更快速地理解和使用这些特性。

- **类型转换**：展示了常见值转为布尔值、数字和字符串时的结果。
- **相等比较**：阐明了 `==` 操作符隐式转换的规则。
- **真假值判断**：列出了 JavaScript 中的假值和真值。
- **特殊行为**：解释了 JavaScript 中的历史遗留问题和奇怪的行为。

---

这样你可以在需要的时候快速回顾这些规则，编写更符合 JavaScript 行为的代码。📚 有其他问题或希望进一步深入某一部分，随时告诉我！
