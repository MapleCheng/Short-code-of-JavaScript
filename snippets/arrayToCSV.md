arrayToCSV
===

Converts the 2D array to CSV string.



### Params
|   name    |  type  |  default  | description                    |
| :-------: | :----: | :-------: | :----------------------------- |
|   data    | string | undefined | CSV data                       |
| delimiter | string |    ','    | Separate the value in each row |



### Code

```js
function arrayToCSV(arr, delimiter=',') {
  return arr
    .map((row) => (row.join(delimiter)))
    .join("\n")
}
```



### Test

```js
CSVToArray([['a', 'b'], ['1', '2'], ['3', '4']]) // "a,b\r\n1,2\r\n3,4"
CSVToArray([['a', 'b'], ['1', '2'], ['3', '4']], ';') // "a;b\n1;2\n3;4"
```

