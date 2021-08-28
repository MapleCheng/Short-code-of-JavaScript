CSVToArray
===
Converts the CSV string to a 2D array.

### Params
| name | type | default | description |
| :--: | :--: | :-----: | :---------- |
| data | string | undefined | CSV data |
| delimiter | string | "," | Separate the value in each row |
| skipRowSize | number | 0 | Skip size of row |

### code

```js
function CSVToArray (data, delimiter = ",", skipRowSize = 0) {
  return (
    data.replace(/\r\n/g, '\n')
        .split('\n')
        .slice(skipRowSize)
        .map((t) => t.split(delimiter))
  )
}
```

### test

```js
CSVToArray("a,b\r\n1,2\r\n3,4") // [["a", "b"], ["1", "2"], ["3", "4"]]
CSVToArray("a,b\n1,2\n3,4") // [["a", "b"], ["1", "2"], ["3", "4"]]
CSVToArray("a;b\n1;2\n3;4", ";") // [["a", "b"], ["1", "2"], ["3", "4"]]
CSVToArray("a,b\n1,2\n3,4", ",", 1) // [["1", "2"], ["3", "4"]]
```

