## The Problem

So far we have been working with data that looks like this

```
symbol,date,price
MSFT,Jan 2000,39.81
MSFT,Feb 2000,36.35
MSFT,Mar 2000,43.22
```

But what if we have data that looks like this?

```
"iyear","Belgium","Denmark","France","Germany","Greece","Ireland","Italy","Luxembourg","Netherlands","Portugal","Spain","United Kingdom"
2000,0,0,0,2,0,0,1,0,0,0,0,57
2006,0,0,1,2,0,1,0,0,0,0,2,0
```

This is a common d3 issue. Long Data vs Wide Data. And sometimes we want to convert from one to the other. We might want both formats, and we might want to switch formats too, depending on what we want to group

## Switching from Long Data to Wide Data

Converting wide data...

[[images/wide.jpeg]]

...to long data

[[images/long.jpeg]]

## The code

Here we take the original data array and convert it into a new array

```
  var orig_data = dsv.parse(raw);
  var data = [];
  orig_data.forEach( function(row) {
    
    Object.keys(row).forEach( function(colname) {
      // Ignore 'iyear' and 'price' columns
      if(colname == "iyear" || colname == "price") {
        return
      }
      data.push({"date": row["iyear"], "price": row[colname], "country": colname});
    });
  });
  console.table(orig_data)
  console.table(data)
```

1) We are making 3 NEW columns, "date", "price", and "country"
2) Everything from "iyear" is pushed into "date"
3) Every Column Name is pushed into "country"
4) Every Value from a Column goes into "price"
5) We ignore columns that we aren't converting

## Switching from Wide Data to Long Data

TODO

Depending how we are nesting or presenting data, we might want to do the opposite. Haven't done that yet, but its in the links below

## References

http://jonathansoma.com/tutorials/d3/wide-vs-long-data/

https://www.google.com/search?q=d3+wide+data+long+data+converting
