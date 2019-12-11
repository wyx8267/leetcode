# 14.最长公共前缀
## 题目描述
编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 ""。

示例 1:

> 输入: ["flower","flow","flight"]
> 输出: "fl"

示例 2:

> 输入: ["dog","racecar","car"]
> 输出: ""
> 解释: 输入不存在公共前缀。

说明:

所有输入只包含小写字母 a-z 。

## 解法
步骤：
1. 如果输入为空，返回“”。
2. 将数组第一项设为当前最长前缀。
3. 依次比较字符串中每个字符，遇到不同时，记录位置，使用`substr(0, 当前下标)`更新最长前缀。如果最长前缀已经为空字符串，返回。
4. 返回所得最长前缀。
```javascript
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function(strs) {
    if(strs.length === 0) return ''
    let prefix = strs[0]
    for(let i=1;i<strs.length;i++){
        let j=0
        for(;j<prefix.length && j<strs[i].length;j++){
            if(prefix[j] !== strs[i][j]) break
        }
        prefix = prefix.substr(0, j)
        if(prefix === '') return prefix
    }
    return prefix
};
```