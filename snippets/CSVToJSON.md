CSVToJSON
===

Converts the CSV string to a JSON string.



### Params
|   name    |  type  |  default  | description                    |
| :-------: | :----: | :-------: | :----------------------------- |
|   data    | string | undefined | CSV data                       |
| delimiter | string |    ','    | Separate the value in each row |



### Code

```js
function CSVToJSON (data, delimiter = ',') {
  // split new line character
  const data_row = data.replace(/\r\n/g, '\n').split('\n')
  
  // Extract title
  const titles = data_row[0].split(delimiter)
  
  return data_row
    .slice(1)
    .map(text => {
      const values = text.split(delimiter)
      
      return titles.reduce(
        (obj, title, index) => ((obj[title] = values[index]), obj), {}
      );
  })
}
```



### Test

```js
CSVToJSON('col1,col2\r\na,b\r\n1,2\r\n3,4')
// [{col1: 'a', col2: 'b'}, {col1: '1', col2: '2'}, {col1: '3', col2: '4'}]
CSVToJSON('col1,col2\na,b\n1,2\n3,4')
// [{col1: 'a', col2: 'b'}, {col1: '1', col2: '2'}, {col1: '3', col2: '4'}]
CSVToJSON('col1;col2\na;b\n1;2\n3;4', ';')
// [{col1: 'a', col2: 'b'}, {col1: '1', col2: '2'}, {col1: '3', col2: '4'}]
```

