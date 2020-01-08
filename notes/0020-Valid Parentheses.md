# 20.有效的括号

## 题目描述

给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。

有效字符串需满足：

1. 左括号必须用相同类型的右括号闭合。
2. 左括号必须以正确的顺序闭合。

注意空字符串可被认为是有效字符串。

示例 1:

> 输入: "()"
> 
> 输出: true

示例 2:

> 输入: "()[]{}"
> 
> 输出: true

示例 3:

> 输入: "(]"
> 
> 输出: false

示例 4:

> 输入: "([)]"
> 
> 输出: false

示例 5:

> 输入: "{[]}"
> 
> 输出: true

## 解法

步骤：
1. 如果输入为空，返回false。
2. 将数组第一项设为当前栈顶。
3. 在数组中循环，当前数组项与当前栈顶匹配，若匹配为一对括号，取出栈顶元素，否则，当前数组项加入成为新的栈顶元素。
4. 判断栈中元素是否匹配结束，为空栈则返回true。
```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function (s) {
    if (s.length < 1) return true
    let arr = s.split('')
    let q = []
    q.push(arr[0])
    for (let i = 1; i < arr.length; i++) {
        let x = q[q.length - 1]
        if ((x === '(' && arr[i] === ')') || (x === '[' && arr[i] === ']') || (x === '{' && arr[i] === '}')) {
            q.pop()
        } else {
            q.push(arr[i])
        }
    }
    if (q.length < 1) return true
    return false
};
```