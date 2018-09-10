计算localStorage用量
```
function localStorageUsed() {
  var size = Object.keys(localStorage).map(function (n) {
      return localStorage.getItem(n).length
    }).reduce(function (t, n) {
      return t + n
    })
  console.log('localStorage used ' + (size / 1024 | 0) + 'KB')
  return size
}
```

显示localStorage详细用量，并排序
```
function localStorageUsedDetail() {
  var list = Object.keys(localStorage).map(function (key) {
      var value = localStorage.getItem(key);
      return { key: key, size: value.length, value: value};
    }).sort(function (a, b) {
      return a.size > b.size ? -1 : 1;
    })
  console.table(list)
  return list;
}
```
