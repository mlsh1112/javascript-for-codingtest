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
function binarySearch(A,x){
    let n=A.length
    let beg=0
    let end=n-1
    result=-1
    while(beg<=end){
        mid=Math.floor((beg+end)/2)
        if(A[beg]<=x){
            beg=mid+1
            result=mid
        }
        else
            end=mid-1
    }

    return result
}
```

