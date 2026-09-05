## C++ XOR (`^` / `^=`)

`^`：按位异或（XOR），**相同为 0，不同为 1**。

```text
a ^ a = 0
a ^ 0 = a
a ^ b = b ^ a
```

`^=` 是异或赋值：

```cpp
a ^= b;  // 等价于 a = a ^ b;
```

## 位运算（Bitwise Operations）

直接对整数的**二进制位**进行操作。

```text
&   AND：都为 1 → 1
|   OR：有一个 1 → 1
^   XOR：不同 → 1
~   NOT：0/1 取反
<<  左移
>>  右移
```

常用：

```cpp
x & 1        // 判断奇偶
x << 1       // ×2
x >> 1       // ÷2
x ^ x == 0   // 相同数字异或抵消
```

## Boyer-Moore 投票算法

用于寻找出现次数 **> n/2** 的多数元素。

核心思想：**不同元素互相抵消，多数元素最后一定会剩下。**

```cpp
int candidate = 0;
int count = 0;

for (int x : nums) {
    if (count == 0)
        candidate = x;

    if (x == candidate)
        count++;
    else
        count--;
}
```

- 相同 → `count++`
- 不同 → `count--`
- `count == 0` → 更换候选人

复杂度：**时间 O(n)，空间 O(1)**。