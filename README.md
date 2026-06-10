# day-1：C++ 学习笔记

## 主题：温度转换、四舍五入、vector 返回多个结果

这篇笔记用来记录我今天学习到的 C++ 知识，方便以后复习。

---

## 一、题目理解

这类题目通常会给一个摄氏度 `celsius`，要求我们返回两个结果：

1. 开尔文温度 `kelvin`
2. 华氏温度 `fahrenheit`

公式如下：

```cpp
kelvin = celsius + 273.15
fahrenheit = celsius * 1.80 + 32.00
```

如果题目要求华氏度四舍五入，就需要使用 `round()`。

---

## 二、完整代码

```cpp
#include <vector>
#include <cmath>
using namespace std;

class Solution {
public:
    vector<double> convertTemperature(double celsius) {
        double kelvin = celsius + 273.15;
        double fahrenheit = celsius * 1.80 + 32.00;

        int roundedFahrenheit = round(fahrenheit);

        return {kelvin, roundedFahrenheit};
    }
};
```

---

## 三、这里用到的新知识

### 1. `round(x)`

`round(x)` 的作用是：把 `x` 四舍五入到最近的整数。

使用 `round()` 需要引入头文件：

```cpp
#include <cmath>
```

例子：

```cpp
round(36.5); // 结果是 37
round(36.4); // 结果是 36
```

---

### 2. `int`

`int` 表示整数类型。

例如：

```cpp
int age = 18;
int roundedFahrenheit = round(fahrenheit);
```

在这段代码里：

```cpp
int roundedFahrenheit = round(fahrenheit);
```

意思是把 `fahrenheit` 四舍五入之后，存进整数变量 `roundedFahrenheit`。

---

### 3. `double`

`double` 表示小数类型。

例如：

```cpp
double celsius = 25.0;
double kelvin = celsius + 273.15;
```

摄氏度、开尔文、华氏度这些计算结果可能有小数，所以通常用 `double`。

---

### 4. `vector<double>`

`vector<double>` 可以理解成：

```text
一个可以存放多个 double 小数的数组
```

例如：

```cpp
vector<double> result = {300.15, 80.0};
```

在这道题中，函数要返回两个结果，所以返回类型写成：

```cpp
vector<double>
```

---

### 5. `return {a, b}`

`return {a, b}` 表示返回一个包含两个元素的列表。

在这道题里：

```cpp
return {kelvin, roundedFahrenheit};
```

表示返回：

```text
第一个结果：kelvin
第二个结果：roundedFahrenheit
```

注意：

虽然 `roundedFahrenheit` 是 `int` 类型，但是返回类型是 `vector<double>`，所以它会自动转换成 `double` 存进去。

---

## 四、代码逐行解释

### 第 1 行

```cpp
#include <vector>
```

引入 `vector`，因为代码中用到了：

```cpp
vector<double>
```

---

### 第 2 行

```cpp
#include <cmath>
```

引入数学函数库，因为代码中用到了：

```cpp
round()
```

---

### 第 3 行

```cpp
using namespace std;
```

这样写之后，就可以直接使用：

```cpp
vector<double>
```

不用写成：

```cpp
std::vector<double>
```

---

### 第 5 行

```cpp
class Solution {
```

这是题目要求的类结构，一般不要改。

---

### 第 7 行

```cpp
vector<double> convertTemperature(double celsius) {
```

这行表示定义一个函数。

函数名是：

```cpp
convertTemperature
```

参数是：

```cpp
double celsius
```

返回值是：

```cpp
vector<double>
```

意思是：

```text
输入一个摄氏度 celsius，返回一个 double 数组。
```

---

### 第 8 行

```cpp
double kelvin = celsius + 273.15;
```

根据公式计算开尔文温度：

```cpp
kelvin = celsius + 273.15
```

---

### 第 9 行

```cpp
double fahrenheit = celsius * 1.80 + 32.00;
```

根据公式计算华氏度：

```cpp
fahrenheit = celsius * 1.80 + 32.00
```

---

### 第 11 行

```cpp
int roundedFahrenheit = round(fahrenheit);
```

把华氏度四舍五入成整数。

例如：

```cpp
round(36.5); // 37
round(36.4); // 36
```

---

### 第 13 行

```cpp
return {kelvin, roundedFahrenheit};
```

返回最终结果。

顺序不能写错：

```text
第一个：kelvin
第二个：roundedFahrenheit
```

---

## 五、重点总结

这段代码主要学到了：

1. 如何使用 `vector<double>` 返回多个结果
2. 如何用公式计算温度
3. 如何使用 `round()` 四舍五入
4. 如何使用 `return {a, b}` 返回两个值
5. `int` 可以自动转换成 `double`
6. `double` 适合存储小数
7. 使用 `round()` 需要 `#include <cmath>`

---

## 六、容易出错的地方

### 1. 忘记引入头文件

如果使用 `round()`，需要写：

```cpp
#include <cmath>
```

否则可能会报错。

---

### 2. 返回顺序写反

正确写法：

```cpp
return {kelvin, roundedFahrenheit};
```

错误写法：

```cpp
return {roundedFahrenheit, kelvin};
```

---

### 3. 不理解 `vector<double>`

`vector<double>` 可以理解成：

```text
一个可以存放小数的数组
```

例如：

```cpp
{300.15, 80}
```

虽然 `80` 看起来是整数，但它也可以作为 `double` 存进去。

---

### 4. 把 `round()` 写错

正确写法：

```cpp
round(fahrenheit)
```

错误写法：

```cpp
round fahrenheit
```

函数调用必须有括号。

---

## 七、我的理解

这道题不是只考温度公式，也是在练习 C++ 的基础语法。

我需要重点记住：

```cpp
vector<double>
```

表示返回一个小数数组。

```cpp
round(x)
```

表示把 `x` 四舍五入。

```cpp
return {a, b};
```

表示一次返回多个结果。

---

## 八、以后复习时重点看

以后复习这篇笔记时，重点看这几个地方：

```cpp
#include <vector>
#include <cmath>
```

```cpp
vector<double> convertTemperature(double celsius)
```

```cpp
double kelvin = celsius + 273.15;
double fahrenheit = celsius * 1.80 + 32.00;
```

```cpp
int roundedFahrenheit = round(fahrenheit);
```

```cpp
return {kelvin, roundedFahrenheit};
```

---

## 九、今日学习记录

今天我学习了：

- GitHub 仓库的基本使用
- 如何把学习笔记保存到仓库
- C++ 中的 `vector<double>`
- C++ 中的 `double`
- C++ 中的 `int`
- C++ 中的 `round()`
- C++ 中的 `return {a, b}`

这篇笔记会作为我的第一份 GitHub 学习记录。
