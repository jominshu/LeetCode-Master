## 題目描述
給定一個非負整數 x,請將其最後兩位數字交換位置後回傳。
如果 x 只有一位數,回傳原數字
如果 x 的最後兩位相同,也視為已交換,回傳原數字

<img width="1196" height="772" alt="image" src="https://github.com/user-attachments/assets/74bd559c-2ece-41b1-9a64-3e5339f52ddb" />


## 思路
用數字來拆解，先確認x的邊界條件，當x小於10，直接回傳x。
若x大於等於10，進入判斷，先處理個位數，用%取餘數，得到個位數a。

```
let x = 11

function digitSwap(x){
    let a = 0;
    let b = 0;
    let c = 0;
    let abc = 0;

    if(x<10){
        return x;
    }else{
        a = x % 10
        b = Math.floor(x/10)%10
        c = Math.floor(x/100)
        abc = c*100 + a*10 + b
    }

    return abc;


}

let result = digitSwap(x);
console.log(result);
```
