## 題目描述
給定一個整數陣列 nums 和一個整數 target,請找出陣列中是否有兩個數字的和等於 target。
如果存在這樣的配對,回傳 true;否則回傳 false。

## 思路1
使用雙重迴圈遍歷陣列中每個元素與下個元素進行相加，在只考慮組合不考慮順序情形，[2,3]組合跟[3,2]相同。
時間複雜度為O(n2)

## 暴力解
```
function findPair(nums, target){
   for(let i = 0; i < nums.length; i++){
        for(let j = i+1; j < nums.length; j++){
            if(nums[i]+nums[j]==target){
                return true;
            }
        }
    }
     return false;
}

let result = findPair(nums, target);
console.log(result);

```
## 思路2
使用雙指針做這題，需要先將陣列轉為有序陣列，因為雙指針要從頭跟尾巴開始向中間找target，如果非有序的話無法有效判斷邊界。
時間複雜度為O(nlogn)

## 雙指針
```
const nums = [1,5,3]
const target = 10

function findPairTwoPtr(nums, target){
    let left = 0;
    let right = nums.length-1;

    let sortedNums = nums.sort((a,b)=>a-b);

    while(left < right){
        let sum = sortedNums[left] + sortedNums[right]
        if(sum == target){
            return true;
        }else if(sum > target){
            right--;
        }else if(sum < target){
            left++;
        }
    }
    return false;
}

let result = findPairTwoPtr(nums,target)
console.log(result);

```
