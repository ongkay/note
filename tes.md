~~~ javascript

~~~


# Query Document

Sama seperti di **relational database**, di MongoDB pun kita bisa melakukan query atau pencarian document yang sudah kita simpan di collection
untuk mencari document dengan query bisa gunakan Syntax `db.<collection>.find(query)`
contoh :

~~~ javascript
// contoh cari _id :
db.customers.find({
    _id: "khannedy"
});

// contoh cari name :
db.customers.find({
    name: "Eko Kurniawan Khannedy"
});

// contoh cari harga :
db.products.find({
    price: 2000
});

// akses embeded objek
db.orders.find({
    "items.product_id": 1
});

// contoh cari name lebih dari satu :
db.customers.find({
    _id: "khannedy",
    name: "Eko Kurniawan Khannedy"
});
~~~

# Comparison Query Operator
Operator | Keterangan
--- | ---
$eq | Membandingkan value dengan value lain
$gt |Membandingkan value lebih besar dari value lain
$gte | Membandingkan value lebih besar atau sama dengan value lain
$lt | Membandingkan value lebih kecil dari value lain
$lte | Membandingkan value lebih kecil atau sama dengan value lain
$in | Membandingkan value dengan value yang ada di array
$nin | Membandingkan value tidak ada dalam value yang ada di array
$ne | Membandingkan value tidak sama dengan value lain


Syntax :
~~~ javascript
    db.customers.find({
        field: {
            $operator: "value"
        }
    });
~~~

contoh : 
~~~ javascript
/**Contoh mencari id dengan nama khannedy di collection customers
 * ada 2 cara dibawah ini :
 * SQL : select * from customers where _id = 'khannedy'
 */
    db.customers.find({
    _id: {
        $eq: "khannedy"
    }
});

//atau cara simple nya :
db.customers.find({
    _id: "khannedy"
});


/**contoh mencari harga yang harganya diatas 1000 di collection products
 * SQL : select * from products where price > 1000
 */
db.products.find({
    price: {
        $gt: 1000
    }
});



// insert product documents
db.products.insertMany([
    {
        _id: 3,
        name: "Pop Mie Rasa Bakso",
        price: new NumberLong(2500),
        category: "food"
    },
    {
        _id: 4,
        name: "Samsung Galaxy S9+",
        price: new NumberLong(10000000),
        category: "handphone"
    },
    {
        _id: 5,
        name: "Acer Precator XXI",
        price: new NumberLong(25000000),
        category: "laptop"
    }
]);

/**Contoh cara mencari/filter produk di katagori "hanphone dan laptop" di collection products
 * dan dengan harga diatas 5000000
 * SQL : select * from products where category in ('handphone', 'laptop') and price > 5000000
 */
db.products.find({
    category: {
        $in: ["handphone", "laptop"]
    },
    price: {
        $gt: 5000000
    }
});
~~~


# Logical Query Operator
    Operator | Keterangan
    --- | ---
    $and   | Menggabungkan query dengan operasi AND, mengembalikan document jika semua kondisi benar
    $or   | Menggabungkan query dengan operasi OR, mengembalikan document jika salah satu kondisi benar
    $nor   | Menggabungkan query dengan operasi NOR, mengembalikan document yang gagal di semua kondis
    $not    | Membalikkan kondisi, mengembalikan document yang tidak sesuai kondisi.


Syntax Logical Operator untuk `$and` `$or`, `$nor`
~~~ javascript
db.collection.find({
    $operator : [
        {
            // expression
        },
        {
            //expression
        }
    ]
})
~~~

Syntax Logical Operator khusus untuk `$not`
~~~ javascript
db.collection.find({
    field: {
        $not: {
            // operator expression
        }
    }
})
~~~

Contoh :
~~~ javascript
/**contoh menampilkan semua produk yang ada di katagori "Laptop dan Hanphone dengan harga diatas 20000000" 
 * SQL : select * from products where category in ('laptop', 'handphone') and price > 20000000
*/
    db.products.find({
    $and: [
        {
            category: {
                $in: ["laptop", "handphone"]
            }
        },
        {
            price: {
                $gt: 20000000
            }
        }
    ]
});

/**ingin mencari/menampilkan produk yang katagorinya tidak didalam "laptop dan hanphone" 
 * SQL : select * from products where category not in ('laptop', 'handphone')
*/
db.products.find({
    category: {
        $not: {
            $in: ["laptop", "handphone"]
        }
    }
});

/**ingin mencari produk  yang harganya 1000 hingga 20000000 
 * dan katagorinya tidak sama dengan 'food'
 * SQL : select * from products where price between 10000000 and 20000000 and category != 'food'
*/
db.products.find({
    $and: [
        {
            price: {
                $gte: 1000,
                $lte: 20000000
            }
        },
        {
            category: {
                $ne: 'food'
            }
        }
    ]
});
~~~


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

