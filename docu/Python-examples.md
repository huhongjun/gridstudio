Python相关功能，参看 /python/init.py

# 1 代码编辑器

# testing

    sheet("A1:A2", [1,2])
    df = pd.DataFrame({'a':[1,2,3], 'b':[4,5,6]})
    sheet("A1:B2")

## 图表

    data = sheet("A68:A71")
    data.plot()
    show()

    data = sheet("A68:A71")
    data.hist()
    show()


# 2 右键菜单

# 3 python扩展

## 从电子表格获得Pandas数据表
df = sheet("A1:D10")

## 将数据表写入单元格
sheet("A", df)

sheet("A", pd.read_sql('SELECT * FROM orders', connection))

# 4 自定义电子表格函数

Grid支持一些函数，类似Microsoft Excel和Google Sheets中的函数，使用方式也是在单元个中填写=MYCUSTOMFUNC(A1)

## SUM(value, ...) - 求和

Example: SUM(A1:A10) or SUM(A1,A2)

## AVERAGE(value, ...) - 求均值 (mean)

Example: AVERAGE(A1:A10) or AVERAGE(A1,A2)

## IF(logical-value, value, value) - if逻辑函数

Example: IF(A1 > 2, 1, 0) or IF(A1 == "random", RAND(), 1)

## MATHC(string) - get a mathematical constant

Example: MATHC("pi") or MATHC("e") or MATHC("π") - currently only π and e are in MATHC

## SQRT(number) - 求数值平方根

Example: SQRT(A1) or SQRT(2)

## CONCATENATE(string-value) or CONCAT(string-value) - 合并字符串

Example: CONCAT("Hello, ", "World!")

## NUMBER(value) - converts a value to a number

Example: NUMBER("0123") = 123

## LEN(value) - get the length of the string representation of a value

Example: LEN("abcd") = 4 or LEN(100) = 3

## COUNT(values) - get the amount cells that contain a value

Example: COUNT(A1:A10) = 4 (if 4 cells are non-empty)

## RAND() - get a random number between 0 and 1

Example: RAND() = 0.92892480103

## FLOOR(number) - take the floor of a number

Example: FLOOR(1.9) = 1

## CEIL(number) - take the ceil of a number

Example: CEIL(1.1) = 2

## ABS(number) - take the absolute value of a number

Example: ABS(-12.1) = 12.1

## VLOOKUP(value, lookup_range, column_index) - look up a value based on a key value

Example: VLOOKUP(A1, Sheet2!$A$1:$D$100, 4) - look up the value in A1 in column Sheet2!A1 and return the result in the 4th column (D).

## OLS(y_range, x1_range, x2_range, ...) - Perform a linear regression with form y ~ x1 + x2 + ...

Example: OLS(A1:A10, B1:B10, C1:C10) with for example A1:A10 containing house prices, B1:B10 containing square meter count and C1:C10 counting city dummy variable