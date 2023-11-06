# 函数速查表

### 简介

该章节提供了函数速查表，你可以在这里快速搜索所有的可用函数以及他们的基础使用方法

### 数值函数

此章节提供了常见的数值处理函数，包括数学运算、统计计算等。

| 函数名称      | 描述                                                             | 输入                        | 输出     | 示例                                                                                     |
| --------- | -------------------------------------------------------------- | ------------------------- | ------ | -------------------------------------------------------------------------------------- |
| SUM       | 将数字加在一起。相当于 number1 + number2 + ...                            | `number1, [number2, ...]` | Number | `SUM(100, 200, 300) => 600`                                                            |
| AVERAGE   | 返回数字的平均值。                                                      | `number1, [number2, ...]` | Number | `AVERAGE(100, 200, 300) => 200`                                                        |
| MAX       | 返回给定数字中的最大值。                                                   | `number1, [number2, ...]` | Number | `MAX(100, 200, 300) => 300`                                                            |
| MIN       | 返回给定数字中的最小值。                                                   | `number1, [number2, ...]` | Number | `MIN(100, 200, 300) => 100`                                                            |
| ROUND     | 根据 "precision" 给出的小数位数四舍五入该值。                                  | `value, [precision]`      | Number | <p><code>ROUND(1.99, 0) => 2</code></p><p><code>ROUND(16.8, -1) => 20</code></p>       |
| ROUNDUP   | 总是向上四舍五入，即远离零。                                                 | `value, [precision]`      | Number | <p><code>ROUNDUP(1.1, 0) => 2</code></p><p><code>ROUNDUP(-1.1, 0) => -2</code></p>     |
| ROUNDDOWN | 总是向下四舍五入，即朝向零。                                                 | `value, [precision]`      | Number | <p><code>ROUNDDOWN(1.9, 0) => 1</code></p><p><code>ROUNDDOWN(-1.9, 0) => -1</code></p> |
| CEILING   | 返回大于或等于该值的最接近的整数倍数。                                            | `value, [significance]`   | Number | <p><code>CEILING(2.49) => 3</code></p><p><code>CEILING(2.49, 1) => 2.5</code></p>      |
| FLOOR     | 返回小于或等于该值的最接近的整数倍数。                                            | `value, [significance]`   | Number | <p><code>FLOOR(2.49) => 2</code></p><p><code>FLOOR(2.49, 1) => 2.4</code></p>          |
| EVEN      | 返回大于或等于指定值的最小偶数。                                               | `value`                   | Number | <p><code>EVEN(0.1) => 2</code></p><p><code>EVEN(-0.1) => -2</code></p>                 |
| ODD       | 将正值四舍五入到最接近的奇数，将负值四舍五入到最接近的奇数。                                 | `value`                   | Number | <p><code>ODD(0.1) => 1</code></p><p><code>ODD(-0.1) => -1</code></p>                   |
| INT       | 返回逻辑参数为真时的number1，否则返回number2。也可用于制作嵌套IF语句。也可用于检查单元格是否为空/是否为空。 | `value`                   | Number | <p><code>INT(1.9) => 1</code></p><p><code>INT(-1.9) => -2</code></p>                   |
| ABS       | 返回绝对值。                                                         | `value`                   | Number | `ABS(-1) => 1`                                                                         |
| SQRT      | 返回非负数的平方根。                                                     | `value`                   | Number | `SQRT(4) => 2`                                                                         |
| POWER     | 计算指定的基数到指定的功率。                                                 | `value`                   | Number | `POWER(2) => 4`                                                                        |
| EXP       | 计算Euler数（e）到指定的功率。                                             | `value`                   | Number | <p><code>EXP(0) => 1</code></p><p><code>EXP(1) => 2.718</code></p>                     |
| LOG       | 在提供的基数中计算值的对数。如果未指定，基数默认为10。                                   | `value, [base=10]`        | Number | <p><code>LOG(100) => 2</code></p><p><code>LOG(1024, 2) => 10</code></p>                |
| MOD       | 返回将第一个参数除以第二个后的余数。                                             | `value, divisor`          | Number | <p><code>MOD(9, 2) => 1</code></p><p><code>MOD(9, 3) => 0</code></p>                   |
| VALUE     | 将文本字符串转换为数字。                                                   | `text`                    | Number | `VALUE("$1,000,000") => 1000000`                                                       |



### 文本函数

在这里，您会找到有关文本处理的常用函数，如字符串操作、格式化等。

| 函数名称                   | 描述                                                           | 输入                                                 | 输出            | 示例                                                                          |
| ---------------------- | ------------------------------------------------------------ | -------------------------------------------------- | ------------- | --------------------------------------------------------------------------- |
| CONCATENATE            | 连接多种值类型参数为单一文本值。                                             | `text1, [text2, ...]`                              | Text          | `CONCATENATE("Hello ", "Teable") => Hello Teable`                           |
| FIND                   | 在指定文本中查找子字符串的位置。如果未找到子字符串，则结果为 0。                            | `stringToFind, whereToSearch, [startFromPosition]` | Number        | `FIND("Teable", "Hello Teable") => 7`                                       |
| SEARCH                 | 在指定文本中查找子字符串的位置。如果未找到子字符串，则结果为空。与FIND函数类似，但当未找到子字符串时FIND返回0。 | `stringToFind, whereToSearch, [startFromPosition]` | Text or Empty | `SEARCH("Teable", "Hello Teable") => 7`                                     |
| MID                    | 提取从指定位置开始的指定数量的子字符串。                                         | `text, whereToStart, count`                        | Text          | `MID("Hello Teable", 6, 6) => "Teable"`                                     |
| LEFT                   | 提取字符串开始的指定数量的字符。                                             | `text, count`                                      | Text          | `LEFT("2023-09-06", 4) => "2023"`                                           |
| RIGHT                  | 提取字符串结束的指定数量的字符。                                             | `text, count`                                      | Text          | `RIGHT("2023-09-06", 5) => "09-06"`                                         |
| REPLACE                | 用替换文本替换从开始字符开始的指定数量的字符。                                      | `text, whereToStart, count, replacement`           | Text          | `REPLACE("Hello Table", 7, 5, "Teable") => "Hello Teable"`                  |
| REGEXP\_REPLACE        | 使用替换文本替换匹配正则表达式的所有子字符串。                                      | `text, regular_expression, replacement`            | Text          | `REGEXP_REPLACE("Hello Table", "H.* ", "") => "Teable"`                     |
| SUBSTITUTE             | 用新文本替换旧文本。可以指定索引号来替换旧文本的特定出现。如果未指定索引号，则将替换旧文本的所有出现。          | `text, oldText, newText, [index]`                  | Text          | `SUBSTITUTE("Hello Table", "Table", "Teable") => "Hello Teable"`            |
| LOWER                  | 将字符串转为小写。                                                    | `text`                                             | Text          | `LOWER("Hello Teable") => "hello teable"`                                   |
| UPPER                  | 将字符串转为大写。                                                    | `text`                                             | Text          | `UPPER("Hello Teable") => "HELLO TEABLE"`                                   |
| REPT                   | 将字符串重复指定的次数。                                                 | `text, number`                                     | Text          | `REPT("Hello!") => "Hello!Hello!Hello!"`                                    |
| TRIM                   | 去除字符串开始和结束的空白字符。                                             | `text`                                             | Text          | `TRIM(" Hello ") => "Hello"`                                                |
| LEN                    | 计算字符串的字符数。                                                   | `text`                                             | Number        | `LEN("Hello") => 5`                                                         |
| T                      | 如果参数是文本，则返回该参数，否则返回空。                                        | `value`                                            | Text or Empty | <p><code>T("Hello") => "Hello"</code></p><p><code>T(100) => null</code></p> |
| ENCODE\_URL\_COMPONENT | 为构造URL或URI替换某些字符为编码等效项。不会编码以下字符：- \_ . \~                    | `value`                                            | Text          | `ENCODE_URL_COMPONENT("Hello Teable") => "Hello%20Teable"`                  |



### 逻辑函数

逻辑函数主要涉及条件判断和逻辑运算。本章节将详细介绍如`IF`, `AND`, `OR`等函数的使用。

| 函数名称      | 描述                                                                                         | 输入                                            | 输出                                      | 示例                                                                                                                                |
| --------- | ------------------------------------------------------------------------------------------ | --------------------------------------------- | --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| IF        | 如果逻辑参数为真，则返回`value1`，否则返回`value2`。还可用于制作嵌套的IF语句，以及检查单元格是否为空。                               | `logical, value1, value2`                     | String \| Number \| Boolean \| Datetime | <p><code>IF(2 > 1, "A", "B") => "A"</code><br><code>IF(2 > 1, TRUE, FALSE) => TRUE</code></p>                                     |
| SWITCH    | 根据输入的表达式，从一系列可能的值中匹配，并返回相对应的结果。如果输入的表达式与定义的模式都不匹配，则可以返回一个默认值。在许多情况下，SWITCH()可以代替嵌套的IF()公式。 | `expression, [pattern, result]..., [default]` | String \| Number \| Boolean \| Datetime | `SWITCH("B", "A", "Value A", "B", "Value B", "Default Value") => "Value B"`                                                       |
| AND       | 如果所有参数都为真，则返回真；否则返回假。                                                                      | `logical1, [logical2, ...]`                   | Boolean                                 | <p><code>AND(1 &#x3C; 2, 5 > 3) => true</code><br><code>AND(1 &#x3C; 2, 5 &#x3C; 3) => false</code></p>                           |
| OR        | 如果任意一个参数为真，则返回真。                                                                           | `logical1, [logical2, ...]`                   | Boolean                                 | <p><code>OR(1 &#x3C; 2, 5 &#x3C; 3) => true</code><br><code>OR(1 > 2, 5 &#x3C; 3) => false</code></p>                             |
| XOR       | 如果有奇数个参数为真，则返回真。                                                                           | `logical1, [logical2, ...]`                   | Boolean                                 | <p><code>XOR(1 &#x3C; 2, 5 &#x3C; 3, 8 &#x3C; 10) => false</code><br><code>XOR(1 > 2, 5 &#x3C; 3, 8 &#x3C; 10) => true</code></p> |
| NOT       | 反转其参数的逻辑值。                                                                                 | `boolean`                                     | Boolean                                 | <p><code>NOT(1 &#x3C; 2) => false</code><br><code>NOT(1 > 2) => true</code></p>                                                   |
| BLANK     | 返回一个空值。                                                                                    | `-`                                           | null                                    | <p><code>BLANK() => null</code><br><code>IF(2 > 3, "Yes", BLANK()) => null</code></p>                                             |
| ERROR     | 返回一个错误值。                                                                                   | `message`                                     | Error                                   | `IF(2 > 3, "Yes", ERROR("Calculation")) => "#ERROR: Calculation"`                                                                 |
| IS\_ERROR | 如果表达式引起错误，则返回真。                                                                            | `expr`                                        | Boolean                                 | `IS_ERROR(ERROR()) => true`                                                                                                       |



### 日期函数

日期函数帮助用户处理和转换日期和时间数据。此部分涵盖了日期的增加、减少、格式化等操作。

| 函数名称           | 描述                                                     | 输入                           | 输出       | 示例                                                                                                                                         |
| -------------- | ------------------------------------------------------ | ---------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| TODAY          | 返回当前日期。                                                | `-`                          | Datetime | `TODAY() => "2023-09-08 00:00"`                                                                                                            |
| NOW            | 返回当前的日期和时间。                                            | `-`                          | Datetime | `NOW() => "2023-09-08 16:50"`                                                                                                              |
| YEAR           | 返回日期的四位数字年份。                                           | `date`                       | Number   | `YEAR("2023-09-08") => 2023`                                                                                                               |
| MONTH          | 返回日期的月份，作为1（1月）到12（12月）之间的数字。                          | `date`                       | Number   | `MONTH("2023-09-08") => 9`                                                                                                                 |
| WEEKNUM        | 返回年份中的周数。                                              | `date`                       | Number   | `WEEKNUM("2023-09-08") => 36`                                                                                                              |
| WEEKDAY        | 返回周中的天数作为0到6之间的整数。您可以选择性地提供第二个参数（“星期日”或“星期一”）以在该天开始一周。 | `date, [startDayOfWeek]`     | Number   | `WEEKDAY("2023-09-08", "Monday") => 5`                                                                                                     |
| DAY            | 返回日期的月份中的日期，作为1-31之间的数字。                               | `date`                       | Number   | `DAY("2023-09-08") => 8`                                                                                                                   |
| HOUR           | 返回日期的小时数，作为0（12:00am）到23（11:00pm）之间的数字。                | `date`                       | Number   | `HOUR("2023-09-08 16:50") => 16`                                                                                                           |
| MINUTE         | 返回日期的分钟，作为0到59之间的整数。                                   | `date`                       | Number   | `MINUTE("2023-09-08 16:50") => 50`                                                                                                         |
| SECOND         | 返回日期的秒数，作为0到59之间的整数。                                   | `date`                       | Number   | `SECOND("2023-09-08 16:50:30") => 30`                                                                                                      |
| FROMNOW        | 计算当前日期与另一个日期之间的天数。                                     | `date, unit`                 | Number   | `FROMNOW({Date}, "day") => 25`                                                                                                             |
| TONOW          | 计算当前日期与另一个日期之间的天数。                                     | `date, unit`                 | Number   | `TONOW({Date}, "day") => 25`                                                                                                               |
| DATETIME\_DIFF | 返回指定单位的日期时间差异。默认单位是秒。(请参阅单位说明符列表。)                     | `date1, date2, [unit]`       | Number   | `DATETIME_DIFF("2022-08-01", "2023-09-08", "day") => 403`                                                                                  |
| WORKDAY        | 返回到开始日期的工作日，不包括指定的假期                                   | `date, count, [holidayStr]`  | Datetime | `WORKDAY("2023-09-08", 200) => "2024-06-14 00:00:00"`                                                                                      |
| WORKDAY\_DIFF  | 返回日期1和日期2之间的工作日数。工作日不包括周末和可选的假日列表，格式为ISO格式的日期的逗号分隔字符串。 | `date1, date2, [holidayStr]` | Number   | `WORKDAY_DIFF("2023-06-18", "2023-10-01") => 75`                                                                                           |
| IS\_SAME       | 比较两个日期到一个单位并确定它们是否相同。如果是，则返回true，否则返回false。            | `date1, date2, [unit]`       | Boolean  | `IS_SAME("2023-09-08", "2023-09-10") => false`                                                                                             |
| IS\_AFTER      | 确定date1是否晚于date2。如果是，则返回true，否则返回false。                | `date1, date2, [unit]`       | Boolean  | <p><code>IS_AFTER("2023-09-10", "2023-09-08") => true</code></p><p><code>IS_AFTER("2023-09-10", "2023-09-08", "month") => false</code></p> |

### 数组和其他函数

除了上述分类的函数，本章节还会介绍一些处理数组或其他特定数据类型的函数。

| 函数名称           | 描述                                          | 输入                      | 输出     | 示例                                                                            |
| -------------- | ------------------------------------------- | ----------------------- | ------ | ----------------------------------------------------------------------------- |
| COUNTALL       | 返回所有元素的数量，包括文本和空白。                          | `value1, [value2, ...]` | Number | `COUNTALL(100, 200, "", "Teable", TRUE()) => 5`                               |
| COUNTA         | 返回非空值的数量。此函数既计算数字又计算文本值。                    | `value1, [value2, ...]` | Number | `COUNTA(100, 200, 300, "", "Teable", TRUE) => 4`                              |
| COUNT          | 返回数字项的数量。                                   | `value1, [value2, ...]` | Number | `COUNT(100, 200, 300, "", "Teable", TRUE) => 3`                               |
| ARRAY\_JOIN    | 使用分隔符将rollup项的数组连接成一个字符串。                   | `array, [separator]`    | String | `ARRAY_JOIN(["Tom", "Jerry", "Mike"], "; ") => "Tom; Jerry; Mike"`            |
| ARRAY\_UNIQUE  | 返回数组中仅有的唯一项。                                | `array`                 | Array  | `ARRAY_UNIQUE([1, 2, 3, 2, 1]) => [1, 2, 3]`                                  |
| ARRAY\_FLATTEN | 通过删除任何数组嵌套来展平数组。所有项目成为单个数组的元素。              | `array`                 | Array  | `ARRAY_FLATTEN([1, 2, " ", 3, true], ["ABC"]) => [1, 2, 3, " ", true, "ABC"]` |
| ARRAY\_COMPACT | 从数组中删除空字符串和null值。保留"false"和包含一个或多个空白字符的字符串。 | `array`                 | Array  | `ARRAY_COMPACT([1, 2, 3, "", null, "ABC"]) => [1, 2, 3, "ABC"]`               |
| RECORD\_ID     | 返回当前记录的ID。                                  | `-`                     | String | `RECORD_ID() => "recxxxxxx"`                                                  |

