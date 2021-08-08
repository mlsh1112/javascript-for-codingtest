# javascript-for-codingtest
* * *
## 자바스크립트 코딩 테스트 요약
- [1. 순열](#순열)
- [2. 조합](#조합)
- [3. 소수 찾기](#소수-찾기)
- [4. 행과 열 바꾸기](#행과-열-바꾸기)
- [5. 배열 값 더하기](#배열-값-더하기)
- [6. 진수](#진수)
- [7. 약수 개수 구하기](#약수-개수-구하기)
- [8. 이진 탐색](#이진-탐색)
- [9. 집합](#집합)
- [10. 우선순위 큐](#우선순위-큐)
- [11. 최대공약수](#최대공약수)
- [12. 최소공배수](#최소공배수)
- [13. 2차원 배열](#2차원-배열)
* * *
## 순열
```
const getPermutations= function (arr, selectNumber) {
  const results = [];
  if (selectNumber === 1) return arr.map((value) => [value]); // 1개씩 택할 때, 바로 모든 배열의 원소 return

  arr.forEach((fixed, index, origin) => {
    const rest = [...origin.slice(0, index), ...origin.slice(index+1)] // 해당하는 fixed를 제외한 나머지 배열 
    const permutations = getPermutations(rest, selectNumber - 1); // 나머지에 대해 순열을 구한다.
    const attached = permutations.map((permutation) => [fixed, ...permutation]); // 돌아온 순열에 대해 떼 놓은(fixed) 값 붙이기
    results.push(...attached); // 배열 spread syntax 로 모두다 push
  });

  return results; // 결과 담긴 results return
};
```

## 조합
```
const getCombinations = function (arr, selectNumber) {
  const results = [];
  if (selectNumber === 1) return arr.map((value) => [value]); // 1개씩 택할 때, 바로 모든 배열의 원소 return

  arr.forEach((fixed, index, origin) => {
    const rest = origin.slice(index + 1); // 해당하는 fixed를 제외한 나머지 뒤
    const combinations = getCombinations(rest, selectNumber - 1); // 나머지에 대해서 조합을 구한다.
    const attached = combinations.map((combination) => [fixed, ...combination]); //  돌아온 조합에 떼 놓은(fixed) 값 붙이기
    results.push(...attached); // 배열 spread syntax 로 모두다 push
  });

  return results; // 결과 담긴 results return
}
```

## 소수 찾기
```
function isPrime(num){
    for(let i=2;i*i<=num;i++){
        if(num%i===0) return false
    }
    return true
}
```

## 행과 열 바꾸기
```
const transpose = matrix => matrix.reduce(
  (result, row) => row.map((e, i) => [...(result[i] || []), e]),
  []
);
```

## 배열 값 더하기
```
[].reduce((a, b) => a + b)
```

## 진수
#### 10진수 -> 16진수
```
var hex = dec.toString(16)
```
#### 10진수 -> 2진수
```
var bin = dec.toString(2)
```
#### 16진수 -> 10진수
```
var dec = parseInt(hex, 16)
```
#### 16진수 -> 2진수
```
var dec = parseInt(hex, 16).toString(2)
```
#### 2진수 -> 10진수
```
var dec = parseInt(bin, 2)
```
#### 2진수 -> 16진수
```
var hex = parseInt(bin, 2).toString(16)
```

## 약수 개수 구하기
```
function countPrime(n){
    let i=1
    let result=0

    while(i*i<n){
        if(n%i===0)
            result+=2
        i+=1
    }
    if(i*i===n)
        result++

    return result
}
```

## 이진 탐색
```
function binarySearch(arr,target{
    let start = 0
    let end = arr.length
    while(start<end){
      const mid = Math.floor((start+end)/2)
      if(arr[mid]>=target){
        end=mid
      }
      else{
        start=mid+1
      }
    }
}
```
## 집합
```
// 합집합
let unionSet = new Set([...setA, ...setB])

for (let value of unionSet) {
  console.log(value);
}
// 차례대로 1, 2, 3, 4, 5, 6, 7, 8 출력


// 교집합
let intersectionSet = new Set(
  [...setA].filter(v => setB.has(v))
);

for (let value of intersectionSet) {
  console.log(value);
}
// 차례대로 4, 5 출력


// 차집합
let differenceSet = new Set(
  [...setA].filter(v => !setB.has(v))
);

for (let value of differenceSet) {
  console.log(value);
}
// 차례대로 1, 2, 3 출력
```
## 우선순위 큐
```
class PriorityQueue {
    constructor() {
        this.memory = [];
        this.length = 0;
    }
    
    push(newItem) {
        this.length++;
        
        let isAdded = false;
        
        for(let i = 0 ; i < this.memory.length ; ++i){
            if(this.memory[i].weight > newItem.weight){
                this.memory.splice(i, 0, newItem);
                isAdded = true;
                break;
            } 
        }        
        
        if(!isAdded) this.memory.push(newItem);
    }
    
    pop() {
        this.length--;
        return this.memory.shift();
    }

}
```
## 최대공약수
```
function gcd(minNum, maxNum){
  return (minNum % maxNum) === 0 ? maxNum : gcd(maxNum, minNum % maxNum);
}
```
## 최소공배수
```
function lcm(minNum, maxNum){
  return minNum * maxNum / gcd(minNum, maxNum);
}
```
## 2차원 배열
```
const graph = Array.from({ length: n + 1 }, () => Array(n + 1).fill(false));
```
