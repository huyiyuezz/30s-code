# averageBy

在使用提供的函数将每个元素映射到一个值之后，计算数组的平均值。

## 思路

- 用于`Array.prototype.map()`将每个元素映射到`fn`.
- 使用`Array.prototype.reduce()`每个值添加到累加器，用的值进行初始化`0`。
- 将结果数组除以其长度。

## code
```javascript
const averageBy = (arr, fn) => 
    arr
        .map(typeof fn === 'function' ? fn : val => val[fn])
        .reduce((acc, val) => acc + val, 0) / arr.length;
```

## examples
```javascript
averageBy([{ n: 4 }, { n: 2 }, { n: 8 }, { n: 6 }], o => o.n); // 5
averageBy([{ n: 4 }, { n: 2 }, { n: 8 }, { n: 6 }], 'n'); // 5
```