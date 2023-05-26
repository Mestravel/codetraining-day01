# codetraining-day01
## 1.二分法查找练习
### 习题704
链接：【https://leetcode.cn/problems/binary-search/】
自己一开始第一想法写的代码
```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0;
        int right = nums.length;
        int middle = (int)(left + right)/2;
        while(left < right){
            if(nums[middle] == target){
                return middle;
            }
            else if(middle == left){
                return -1;
            }
            else if(nums[middle] > target){
                right = middle;
                middle = (int)(left + right)/2;
            }
            else if(nums[middle] < target){
                left = middle;
                middle = (int)(left + right)/2;
            }
        }
        return -1;
    }
}
```
但是这有点投机取巧，没有理解这个方法中的一个关键问题，就是查找的定义域，无论是两边都闭合还是左闭右开核心都是查找了一个区域之后再查找的区域要完全略过已经确定没有的区域，接下来理解后的代码是这样的
```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0;
        int right = nums.length;
        int middle = (int)(left + right)/2;
        while(left < right){
            middle = (int)(left + right)/2;
            if(nums[middle] > target){
                right = middle ;
            }
            else if(nums[middle] < target){
                left = middle + 1;
            }
            else return middle;
        }
        return -1;
    }
}
```
这个感觉就很好
