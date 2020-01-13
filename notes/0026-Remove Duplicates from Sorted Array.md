# 26.删除排序数组中的重复项

## 题目描述

给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。

不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。

示例 1:

> 给定数组 nums = [1,1,2], 
> 
> 函数应该返回新的长度 2, 并且原数组 nums 的前两个元素被修改为 1, 2。 
> 
> 你不需要考虑数组中超出新长度后面的元素。

示例 2:

> 给定 nums = [0,0,1,1,1,2,2,3,3,4],
> 
> 函数应该返回新的长度 5, 并且原数组 nums 的前五个元素被修改为 0, 1, 2, 3, 4。
> 
> 你不需要考虑数组中超出新长度后面的元素。

说明:

为什么返回数值是整数，但输出的答案是数组呢?

请注意，输入数组是以“引用”方式传递的，这意味着在函数里修改输入数组对于调用者是可见的。

你可以想象内部操作如下:

```javascript
// nums 是以“引用”方式传递的。也就是说，不对实参做任何拷贝
int len = removeDuplicates(nums);

// 在函数里修改输入数组对于调用者是可见的。
// 根据你的函数返回的长度, 它会打印出数组中该长度范围内的所有元素。
for (int i = 0; i < len; i++) {
    print(nums[i]);
}
```

## 解法

### 解法一

`splice()`修改原数组，去除重复项。

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var removeDuplicates = function(nums) {
    let cur = nums[0];
    for (let i=1; i<nums.length;){
        if(nums[i] === cur){
            nums.splice(i,1);
        }else{
            cur = nums[i++];
        }
    }
    return nums.length;
};
```

### 解法二

直接修改所需长度内的数组数据项。

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var removeDuplicates = function(nums) {
    let len = 1;
    for (let i=1; i<nums.length; i++){
        if(nums[i] !== nums[i-1]){
            nums[len] = nums[i]
            len++;
        }
    }
    return len;
};
```