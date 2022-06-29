# Element Query Operator
  
  | Operator        | Keterangan                                                  | 
  | --------------- |:-----------------------------------------------------------:|
  | $exists         | Mencocokkan document yang memiliki field tersebut           |
  | $type           | Mencocokkan document yang memiliki type field tersebut      | 


  
~~~ javascript
/**ingin menampilkan produk yang tidak memiliki field category
 * SQL : // select * from products where category is null
 */

db.products.find({
    category: {
        $exists: false
    }
});

/**ingin menampilkan produk yang memiliki field category
 * SQL : select * from products where category is not null
 */

 db.products.find({
    category: {
        $exists: true
    }
});
~~~

~~~ javascript
/**ingin menampilkan produk yang katagorinya memiliki tipe data 'string'
 * ingin mengecek apakah tipe data field category adalah 'sring'
 * SQL : select * from products where type(category) = "string"
 */
db.products.find({
    category: {
        $type: "string"
    }
});


/**Jika lebih dari satu tipe data maka gunakan [array]
 * contohnya ingin menampilkan produk yang katagorinya memiliki tipe data 'string' atau 'long'
 * SQL : select * from products where type(category) in ("long", "string")
 */
 db.products.find({
    category: {
        $type: ["string", "long"]
    }
});
~~~

