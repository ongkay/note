~~~ javascript

~~~


# Query Document
[![Video dari youtube](http://img.youtube.com/vi/3An0AfYyZAM/0.jpg)](http://www.youtube.com/watch?v=3An0AfYyZAM)

Sama seperti di **relational database**, di MongoDB pun kita bisa melakukan query atau pencarian document yang sudah kita simpan di collection
untuk mencari document dengan query bisa gunakan 
+ Syntax `db.<collection>.find(query)`

+ contohnya :
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
[![Video dari youtube](http://img.youtube.com/vi/M3Ho4djinHE/0.jpg)](http://www.youtube.com/watch?v=M3Ho4djinHE)

Operator | Keterangan
--- | ---
`$eq` | Membandingkan value dengan value lain
`$gt` |Membandingkan value lebih besar dari value lain
`$gte` | Membandingkan value lebih besar atau sama dengan value lain
`$lt` | Membandingkan value lebih kecil dari value lain
`$lte` | Membandingkan value lebih kecil atau sama dengan value lain
`$in` | Membandingkan value dengan value yang ada di array
`$nin` | Membandingkan value tidak ada dalam value yang ada di array
`$ne` | Membandingkan value tidak sama dengan value lain

Info lebih detail : https://docs.mongodb.com/manual/reference/operator/query-comparison/

+ Syntax :
    ~~~ javascript
    db.customers.find({
        field: {
            $operator: "value"
        }
    });
    ~~~

+ contoh penggunaannya : 
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
[![Video dari youtube](http://img.youtube.com/vi/9bwQA68o7nQ/0.jpg)](http://www.youtube.com/watch?v=9bwQA68o7nQ)

Operator | Keterangan
--- | ---
`$and` | Menggabungkan query dengan operasi AND, mengembalikan document jika semua kondisi benar
`$or` | Menggabungkan query dengan operasi OR, mengembalikan document jika salah satu kondisi benar
`$nor` | Menggabungkan query dengan operasi NOR, mengembalikan document yang gagal di semua kondis
`$not` | Membalikkan kondisi, mengembalikan document yang tidak sesuai kondisi

info lebih detail : https://docs.mongodb.com/manual/reference/operator/query-logical/

+ Syntax Logical Operator untuk `$and` `$or`, `$nor`
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

    Contoh penggunaannya : 
    ~~~ javascript
    /**ingin menampilkan semua produk yang ada di katagori "Laptop dan Hanphone dengan harga diatas 20000000" 
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
    ~~~

+ Syntax Logical Operator khusus untuk `$not`
    ~~~ javascript
    db.collection.find({
        field: {
            $not: {
                // operator expression
            }
        }
    })
    ~~~

    Contohnya :
    ~~~ javascript
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
[![Element Query Operator](http://img.youtube.com/vi/Qm5PHB0ZAXw/0.jpg)](http://www.youtube.com/watch?v=Qm5PHB0ZAXw)  

  | Operator        | Keterangan                                                  | 
  | --------------- |:-----------------------------------------------------------:|
  | `$exists`         | Mencocokkan document yang memiliki field tersebut           |
  | `$type`           | Mencocokkan document yang memiliki type field tersebut      | 

Lebih lengkap lagi cek : https://docs.mongodb.com/manual/reference/operator/query-element/

+ Syntax Element Query Operator
    ~~~ javascript
    db.collection.find({
        field: {
            $exists: value
        }
    });
    ~~~

+ Contoh menggunakan `$exists`
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

+ Contoh menggunakan `$type`
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



# Evaluation Query Operator
[![Video dari youtube](http://img.youtube.com/vi/MyM_Qa4mCGM/0.jpg)](http://www.youtube.com/watch?v=MyM_Qa4mCGM)

Operator | Keterangan
--- | ---
`$expr` | Menggunakan aggregation operation
`$jsonSchema` | Validasi document sesuai dengan JSON schema
`$mod` | Melakukan operasi modulo 
`$regex` | Mengambil document sesuai dengan regular expression (PCRE)
`$text` | Melakukan pencarian menggunakan text
`$where` | Mengambil document dengan JavaScript Function

+ `$expr` : Menggunakan aggregation operation
   - Syntax `$expr` :
        ~~~ javascript
        db.products.find({
            $expr: {
                // aggretion expression
            }
        });
        ~~~

    - Contoh menggunakan `$expr` :
        ~~~ javascript
        /**Mencari produk yang field price diatas 1000000
         * SQL : select * from products where price > 1000000
        */

        db.products.find({
            $expr: {
                $gt: ["$price", 1000000]
            }
        });

        /** mencari produk dengan uppercasin dulu field _id
         * SQL : select * from customers where toUpper(_id) = 'KHANNEDY'
        **/
        db.customers.find({
            $expr: {
                $eq: [
                    { $toUpper: "$_id" }, 
                    "KHANNEDY"
                ]
            }
        });
        ~~~
        

    - lebih detail lagi cek di :
        https://docs.mongodb.com/manual/reference/operator/query/expr/
        https://docs.mongodb.com/manual/meta/aggregation-quick-reference/#aggregation-expressions


+ `$jsonSchema` : Validasi document sesuai dengan JSON schema
    - Syntax `$jsonSchema` :
        ~~~ javascript
        db.products.find({
            $jsonSchema: {
                // JSON Schema Object
            }
        });
        ~~~

    - Contoh menggunakan `$jsonSchema` :
        ~~~ javascript
        //mengambil produk yang wajib ada field 'name' dan 'catagory'
        // select * from products where name is not null and category is not null
        db.products.find({
            $jsonSchema: {
                required: [ "name", "category"]
            }
        });

        //contoh lebih detail lagi
        // select * from products where name is not null and type(name) = 'string' and type(price) = 'long'
        db.products.find({
            $jsonSchema: {
                required: [ "name"],
                properties: {
                    name: {
                        bsonType: "string"
                    },
                    price: {
                        bsonType: "long"
                    }
                }
            }
        });
        ~~~

    - lebih detail lagi cek di :
        http://json-schema.org/
        https://docs.mongodb.com/manual/reference/operator/query/jsonSchema/


+ `$mod` : Melakukan operasi modulo 
    - Syntax `$mod` :
        ~~~ javascript
        db.products.find({ 
            field: { 
                $mod: [ devisor, reminder]
            } 
        });
        ~~~

    - Contoh menggunakan `$mod` :
        ~~~ javascript
        /**mencari produk dengan harga yg habis di bagi 5
        * select * from products where price % 5 = 0
        **/
        db.products.find({ 
            price: { 
                $mod: [5, 0]
            } 
        });
        ~~~

    - lebih detail lagi cek di :
        https://docs.mongodb.com/manual/reference/operator/query/mod/

+ `$regex` : Mengambil document sesuai dengan regular expression (PCRE)
    - Syntax `$regex` :
        ~~~ javascript
        db.products.find({
            field: {
                $regex: /regex/,
                $options: "<option>"
            }
        });
        ~~~

    - Contoh menggunakan `$regex` :
        ~~~ javascript
        /**Mencari produk yang mengandung kata 'mie
         * SQL : select * from products where name like "%mie%"
        */
        db.products.find({
            name: {
                $regex: /mie/,
                $options: "i"
            }
        });

        /**Mencari produk dengan katakunci yang diawali dengan 'Mie'
        * SQL : select * from products where name like "Mie%"
        */
        db.products.find({
            name: {
                $regex: /^Mie/
            }
        });
        ~~~

    - lebih detail lagi cek di :
        https://regexr.com/
        https://docs.mongodb.com/manual/reference/operator/query/regex/

+ `$text` : Melakukan pencarian menggunakan text
    - Syntax `$text` :
        ~~~ javascript
        db.products.find({
            $text: {
                $search: "string",
                $language: "string", //opsional
                $caseSensitive: "boolean", //opsional
                $diacriticSensitive: "boolean" //opsional
            }
        });
        ~~~

    - Contoh menggunakan `$text` :
        ~~~ javascript
        /**Mencari Produk dengan Index
         * SQL : create text index on products
        **/
        db.products.createIndex({
            name: "text",
            catagory: "text"
        });

        //dengan membuat index di atas, maka pencarian hanya didalam field 'name' dan 'catagory'

        /**Mencari produk dengan katakunci yang mengandung kata 'mie' ATAU 'sedap' 
        * di field index diatas
        * SQL : select * from products where (name like "%mie%" or name like "%sedap%")
        */
        db.products.find({
            $text: {
                $search: "mie sedap" //==> mie atau sedap
            }
        });

        /**Mencari produk dengan katakunci yang mengandung kata 'mie' DAN 'sedap' 
        * di field index diatas
        * SQL : select * from products where name like "%mie sedap%"
        */
        db.products.find({
            $text: {
                $search: '"mie sedap"' //==> mie dan sedap
            }
        });
        ~~~

    - lebih detail lagi cek di :
        https://docs.mongodb.com/manual/reference/operator/query/text/

+ `$where` : Mengambil document dengan JavaScript Function
    - Syntax `$jsonSchema` :
        ~~~ javascript
        db.collection.find({
            $where: function(){
                return "apa";
            }
        });
        ~~~

    - Contoh menggunakan `$jsonSchema` :
        ~~~ javascript
        /**Mencari ID menggunakan functions
         * SQL : select * fro customers where _id = "khannedy"
        **/
        db.customers.find({
            $where: function(){
                return this._id == "khannedy";
            }
        });
        ~~~

    - lebih detail lagi cek di :
        https://docs.mongodb.com/manual/reference/operator/query/where/

+ `$jsonSchema` : apa
    - Syntax `$jsonSchema` :
        ~~~ javascript

        ~~~

    - Contoh menggunakan `$jsonSchema` :
        ~~~ javascript
        
        ~~~

    - lebih detail lagi cek di :



 
