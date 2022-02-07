##### use Mockaroo
##### create a 1000 size collection of the following schema

- product_name
- product_id
- product_rating
- currency
- price
- no_of_purchases
- qty_left

```to import```
```js
 mongoimport --db db_name --collection collection_name --file data.json --port 27017  --jsonArray 
 ```
- Do the following queries
- 1. top 10 purchased items
- 2. top 10 cheapest items
- 3. top items where qty remains in stock
- 4. top 10 rated products
- 5. bottom 10 rated products
- 6. from 11-20 top rated products
- 7. find products with rating between 3 and 4, and sorted from descending order of rating, if the ratings are same, then show the alphabetic order of name of the product

- 1. 
```js
     db.product.find().sort({no_of_purchases:-1}).limit(10)
```

- 2. 
```js
    db.product.find().sort({price:1}).limit(10)
```

- 3. 
```js
    db.product.find().sort({qty_left:-1}).limit(10)
```

- 4. 
```js
     db.product.find().sort({price:-1}).limit(10).pretty()
```
```Note:~ Pretty() is for making prettier like how it will print the output```
- 5. 
```js
     db.product.find().sort({price:-1}).skip(990).limit(10)
```

- 6. 
```js
    db.product.find().sort({price:-1}).skip(10)limit(10).pretty()
```

- 7. 
```js
     db.product.find({$and:[{product_rating:{$gte:3}},{product_rating:{$lte:4}}]}).sort({product_rating:1,product_name:1})
```
