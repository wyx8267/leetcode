# 9.回文数
## 题目描述
判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。

示例 1:

> 输入: 121
> 输出: true

示例 2:

> 输入: -121
> 输出: false
> 解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。

示例 3:

> 输入: 10
> 输出: false
> 解释: 从右向左读, 为 01 。因此它不是一个回文数。

进阶:

你能不将整数转为字符串来解决这个问题吗？

## 解法
1. 通过取整和取余操作每次比较两端的数字
```javascript
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(x) {
    if (x < 0) return false
    var a = 1
    while (x / a >= 10) a *= 10
    while (x > 0) {
        var left = parseInt(x / a)
        var right = x % 10
        if (left !== right) return false
        x = parseInt((x % a) / 10)
        a /= 100
    }
    return true
};
```
2. 以字符串形式翻转并比较
```javascript
var isPalindrome = function(x) {
    var reverse = x.toString().split('').reverse().join('')
    return x.toString() === reverse ? true : false
};
```