<a name="top"></a>

## Table of Contents
1. [Pengenalan MongoDB](https://www.youtube.com/watch?v=JXXUBiJGu94&list=PL-CtdCApEFH-eFFdPeS5e16o3THdmvxvz&index=2)
1. [Menginstall MongoDB](https://www.youtube.com/watch?v=E4MHb_ctVKA&list=PL-CtdCApEFH-eFFdPeS5e16o3THdmvxvz&index=3)
1. [MongoDB Client](https://www.youtube.com/watch?v=wuQoq0-f4kQ&list=PL-CtdCApEFH-eFFdPeS5e16o3THdmvxvz&index=4)
1. [Database](#04-database)
1. [Collection](#05-collection)
1. [Data Model](#06-data-model)
1. [BSON](#07-bson)
1. [Insert Document](#08-insert-document)
1. [Query Document](#09-query-document)
1. [Comparison Query Operator](#10-comparison-query-operator)
1. [Logical Query Operator](#11-logical-query-operator)
1. [Element Query Operator](#12-element-query-operator)
1. [Evaluation Query Operator](#13-evaluation-query-operator)
1. [Array Query Operator](#14-array-query-operator)
1. [Projection Operator](#15-projection-operator)
1. [Query Modifier](#16-query-modifier)
1. [Update Document](#17-update-document)
1. [Field Update Operator](#18-field-update-operator)
1. [Array Update Operator](#19-array-update-operator)
1. [Delete Document](#20-delete-document)
1. [Bulk Write Operation](#21-bulk-write-operation)
1. [Schema Validation](#22-schema-validation)
1. [Indexes](#23-indexes)
1. [Text Indexes](#24-text-indexes)
1. [Wildcard Indexes](#25-wildcard-indexes)
1. [Index Properties](#26-index-properties)
1. [Transaction (belum selesai)](#27-transaction)
1. [Security](#28-security)
1. [Authentication](#29-authentication)
1. [Authorization](#30-authorization)


# 04 Database
[![Video dari youtube](http://img.youtube.com/vi/apa-CmxYVyY/0.jpg)](http://www.youtube.com/watch?v=apa-CmxYVyY)

- **Apa itu Database ??**
    > - Database adalah tempat menyimpan collection 
    > - Semua collection harus disimpan di database
    > - Biasanya database digunakan untuk memisahkan data secara logical per aplikasi, artinya biasanya satu aplikasi akan memiliki satu database
    > - Jarang sekali kita akan menggunakan satu database untuk beberapa aplikasi

- **Membuat Database** 
    > - Kita tidak perlu secara eksplisit membuat database
    > - MongoDB akan secara otomatis membuatkan database sesuai dengan nama database yang kita pilih
    > - Untuk memilih nama database, kita bisa menggunakan perintah “use” diikuti nama database

- **Database Methods** [:link:docs](https://docs.mongodb.com/manual/reference/method/js-database/)
    Operator | Keterangan
    --- | ---
    `db.dropDatabase()` | Menghapus database
    `db.getName()` | Mengambil nama database
    `db.hostInfo()` | Mengambil informasi host tempat mongodb
    `db.version()` | Mengambil versi database
    `db.stats()` | Mengambil statistik penggunaan database

**[⬆ back to top](#top)**

# 05 Collection
[![Video dari youtube](http://img.youtube.com/vi/VbguzSZfvaE/0.jpg)](http://www.youtube.com/watch?v=VbguzSZfvaE)

+ **Apa itu Collection ??**
    > - Collection adalah tempat menyimpan document
    > - Maximum per document yang bisa disimpan adalah 16MB
    > - Maximum level nested document yang bisa disimpan adalah 100 level 

+ **Database Methods untuk Collection** [:link:docs](https://docs.mongodb.com/manual/reference/method/js-database/)
    Database Methods untuk Collection | Keterangan
    --- | ---
    `db.getCollectionNames()`  | Mengambil semua nama collection
    `db.createCollection(name)`  | Membuat collection baru
    `db.getCollection(name)`  | Mendapatkan object collection
    `db.<name>`  | Sama dengan `db.getCollection(<name>)`
    `db.getCollectionInfos()`  | Mendapat informasi semua collection

+ **Collection Methods** [:link:docs](https://docs.mongodb.com/manual/reference/method/js-collection/)
    Database Methods untuk Collection | Keterangan
    --- | ---
    `db.<collection>.find()` | Mengambil semua document 
    `db.<collection>.count()` | Mengambil jumlah document
    `db.<collection>.drop()` | Menghapus collection
    `db.<collection>.totalSize()` | Mengambil total ukuran collection
    `db.<collection>.stats()` | Mengambil informasi statistik collection

**[⬆ back to top](#top)**

# 06 Data Model
[![Video dari youtube](http://img.youtube.com/vi/RURinfDM8cA/0.jpg)](http://www.youtube.com/watch?v=RURinfDM8cA)

- **Kenapa Perlu Mengerti Data Modeling**
    > - Pindah dari relational database ke document database bukanlah hal yang sesederhana hanya dengan memindahkan semua table ke collection
    > - Penggunaan document database tidak akan mendatangkan manfaat besar jika kita tidak mengerti cara memodelkan data untuk kebutuhan aplikasi kita
    > - Saat memodelkan data menggunakan relational database, biasanya kita mengacu ke database normalization 
    > - Saat memodelkan data menggunakan document database, kita harus mengacu ke penggunaan aplikasi dalam melakukan query, update dan memproses data

- **Schema yang Flexible** 
    > - Tidak seperti di relational database, di MongoDB kita bisa memasukkan data ke collection secara langsung tanpa mendefinisikan schema collection nya.
    > - Schema untuk collection di MongoDB sangat flexible, tiap document bisa berbeda. Tidak seperti table di relational database yang harus sama  tiap record.
    > - Namun pada prakteknya, sangat direkomendasikan menggunakan jenis data yang sama untuk tiap collection, walaupun bisa berbeda-beda di collection yang sama
    > - 

**[⬆ back to top](#top)**

# 07 BSON
[![Video dari youtube](http://img.youtube.com/vi/P9T_V2h60cY/0.jpg)](http://www.youtube.com/watch?v=P9T_V2h60cY)

+ **Apa itu BSON ??**
    > - BSON singkatan dari Binary JSON, yaitu binary-encoded serialization dokumen seperti JSON
    > - Sama seperti JSON, di BSON juga bisa kita bisa menggunakan embedded object, array dan lain-lain
    > - http://bsonspec.org/ 
    > - https://docs.mongodb.com/manual/reference/bson-types/ 

+ **Tipe Data di BSON** 
    Tipe Data | Alias
    --- | ---
    Double  | double
    String  | string
    Object  | object
    Array  | arrat
    Binary Data  | binData
    ObjectId  | objectId
    Boolean  | bool
    Date  | date
    Null  | null
    Regular Expression  | regex
    JavaScript  | javascript
    JavaScript with Scope  | javascriptWithScope
    32 Bit Integer  | int
    Timestamp  | timestamp
    64 Bit Integer  | long
    Decimal 128  | decimal
    Min Key  | minKey
    Max key  | maxKey

+ **ObjectId** 
    > - ObjectId adalah random data yang unik, cepat untuk digenerate dan terurut.
    > - Nilai ObjectId memiliki ukuran panjang 12 byte, konsisten terdiri dari informasi 4 byte timestamp, 5 byte random value, dan 3 byte incrementing counter
    > - ObjectId digunakan sebagai sebagai default _id (primary key) di document jika kita tidak secara eksplisit menyebutkan _id document nya

+ **Date dan ISODate** 
    > - BSON Date adalah 64 bit integer yang merepresentasikan angka milisecond sejak Unix epoch (1 Januari 1970).
    > - Nilai ini bisa merepresentasikan waktu dengan jarak 290 juta tahun sebelum dan setelah unix epoch.
    > - ISODate merupakan representasi waktu yang digunakan oleh MongoDB
    > - Date ini kompatibel dengan Date di JavaScript
    > - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date 

**[⬆ back to top](#top)**

# 08 Insert Document
[![Video dari youtube](http://img.youtube.com/vi/WRK_jXywV1Y/0.jpg)](http://www.youtube.com/watch?v=WRK_jXywV1Y)

+ **Apa itu Insert Document ??**
    > - Untuk menyimpan data ke MongoDB, kita perlu membuat document dalam bentuk JSON
    > - Field _id tidak wajib dimasukkan, jika kita tidak memasukkan field _id, maka secara otomatis MongoDB akan membuat _id baru secara random dengan tipe data ObjectId
    > - Atau kita juga bisa secara eksplisit membuat ObjectId baru dengan menggunakan perintah “new ObjectId()”

+ Insert Document Function
    Function | Keterangan
    --- | ---
    `db.<collection>.insertOne(document)`  | Menambah dokumen ke collection
    `db.<collection>.insertMany(array<document>)`  | Menambah semua dokumen di array ke collection 
    `db.<collection>.insert(document / array)`  | Menambah satu document atau banyak dokumen
**[⬆ back to top](#top)**

# 09 Query Document
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
**[⬆ back to top](#top)**

# 10 Comparison Query Operator
[![Video dari youtube](http://img.youtube.com/vi/M3Ho4djinHE/0.jpg)](http://www.youtube.com/watch?v=M3Ho4djinHE)

**Comparison Operator** [:link:docs](https://docs.mongodb.com/manual/reference/operator/query-comparison/)
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

**[⬆ back to top](#top)**

# 11 Logical Query Operator
[![Video dari youtube](http://img.youtube.com/vi/9bwQA68o7nQ/0.jpg)](http://www.youtube.com/watch?v=9bwQA68o7nQ)

**Logical Operator** [:link:docs](https://docs.mongodb.com/manual/reference/operator/query-logical/)
Operator | Keterangan
--- | ---
`$and` | Menggabungkan query dengan operasi AND, mengembalikan document jika semua kondisi benar
`$or` | Menggabungkan query dengan operasi OR, mengembalikan document jika salah satu kondisi benar
`$nor` | Menggabungkan query dengan operasi NOR, mengembalikan document yang gagal di semua kondis
`$not` | Membalikkan kondisi, mengembalikan document yang tidak sesuai kondisi

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

**[⬆ back to top](#top)**

# 12 Element Query Operator
[![Element Query Operator](http://img.youtube.com/vi/Qm5PHB0ZAXw/0.jpg)](http://www.youtube.com/watch?v=Qm5PHB0ZAXw)  

**Element Operator** [:link:docs](https://docs.mongodb.com/manual/reference/operator/query-element/)
  | Operator        | Keterangan                                                  | 
  | --------------- |-----------------------------------------------------------|
  | `$exists`         | Mencocokkan document yang memiliki field tersebut           |
  | `$type`           | Mencocokkan document yang memiliki type field tersebut      | 


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


**[⬆ back to top](#top)**

# 13 Evaluation Query Operator
[![Video dari youtube](http://img.youtube.com/vi/MyM_Qa4mCGM/0.jpg)](http://www.youtube.com/watch?v=MyM_Qa4mCGM)

+ **Evaluation Operator** [:link:docs](https://docs.mongodb.com/manual/reference/operator/query-evaluation/)
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

**[⬆ back to top](#top)**

# 14 Array Query Operator
[![Video dari youtube](http://img.youtube.com/vi/XG3-0TdxuGI/0.jpg)](http://www.youtube.com/watch?v=XG3-0TdxuGI)

+ **Array Operator** [:link:docs](https://docs.mongodb.com/manual/reference/operator/query-array/)
    Operator | Keterangan
    --- | ---
    `$all` | Mencocokkan array yang mengandung elemen-elemen tertentu
    `$elemMatch` | Mengambil document jika tiap element di array memenuhi kondisi tertentu
    `$size` | Mengambil document jika ukuran array sesuai 

+ sebelum di praktekan mari insert produk dulu :
    ~~~ javascript
    //  insert products baru yang memiliki field tags array
    db.products.insertMany([
        {
            _id: 6,
            name: "Logitech M235 Wireless Mouse",
            price: new NumberLong(175000),
            category: "laptop",
            tags: [
                "logitech", "mouse", "accessories"
            ]
        },
        {
            _id: 7,
            name: "Havit Cooler Pad Gaming 5Fan Blue led F2082",
            price: new NumberLong(200000),
            category: "laptop",
            tags: [
                "cooler", "laptop", "accessories", "fan"
            ]
        },
        {
            _id: 8,
            name: "Samsung LC24F390FHEXXD Curved Monitor ",
            price: new NumberLong(1750000),
            category: "computer",
            tags: [
                "samsung", "monitor", "computer"
            ]
        }
    ]);
    ~~~


+ `$all` --> Mencocokkan array yang mengandung elemen-elemen tertentu, Jika lebih dari satu element maka akan di baca AND
    - syntax `$all` [:link:docs](https://docs.mongodb.com/manual/reference/operator/query/all/)
        ~~~ javascript
        db.collection.find({
            field: {
                $all: ["value"] //jika lebih dari 1 maka AND bukan OR
            }
        });
        ~~~
    - Contoh menggunakan  `$all`: 
        ~~~ javascript
        /**Mencari produk di field tag yang mengandung element 'samsung' DAN 'monitor'
         * SQL : select * from products where (tags = "samsung" and tags = "monitor")
        */
        db.products.find({
            tags: {
                $all: ["samsung", "monitor"] //AND
            }
        });
        ~~~

+ `$elemMatch` --> Mengambil document jika tiap element di array memenuhi kondisi tertentu (lebih fleksibel gais)
    - syntax `$elemMatch` [:link:docs](https://docs.mongodb.com/manual/reference/operator/query/elemMatch/)
        ~~~ javascript
        db.collection.find({
            fields: {
                $elemMatch: {
                    // quary1,
                    // quary 2
                }
            }
        });
        ~~~
    - Contoh menggunakan  `$elemMatch`: 
        ~~~ javascript
        /**Mencari produk di field tag yang mengandung element 'samsung' ATAU 'monitor'
        * SQL : select * from products where tags in ("samsung",  "logitect")
        */
        db.products.find({
            tags: {
                $elemMatch: {
                    $in: ["samsung", "logitech"] //OR
                }
            }
        });
        ~~~

+ `$size` --> Mengambil document jika ukuran array sesuai
    - syntax `$size`: [:link:docs](https://docs.mongodb.com/manual/reference/operator/query/size/)
        ~~~ javascript
        db.products.find({
            fields: {
                $size: 1 // length
            }
        });
        ~~~
    - Contoh menggunakan  `$size`: 
        ~~~ javascript
        /**Menampilkan field tags yang mempunyai array sebanyak 3 element
        * SQL :select * from products where size(tags) = 3
        */
        db.products.find({
            tags: {
                $size: 3
            }
        });
        ~~~

**[⬆ back to top](#top)**

# 15 Projection Operator
[![Video dari youtube](http://img.youtube.com/vi/XLkZI244vnM/0.jpg)](http://www.youtube.com/watch?v=XLkZI244vnM)

**Apa itu Projection ?**
> - Pada function find, terdapat parameter kedua setelah query, yaitu projection
> - Projection adalah memilih field mana yang ingin kita ambil atau hide
> - `db.<collection>.find(query, projection)`

- syntax Projection [:link:docs](link) 
    ~~~ javascript
    db.collection.find({
        // query
    },{
        field1: 1, // include
        field2: 0 // hide
    })
    ~~~

- **Projection Operator** [:link:docs](https://docs.mongodb.com/manual/reference/operator/projection/)
Operator | Keterangan
    --- | ---
    `$` | Limit array hanya mengembalikan data pertama yang match dengan array operator
    `$elemMatch` | Limit array hanya mengembalikan data pertama yang match dengan kondisi query
    `$meta` | Mengembalikan informasi metadata yang didapat dari setiap matching document
    `$slice` | Mengontrol jumlah data yang ditampilkan pada array


+ `$` --> Limit array hanya mengembalikan data pertama yang match dengan array operator
    - Syntax Operator `$`
        ~~~ javascript
        db.collection.find({
            field: {
                $elemMatch: {
                    //query
                }
            }
        }, {
            "field.$": 1
        });
        ~~~

    - Contoh menggunakan Operator `$`
        ~~~ javascript
        /**Menampilkan semua produk yang ada field 'name' dan 'category'
        * pasti yg di tampilkan hanya field 'name' dan 'category' saja
        * field lainnya seperti 'price', 'tags' dll tidak akan di tampilkan cuy.
        * SQL : select _id, name, category from products
        */
        // 
        db.products.find({}, {
            name: 1,
            category: 1
        });

        /**Menampilkan semua produk kecuali yang tetapi field 'tags' tidak akan di tampilkan
        * semua field akan ditampilkan kecuali 'tags'
        * SQL : select _id, name, category, price from products
        */
        // 
        db.products.find({}, {
            tags: 0
        });


        /**menampilkan semua produk yang memiliki field tags aja
        * yang mengandung element 'samsung' ATAU 'logitech'
        * dan yang di tampikan hanya field : name, category, price. dan tags
        * SQL : select _id, name, category, price, tags[first] from products where tags in ("samsung", "logitech")
        */
        // 
        db.products.find({
            tags: {
                $elemMatch: {
                    $in: ["samsung", "logitech"]
                }
            }
        }, {
            name: 1,
            category: 1,
            price: 1,
            "tags.$": 1 //Akan di ambil tags yang pertama aja, sisanya gak akan di ambil
        });
        ~~~

+ `elemMatch` --> Limit array hanya mengembalikan data pertama yang match dengan kondisi query
    - Syntax Operator `elemMatch`
        ~~~ javascript
        db.collection.find({}, {
             field: {
                $elemMatch: {
                    //query
                }
            }
        });
        ~~~

    - Contoh menggunakan Operator `elemMatch`
        ~~~ javascript
        /**menampilkan semua produk
        * tetapi yang ditampilkan/include hanya field : name, category, price dan
        * field tags hanya di tampilkan yang mengandung element 'samsung' ATAU 'logitech'
        * SQL : select _id, name, category, price, tags(in ("samsung", "logitech")) from products
        */
        // 
        db.products.find({}, {
            name: 1,
            category: 1,
            price: 1,
            tags: {
                $elemMatch: {
                    $in: ["samsung", "logitech"]
                }
            }
        })
        ~~~

+ `meta` --> Mengembalikan informasi metadata yang didapat dari setiap matching document
    - Syntax Operator `meta`
        ~~~ javascript
        db.products.find({
            $text: {
                $search: "query"
            }
        },{
            score: {
                $meta: "textScore"
            }
        })
        ~~~

    - Contoh menggunakan Operator `meta`
        ~~~ javascript
        /**Menampilkan produk yang mengandung kata 'monitor'
        * dan cek scorenya.
        * Score paling tinggi adalah 1
        * SQL : select *, score from products where $search like "monitor"
        */
        // 
        db.products.find({
            $text: {
                $search: "monitor"
            }
        },{
            score: {
                $meta: "textScore"
            }
        })
        ~~~

+ `slice` --> Mengontrol jumlah data yang ditampilkan pada array
    - Syntax Operator `slice`
        ~~~ javascript
        db.collection.find({
            // query
        }, {
            field: {
                $slice: 2 // slice size
            }
        });
        ~~~

    - Contoh menggunakan Operator `slice`
        ~~~ javascript
        /**Menampilkan semua produk 
        * tetapi field 'tags' hanya di ambil 2 element urutan dari depan
        * SQL : select _id, name, price, category, tags[0,2] from products
        */
        // 
        db.products.find({}, {
            tags: {
                $slice: 2
            }
        });


        /**Menampilkan semua produk 
        * tetapi field 'tags' hanya di ambil 2 element urutan dari belakang
        * SQL : select _id, name, price, category, tags[last 2] from products
        */
        // 
        db.products.find({}, {
            tags: {
                $slice: -2
            }
        });


        /**Menampilkan semua produk 
        * tetapi field 'tags' hanya di ambil di index 1 dan di tampikan 1 element
        * SQL : select _id, name, price, category, tags[from, limit] from products
        */
        // 
        db.products.find({}, {
            tags: {
                $slice: [1, 1] // [index, brapa banyak]
            }
        });
        ~~~








**[⬆ back to top](#top)**

# 16 Query Modifier
[![Video dari youtube](http://img.youtube.com/vi/NhnCwldKSQM/0.jpg)](http://www.youtube.com/watch?v=NhnCwldKSQM)

> **Apa iitu Quary Modifier ??**
> - Query Modifier adalah *memodifikasi hasil query* yang telah kita lakukan
> - Contoh yang sering kita lakukan seperti, mengubah query menjadi jumlah data, membatasi jumlah data dengan paging, dan lain-lain
> - Untuk memodifikasi hasil query, kita bisa menambahkan function query modifier setelah menggunakan function `find`

Operator | Keterangan
--- | ---
`count()` | Mengambil jumlah data hasil query
`limit(size)` | Membatasi jumlah data yang didapat dari query
`skip(size)` | Menghiraukan data pertama hasil query sejumlah yang ditentukan
`sort(query)` | Mengurutkan hasil data query

doc --> https://docs.mongodb.com/manual/reference/method/js-cursor/

- Lihat contoh berikut ini :
    ~~~ javascript
    /**menampilkan berapa jumlah data yang data dicollection produk
     * akan di tampilkan angka, misalnya 3, 8
     * SQL :
     */
    // select count(*) from products
    db.products.find({}).count()


    /**menampilkan semua data produk sebanyak 4 
     * SQL :
     */
    // select * from products limit 4
    db.products.find({}).limit(4)


    /** tampilkan semua data produk urutan 2 pertama tidak di tampilkan
     * SQL :
     */
    // select * from products offset 2
    db.products.find({}).skip(2)


    /**tampilkan semua data produk sebanyak 4 produk dan lewati 2 urutan pertama
     * SQL :
     */
    // select * from products limit 4 offset 2
    db.products.find({}).limit(4).skip(2)


    /** tampilkan semua data produk 
     * field 'name' urutkan asc (a-z) dan
     * field 'category' urukan desc (z-a)
     * SQL :
     */
    // select * from products order by name asc, category desc
    db.products.find({}).sort({
        name: 1, //asc
        category: -1 //desc
    })
    ~~~
**[⬆ back to top](#top)**

# 17 Update Document
[![Video dari youtube](http://img.youtube.com/vi/HC44ffHosYo/0.jpg)](http://www.youtube.com/watch?v=HC44ffHosYo)

+ Apa itu ?
    >- Sama seperti database lainnya, di MongoDB juga kita bisa mengubah document yang sudah kita insert ke collection
    >- Namun berbeda dengan perintah SQL, di MongoDB, untuk mengubah document, kita diberikan beberapa function
    > - Untuk update document, kita bisa menggunakan collection : `db.<collection>.<updateFunction>()`

+ Update Document Function
    Operator | Keterangan
    --- | ---
    `updateOne()` | Mengubah satu document
    `updateMany()` | Mengubah banyak document sekaligus
    `replaceOne()` | Mengubah total satu document dengan document baru

    doc --> https://docs.mongodb.com/manual/reference/method/js-cursor/


+ `updateOne()` --> Mengubah satu document
    - Syntax Function `updateOne()`
        ~~~ javascript
        db.collection.updateOne(
            {}, // filter
            {}, // update
            {} // option
        )
        ~~~

    - Contoh menggunakan Function `updateOne()`
        ~~~ javascript
        /**Misalnya ingin mengupdate atau menambahkan field catagory di colection products _id1
        * SQL : update products set category = "food" where _id = 1
        */
        db.products.updateOne({
            _id: 1
        },{
            $set: {
                category: "food"
            }
        });


        /**update atau menambahkan field catagory di colection products _id2
        * SQL : update products set category = "food" where _id = 2
        */
        db.products.updateOne({
            _id: 2
        },{
            $set: {
                category: "food"
            }
        });
        ~~~

+ `updateMany()` --> Mengubah banyak document sekaligus
    - Syntax Function `updateMany()`
        ~~~ javascript
        db.collection.updateMany(
            {}, // filter
            {}, // update
            {} // option
        )
        ~~~

    - Contoh menggunakan Function `updateMany()`
        ~~~ javascript
        /**menambahkan field 'tags' dengan value food di produk yang
        * ada di field 'category food' DAN yg belum memiliki field 'tags'
        * SQL : update products set tags = ["food"] where category = "food" and tags is null
        */
        db.products.updateMany({
            $and: [
                {
                    category :{
                        $eq: "food"
                    }
                },
                {
                    tags: {
                        $exists: false
                    }
                }
            ]
        }, {
            $set: {
                tags: ["food"]
            }
        })


        /**Menambahkan field 'wrong' ke semua produk
        * SQL : update products set wrong = "wrong"
        */
        db.products.updateMany({}, [
            {
                $set: {
                    wrong: "wrong"
                }
            }
        ]); 


        /**Menghapus field 'wrong' di semua produk
        * SQL : update products set wrong = null
        */
        db.products.updateMany({}, [
            {
                $set: {
                    wrong: null
                }
            }
        ]);
        db.products.updateMany({}, [
            {
                $unset: [ "wrong" ] 
            }
        ]);
        ~~~

+ `replaceOne()` --> Mengubah total satu document dengan document baru
    - Syntax Function `replaceOne()`
        ~~~ javascript
        db.collection.replaceOne(
            {}, // filter
            {}, // replacement
            {} // option
        )
        ~~~

    - Contoh menggunakan Operator `replaceOne()`
        ~~~ javascript
        /**Menimpa semua isi data produk di _id: 9
        * semua data akan berubah baru
        * benar-benar menimpah bulat-bulat tanpa ampun cuy...
        * SQL :  replace document with id 9
        */
        db.products.replaceOne({
            _id: 9
        }, {
            name: "Adidas Pulseboost HD Running Shoes Sepatu lari Pria",
            price: new NumberLong(1100000),
            category: "shoes",
            tags: [
                "adidas", "shoes", "running"
            ]
        });
        ~~~


**[⬆ back to top](#top)**

# 18 Field Update Operator
[![Video dari youtube](http://img.youtube.com/vi/SW1CzT561xU/0.jpg)](http://www.youtube.com/watch?v=SW1CzT561xU)

+ Apa itu ?
    > - Sebelumnya kita sudah tau kalo untuk update document di MongoDB kita bisa menggunakan operator $set dan $unset
    > - Namun sebenarnya masih banyak operator yang bisa kita gunakan

+ Update Document Function [:link:docs](https://docs.mongodb.com/manual/reference/operator/update-field/)
    Operator | Keterangan
    --- | ---  
    `$set` | Mengubah nilai field di document
    `$unset` | Menghapus field di document
    `$rename` | Mengubah nama field di document
    `$inc` | Menaikan nilai number di field sesuai dengan jumlah tertentu 
    `$currentDate` | Mengubah field menjadi waktu saat ini


+ sytax operatornya :
    - Syntax Operator `$set` dan `$unset` :
        ~~~ javascript
        // $set
        db.collection.update({
            // query
        },{
            $set: {
                field1: "value",
                field2: "value"
            }
        });

        // $unset
        db.collection.update({
            // query
        },{
            $unset: {
                field1: "value",
                field2: "value"
            }
        });
        ~~~

    - `$rename` --> Mengubah nama field di document
        ~~~ javascript
        // syntax
        db.collection.update({
            // query
        },{
            $rename: {
                field1: "newName1",
                field2: "newName1"
            }
        });

        /** contoh :
         * ingin merubah field 'name' menjadi 'full_name'
         * SQL : alter table customers change name full_name
        **/
        db.customers.updateMany({}, {
            $rename: {
                name: "full_name"
            }
        })
        ~~~

    - `$inc` --> Menaikan nilai number di field sesuai dengan jumlah tertentu 
        ~~~ javascript
        // syntax
        db.collection.updateMany({
            // query
        },{
            $incr: {
                field1: 1, // inmcrement
                field2: -1 // dcrement
            }
        });

        /** contohnya :
         * ingin menaikan stock semua produk menjadi 10
         * SQL : update products set stock = stock + 10
         */
        db.products.updateMany({}, {
            $inc: {
                stock: 10 // maka semua stock produk akan naik 10
            }
        });

        ~~~

    - `$currentDate` --> Mengubah field menjadi waktu saat ini
        ~~~ javascript
        // syntax
        db.collection.update({
            // query
        },{
            $currentDate: {
                field1: {
                    $type: "date"
                }
                field2: {
                    $type: "timestamp"
                }
            }
        });

        /** Contohnya :
         * ingin merubah waktu di saat ini juga
         * SQL :update products set lastModifiedDate = current_date()
         */
        db.products.updateMany({}, {
            $currentDate: {
                lastModifiedDate: {
                    $type: "date"
                }
            }
        });
        ~~~

  





  **[⬆ back to top](#top)**

# 19 Array Update Operator
[![Video dari youtube](http://img.youtube.com/vi/hKk-E2_GzBw/0.jpg)](http://www.youtube.com/watch?v=hKk-E2_GzBw)

**Apa itu ?**
> - Secara default, saat kita mengubah field dengan tipe array, maka seluruh array akan diubah
> - Kadang  kita ingin menambah, atau hanya mengubah data array tanpa harus mengubah seluruh field array
> - Hal ini bisa dilakukan di MongoDB

1. **Array Update Operator** [:link:docs](https://docs.mongodb.com/manual/reference/operator/update-array/#update-operators)
    Operator | Keterangan | Contoh
    --- | ---  | ---
    `$` | Mengupdate data array pertama sesuai kondisi query | [cek](#1911)
    `$[]` | Mengupdate semua data array sesuai kondisi query | [cek](#1912)
    `$[<identifier>]` | Mengupdate semua data array yang sesuai kondisi arrayFilters | [cek](#1913)
    `<index>` | Mengupdate data array sesuai dengan nomor index | [cek](#1914)
    `$addToset` | Menambahkan value ke array, dihiraukan jika sudah ada | [cek](#1915)
    `$pop` | Menghapus element pertama (-1) atau terakhir (1) array | [cek](#1916)
    `$pull` | Menghapus semua element di array yang sesuai kondisi | [cek](#1917)
    `$push` | Menambahkan element ke array | [cek](#1918)
    `$pullAll` | Menghapus semua element di array | [cek](#1919)


2. **Array Update Operator Modifier** [:link:docs](https://docs.mongodb.com/manual/reference/operator/update-array/#update-operator-modifiers)
    Operator | Keterangan | Contoh
    --- | --- | ---  
    `$each` | Digunakan di $addToSet dan $push, untuk menambahkan multiple element | [cek](#1921)
    `$position` | Digunakan di $push untuk mengubah posisi menambahkan data | [cek](#1922)
    `$slice` | Digunakan di $push untuk menentukan jumlah maksimal data array | [cek](#1923)
    `$sort` | Digunakan untuk mengurutkan array setelah operasi $push | [cek](#1924)



+ **1.1 `$` --> Mengupdate data array pertama sesuai kondisi query** [:link:docs](https://docs.mongodb.com/manual/reference/operator/update/positional/)
  <a name="1911"></a>
    - Syntax Operator `$`
        ~~~ javascript
        db.collection.updateMany({ 
            field: "value"
        }, {
            $operator: {
                "field.$": "value"
            }
        });
        ~~~

    - Contoh menggunakan Operator `$`
        ~~~ javascript
        /**untuk praktekan, kita Update/tambahkan dahulu field ratings di semua produk
        * SQL : update products set ratings = [90, 80, 70]
        */
        db.products.updateMany({}, {
            $set: {
                ratings: [90, 80, 70]
            }
        });


        /**Merubah rating pertama 90 menjadi 100
        * SQL : update first element of array, query must include array fields
        */
        db.products.updateMany({ 
            ratings: 90
        }, {
            $set: {
                "ratings.$": 100
            }
        });

        ~~~



+ **1.2 `$[]` --> Mengupdate semua data array sesuai kondisi query** [:link:docs](https://docs.mongodb.com/manual/reference/operator/update/positional-all/)
  <a name="1912"></a>
    - Syntax Operator `$[]`
        ~~~ javascript
        db.collection.updateMany({ 
            // query
        }, {
            $operator: {
                "field.$[]": "value"
            }
        });
        ~~~

    - Contoh menggunakan Operator `$[]`
        ~~~ javascript
        /**Merubah semua isi field 'rating' menjadi 100
        * contohnya isinya : 90, 80, 70
        * maka setelah di set akan berubah : 100, 100, 100
        * SQL : update all element of array
        */
        db.products.updateMany({}, {
            $set: {
                "ratings.$[]": 100
            }
        })
        ~~~

+ **1.3 `$[<identifier>]` --> Mengupdate semua data array yang sesuai kondisi arrayFilters** [:link:docs](https://docs.mongodb.com/manual/reference/operator/update/positional-filtered/)
  <a name="1913"></a>
    - Syntax Operator `$[<identifier>]`
        ~~~ javascript
        db.products.updateMany({}, {
            // query
        }, {
            $operator: {
                "field.$[element]" : "value"
            }
        },{
            arrayFilters: [ 
                { 
                    element: {  //opsinya disini
                        $operator: "value"
                    } 
                } 
            ]
        })
        ~~~

    - Contoh menggunakan Operator `$[<identifier>]`
        ~~~ javascript
        /**contohnya ingin update nilai yg ada di field 'rating' menjadi 100 khusus
        * untuk rating yg di atas 80 saja, kalo di bawah 80 maka tidak di update.
        * SQL : update element of array based on arrayFilters
        */
        db.products.updateMany({}, {
            $set: {
                "ratings.$[element]" : 100 //nilai updatenya
            }
        },{
            arrayFilters: [ 
                { 
                    element: {  //opsinya disini
                        $gte: 80
                    } 
                } 
            ]
        })
        ~~~

+ **1.4 `$<index>` --> Mengupdate data array sesuai dengan nomor index** 
  <a name="1914"></a>
    - Syntax Operator `$<index>`
        ~~~ javascript
        db.collection.updateMany({
            // query
        }, {
            $set: {
                "field.<index>": "value"
            }
        });
        ~~~

    - Contoh menggunakan Operator `$<index>`
        ~~~ javascript
        /**update index ke-1 dan kedua di semua field 'rating'
        * SQL : update element of array with given index
        */
        db.products.updateMany({}, {
            $set: {
                "ratings.0": 50, //index ke-1
                "ratings.1": 60 // index ke-2
            }
        });
        ~~~

+ **1.5 `$addToset` --> Menambahkan value ke array, dihiraukan jika sudah ada** [:link:docs](https://docs.mongodb.com/manual/reference/operator/update/addToSet/)
  <a name="1915"></a>
    - Syntax Operator `$addToset`
        ~~~ javascript
        db.collection.updateOne({
            // query
        }, {
            $addToSet: {
                field: "value"

            }
        });
        ~~~

    - Contoh menggunakan Operator `$addToset`
        ~~~ javascript
        /**menambahkan field tags ke id1 dengan value tags 'populer'
        * otomatis akan update jika datanya belum ada, 
        * jika sudah ada maka tidak akan bertambah cuy...
        * SQL : add "popular" to array if not exists
        */
        db.products.updateOne({
            _id: 1
        }, {
            $addToSet: {
                tags: "popular"

            }
        });
        ~~~

+ **1.6 `$pop` --> Menghapus element pertama (-1) atau terakhir (1) array** [:link:docs](https://docs.mongodb.com/manual/reference/operator/update/pop/)
  <a name="1916"></a>
    - Syntax Operator `$pop`
        ~~~ javascript
        db.collection.updateMany({
            //array
        }, {
            $pop: {
                field: -1 // element pertama : -1, element terakhir : 1
            }
        });
        ~~~

    - Contoh menggunakan Operator `$pop`
        ~~~ javascript
        /**Menghapus data ratings element yg pertama
        * SQL : remove first element of array
        */
        db.products.updateMany({}, {
            $pop: {
                ratings: -1 // element pertama : -1, element terakhir : 1
            }
        });
        ~~~

+ **1.7 `$pull` --> Menghapus semua element di array yang sesuai kondisi** [:link:docs](https://docs.mongodb.com/manual/reference/operator/update/pull/)
  <a name="1917"></a>
    - Syntax Operator `$pull`
        ~~~ javascript
        db.collection.updateMany({
            // quary
        }, {
            $pull: {
                field: {
                    $operator: "value"
                }
            }
        })
        ~~~

    - Contoh menggunakan Operator `$pull`
        ~~~ javascript
        /**Menghapus semua rating yang diatas 80
        * SQL : remove all element where ratings >= 80
        */
        db.products.updateMany({}, {
            $pull: {
                ratings: {
                    $gte: 80
                }
            }
        })
        ~~~

+ **1.8 `$push` --> Menambahkan element ke array** [:link:docs](https://docs.mongodb.com/manual/reference/operator/update/push/)
  <a name="1918"></a>
    - Syntax Operator `$push`
        ~~~ javascript
        db.products.updateMany({
            // quary
        }, {
            $push: {
                field: "value"
            }
        })
        ~~~

    - Contoh menggunakan Operator `$push`
        ~~~ javascript
        /**menambahkan rating 100 di semua produk 
        * akan bertambah paling akhir atau idex terakhir
        * SQL : add 100 to ratings
        */
        db.products.updateMany({}, {
            $push: {
                ratings: 100
            }
        })
        ~~~

+ **1.9 `$pullAll` --> Menghapus semua element di array** [:link:docs](https://docs.mongodb.com/manual/reference/operator/update/pullAll/)
  <a name="1919"></a>
    - Syntax Operator `$pullAll`
        ~~~ javascript
        db.products.updateMany({}, {
            $pullAll: {
                field: ["value"]
            }
        })
        ~~~

    - Contoh menggunakan Operator `$pullAll`
        ~~~ javascript
        /**menhapus rating 100 dan juga 40
        * SQL : remove element 100 
        */
        db.products.updateMany({}, {
            $pullAll: {
                ratings: [100, 40]
            }
        })
        ~~~


+ **2.1 `$each` --> Digunakan di `$addToSet` dan `$push`, untuk menambahkan multiple element** [:link:docs](https://docs.mongodb.com/manual/reference/operator/update/each/)
  <a name="1921"></a>
    - Syntax :
        ~~~ javascript
        db.collection.updateMany({
            // quary
        },{
            $operator: {
                field: {
                    $each: ["value1", "value2"]
                }
            }
        })
        ~~~

    - Contoh :
        ~~~ javascript
        /**menambahkan rating di semua produk sebanyak 3 element
        * nilai rating 100, 200, 300
        * SQL : add 100, 200, 300 to ratings
        */
        db.products.updateMany({},{
            $push: {
                ratings: {
                    $each: [100, 200, 300]
                }
            }
        })


        /**menambahkan tags baru sebanyak 2 di semua produk
        * tetapi tags nya harus unix 
        * jika duplicat maka akan di skip
        * SQL : add trending, popular to tags
        */
        db.products.updateMany({},{
            $addToSet: {
                tags: {
                    $each: ["trending", "popular"]
                }
            }
        })

        ~~~

+ **2.2 `$position` --> Digunakan di `$push` untuk mengubah posisi menambahkan data** [:link:docs](https://docs.mongodb.com/manual/reference/operator/update/position/)
  <a name="1922"></a>
    - Syntax :
        ~~~ javascript
        db.collection.updateMany({
            // query
        },{
            $push: {
                field: {
                    $each: ["value"],
                    $position: 1
                }
            }
        })
        ~~~

    - Contoh :
        ~~~ javascript
        /**menambahkan tags 'hot' di semua produk di posisi index ke-1
        * akan masuk ke element kedua index ke 1
        * SQL : add hot in posititon 1
        */
        db.products.updateMany({},{
            $push: {
                tags: {
                    $each: ["hot"],
                    $position: 1
                }
            }
        })
        ~~~

+ **2.3 `$slice` --> Digunakan di `$push` untuk menentukan jumlah maksimal data array** [:link:docs](https://docs.mongodb.com/manual/reference/operator/update/slice/)
  <a name="1923"></a>
    - Syntax :
        ~~~ javascript
        db.collection.updateMany({
            // query
        },{
            $push: {
                ratings: {
                    $each: ["value1", "value2"],
                    $slice: 1
                }
            }
        })
        ~~~

    - Contoh :
        ~~~ javascript
        /**menambahkan element rating maksimal 2
        * dan ambil 2 dari urutan paling belakang
        * data akan tertimpa jadi baru
        * SQL : add all element, but limit with slice
        */
        db.products.updateMany({},{
            $push: {
                ratings: {
                    $each: [150, 200, 300, 400, 500],
                    $slice: -2 // max 2, mengambil urutan paling belakang : 400, 500
                }
            }
        })
        ~~~

+ **2.4 `$sort` --> Digunakan untuk mengurutkan array setelah operasi `$push`** [:link:docs](https://docs.mongodb.com/manual/reference/operator/update/sort/)
  <a name="1924"></a>
    - Syntax :
        ~~~ javascript
        db.collection.updateMany({
            // query
        },{
            $push: {
                field: {
                    $each: [300, 400, 500],
                    $sort: 1
                }
            }
        })
        ~~~

    - Contoh :
        ~~~ javascript
        /**Menambahkan element rantings baru secara desending
        * SQL : add all element, and sort desc
        */
        db.products.updateMany({},{
            $push: {
                ratings: {
                    $each: [300, 400, 500],
                    $sort: -1 // menambahkan data baru desending : 500, 400, 300
                }
            }
        })
        ~~~

**[⬆ back to top](#top)**

# 20 Delete Document
[![Video dari youtube](http://img.youtube.com/vi/qnS4BYHmIIg/0.jpg)](http://www.youtube.com/watch?v=qnS4BYHmIIg)

> **Apa iitu Quary Modifier ??**
> - MongoDB memiliki function yang bisa kita gunakan untuk menghapus document di collection secara permanen
> - Document yang sudah kita hapus, tidak akan bisa dikembalikan lagi

**Delete Document Function** [:link:docs](https://docs.mongodb.com/manual/reference/delete-methods/)
Operator | Keterangan
--- | ---
`db.<collection>.deleteOne(query)` | Menghapus satu document yang sesuai dengan kondisi query
`db.<collection>.deleteMany(query)` | Menghapus banyak document yang sesuai dengan kondisi query

+ **`db.<collection>.deleteOne(query)` --> Menghapus satu document yang sesuai dengan kondisi query** 
    - Syntax :
        ~~~ javascript
        db.customers.deleteOne({
            // query
        });
        ~~~

    - Contoh :
        ~~~ javascript
        // Insert spammer document
        db.customers.insertOne({
            _id: "spammer",
            full_name: "Spammer"
        });

        // Delete document by _id
        db.customers.deleteOne({
            _id: "spammer"
        });

        ~~~

+ **`db.<collection>.deleteMany(query)` --> Menghapus banyak document yang sesuai dengan kondisi query** 
    - Syntax :
        ~~~ javascript
        db.collection.deleteMany({
            //query
        })
        ~~~

    - Contoh :
        ~~~ javascript
        // Insert many spammer documents
        db.customers.insertMany([
            {
                _id: "spammer1",
                full_name: "Spammer1"
            },
            {
                _id: "spammer2",
                full_name: "Spammer2"
            },
            {
                _id: "spammer3",
                full_name: "Spammer3"
            }
        ]);

        // Delete many documents
        db.customers.deleteMany({
            _id: {
                $regex: "spammer"
            }
        })
        ~~~
**[⬆ back to top](#top)**

# 21 Bulk Write Operation
[![Video dari youtube](http://img.youtube.com/vi/zmOLV-KBH4k/0.jpg)](http://www.youtube.com/watch?v=zmOLV-KBH4k)

> **Apa iitu Quary Modifier ??**
> - Komunikasi antara aplikasi dengan database biasanya dilakukan secara request-response
> - Artinya tiap perintah yang ingin kita kirimkan dari aplikasi ke database, akan diresponse secara langsung oleh database
> - Proses tersebut akan sangat lambat, jika kita menghadapi kasus harus memanipulasi data besar secara langsung. Misal upload data dari file dengan jumlah jutaan ke dalam database.
> - MongoDB mendukung Bulk Write Operation, yaitu operasi bulk yang dalam satu request, kita bisa mengirim banyak perintah
> - Fitur ini cocok pada kasus jika kita ingin melakukan operasi bulk atau batch secara banyak sekaligus

+ **Bulk Write Function** [:link:docs](https://docs.mongodb.com/manual/core/bulk-write-operations/)
    Function | Keterangan 
    --- | ---
    `db.<collection>.insertMany()` | Insert document secara banyak sekaligus
    `db.<collection>.updateMany()` | Update document secara banyak sekaligus
    `db.<collection>.deleteMany()` | Delete document secara banyak sekaligus
    `db.<collection>.bulkWrite()` | Melakukan operasi write (insert, update, delete) banyak secara sekaligus

+ Supported Bulk Write Operation [:link:docs](https://docs.mongodb.com/manual/reference/method/db.collection.bulkWrite/)
    - insertOne
    - updateOne
    - updateMany
    - replaceOne
    - deleteOne
    - deleteMany

+  **`db.<collection>.bulkWrite()` | Melakukan operasi write (insert, update, delete) banyak secara sekaligus**
    - Syntax :
        ~~~ javascript
        db.customers.bulkWrite([
            {
                // Operation 1
            },
            {
                // Operation 2
            },            
            {
                // Operation 3
            }
        ])
        ~~~

    - Contoh :
        ~~~ javascript
        db.customers.bulkWrite([
            {
                insertOne: {
                    document: {
                        _id: "eko",
                        full_name: "Eko"
                    }
                }
            },
            {
                insertOne: {
                    document: {
                        _id: "kurniawan",
                        full_name: "Kurniawan"
                    }
                }
            },
            {
                updateMany: {
                    filter: {
                        _id: {
                            $in: ["eko", "kurniawan", "khannedy"]
                        }
                    },
                    update: {
                        $set: {
                            full_name: "Eko Kurniawan Khannedy"
                        }
                    }
                }
            }
        ])
        ~~~

**[⬆ back to top](#top)**

# 22 Schema Validation
[![Video dari youtube](http://img.youtube.com/vi/m1wnqoDJmTs/0.jpg)](http://www.youtube.com/watch?v=m1wnqoDJmTs)

+ **Apa itu ??**
    - ***Schema Validation***
        > - Pada Relational DB, kita biasanya menambahkan constraint terhadap data yang ada di tabel
        > - Misal, maksimal karakter, Enum string, Not Null, dan lain-lain
        > - Di MongoDB, fitur untuk validasi data lebih canggih dibanding constraint di Relational DB
        > - MongoDB mendungkung Schema Validation menggunakan JSON Schema
    
    - ***Schema Validation***
        > - JSON Schema adalah standar resmi untuk memvalidasi data JSON
        > - Dengan menggunakan JSON Schema, kita bisa memberi batasan, data JSON apa yang valid, 
        > - sehingga bisa dimasukkan ke dalam collection
        > - http://json-schema.org/ 

+ **Syntax Create Collection dengan Validator** [:link:docs](https://docs.mongodb.com/manual/core/schema-validation/)
    - Syntax : 
        ~~~ javascript
        db.createCollection("collection", {
            validator: {
                $jsonSchema: {
                    // json schema
                }
            }
        })
        ~~~

    - Contohnya : 
        ~~~ javascript
        // Create category collection
        db.createCollection("merchants", {
            validationAction: "error",
            validator: {
                $jsonSchema: {
                    bsonType: "object",
                    required: ["name", "balance", "type", "address"],
                    properties: {
                        name: {
                            bsonType: "string",
                            description: "Must be a string"
                        },
                        balance: {
                            bsonType: "long",
                            description: "Must be a long"
                        },
                        type: {
                            enum: ["PREMIUM", "REGULAR"],
                            description: "Can only be one of enum values"
                        },
                        address: {
                            bsonType: "object",
                            required: ["street", "city"],
                            properties: {
                                street: {
                                    bsonType: "string",
                                    description: "Must be a string"
                                },
                                city: {
                                    bsonType: "string",
                                    description: "Must be a string"
                                },
                                country: {
                                    bsonType: "string",
                                    description: "Must be a string"
                                }
                            }
                        }
                    }
                }
            }
        })

        /**Jika sudah buat validator, maka data yg di input harus sesuai validator
         * jika tidak maka akan gagal
         * contohnya berikut ini :
         */

        // Insert valid document
        db.merchants.insertOne({
            _id: "toko1",
            name: "Toko Satu",
            balance: new NumberLong(1000000),
            type: "PREMIUM",
            address: {
                street: "Jalan Raya Belum Jadi",
                city: "Jakarta",
                country: "Indonesia"
            }
        })

        // Inser Invalid document: Name is blank
        db.merchants.insertOne({
            _id: "toko2",
            balance: new NumberLong(1000000),
            type: "PREMIUM",
            address: {
                street: "Jalan Raya Belum Jadi",
                city: "Jakarta",
                country: "Indonesia"
            }
        })

        // Inser Invalid document: Address City is blank
        db.merchants.insertOne({
            _id: "toko2",
            name: "Toko Dua",
            balance: new NumberLong(1000000),
            type: "PREMIUM",
            address: {
                street: "Jalan Raya Belum Jadi",
                country: "Indonesia"
            }
        })


        ~~~
        
+ **Syntax Update Collection dengan Validator** [:link:docs](https://docs.mongodb.com/manual/reference/command/collMod/)
    - Syntax :
        ~~~ javascript
        db.runCommand({
            collMod: "collection",
            validationAction: "error",
            validator: {
                $jsonSchema: {
                    // json schema
                }
            }
        })
        ~~~

    - Contoh :
        ~~~ javascript
        // Add validator to customers collection
        db.runCommand({
            collMod: "customers",
            validationAction: "error",
            validator: {
                $jsonSchema: {
                    bsonType: "object",
                    required: ["full_name"],
                    properties: {
                        full_name: {
                            bsonType: "string",
                            description: "Must be a string"
                        }
                    }
                }
            }
        })
        ~~~





















**[⬆ back to top](#top)**

# 23 Indexes
[![Video dari youtube](http://img.youtube.com/vi/RKtqsv9iQ0g/0.jpg)](http://www.youtube.com/watch?v=RKtqsv9iQ0g)

+ **Apa itu Indexes ??** [:link:docs](https://docs.mongodb.com/manual/indexes/)
    > - Index adalah fitur di MongoDB untuk mengefisienkan proses query. Tanpa Index, MongoDB harus melakukan proses query dengan cara collection scan (mencari keseluruh data dari awal sampai akhir)
    > - Jika terdapat Index pada collection MongoDB, MongoDB bisa menggunakan Index untuk mendapatkan data, tanpa harus melakukan pencarian keseluruh document
    > - Index adalah struktur data khusus yang menyimpan data dalam struktur yang mudah untuk dicari.
    > - Index menyimpan spesifik field, lalu mengurutkan data field tersebut. Hal ini tidak hanya mempermudah ketika proses pencarian, namun mempermudah ketika kita butuh melakukan pencarian dalam bentuk range document (seperti paging).
    > - Secara dasar, Index di MongoDB, cara kerjanya sama seperti Index di Relational DB
    


+ **Create Index Function** [:link:docs](https://docs.mongodb.com/manual/reference/method/db.collection.createIndex/)
    Function | Keterangan
    --- | ---
    `db.<collection>.createIndex()` | Membuat index di collection
    `db.<collection>.getIndexes()` | Melihat semua index di collection
    `db.<collection>.dropIndexes()` | Menghapus index di collection

+ ***Single Field Index*** [:link:docs](https://docs.mongodb.com/manual/core/index-single/)
    > - Secara default, field _id di MongoDB sudah di index secara otomatis, jadi kita tidak perlu membuat index lagi secara manual untuk field _id
    > - MongoDB mendukung penuh pembuatan index di semua field yang ada di document. Dengan begitu, ini bisa mempercepat proses query di MongoDB untuk query terhadap field tersebut

    - syntax :
        ~~~ javascript
        db.collection.createIndex({
            field: 1 // ascending
        });

        db.collection.createIndex({
            field: -1 // descending
        });
        ~~~

+ ***Compound Indexes*** [:link:docs](https://docs.mongodb.com/manual/core/index-compound/)
    > - Jika kita butuh melakukan query terhadap lebih dari satu field, kita juga bisa membuat index terhadap lebih dari satu field, atau disebut Compound Index
    > - MongoDB membatasi pembuatan maksimal field yang bisa dibuat di compound index adalah 32 field
    
    - syntax :
        ~~~ javascript
        db.collection.createIndex({
            field1: 1 // ascending
            field2: -1 // descending
        });
        ~~~

+ ***Indexing Strategy*** [:link:docs](https://docs.mongodb.com/manual/applications/indexes/)
    > - Buat index untuk mendukung performa query
    >    - Gunakan single index, jika kita hanya melakukan query terhadap satu field saja
    >    - Gunakan compound index, jika kita sering melakukan query ke field pertama, atau kombinasi field pertama dan kedua, atau pertama dan kedua dan seterusnya
    > - Buat index untuk mengurutkan hasil query
    > - Sering-seringlah menggunakan function explain() untuk mengecek apakah query kita sudah di optimize dengan index atau belum

+ ***Contoh :***
    ~~~ javascript

    // Buat index di field category di collection produk
    db.products.createIndex({
        category: 1
    });

    // Cara melihat index. Get all indexes in products collection
    db.products.getIndexes();

    // Find products by category (will use index)
    db.products.find({
        category: "food"
    });


    // Debugging query optimization
    /**Untuk mengecek apakah benar menggunakan index
    * Jika sudah di buat index maka hasilnya akan terlihat "IXSCAN"
    * jika belum maka "COLLSCAN" artinya akan mencari data satu2 dan lama cuy
    */
    db.products.find({
        category: "food"
    }).explain();

    db.products.find({}).sort({
        category:1
    }).explain();

    /**Jika membuat index lebih dari 1 maka
    * field 1 --> kena
    * field 1, 2 --> kena
    * field 1, 2, 3 --> kena
    * field 2 --> tidak
    * field 2, 3 --> tidak
    */

    // Create index at price and tags in products collection
    db.products.createIndex({
        stock: 1, // field 1
        tags: 1 // field 2
    });

    // Find products by stock and tags (will use index)
    db.products.find({
        stock: 10,
        tags: "popular"
    });

    // Debugging query optimization
    db.products.find({
        stock: 10
    }).explain();

    db.products.find({
        stock: 10,
        tags: "popular"
    }).explain();
    
    db.products.find({
        tags: "popular"
    }).explain();
    ~~~

**[⬆ back to top](#top)**

# 24 Text Indexes
[![Video dari youtube](http://img.youtube.com/vi/b3TXEbwxnWY/0.jpg)](http://www.youtube.com/watch?v=b3TXEbwxnWY)

**Apa itu Text Indexes ??** [:link:docs](https://docs.mongodb.com/manual/core/index-text/)
> - MongoDB menyediakan text index untuk mendukung pencarian text di tipe data string.
> - Text index tidak hanya bisa digunakan pada field dengan tipe data string, namun juga pada array berisi tipe data `string`

+ Syntax Text Index 
    ~~~ javascript
    db.collection.createIndex({
        field1: "text",
        field2: "text"
    }, {
        weights: {
            field1: 10, // nilai semakin besar akan semakin di prioritaskan
            field2: 5,
        }
    });

    ~~~

- Contoh :
    ~~~ javascript
    // create index text
    db.products.createIndex({
        name: "text",
        category: "text",
        tags: "text"
    }, {
        weights: {
            name: 10, // nilai semakin besar akan semakin di prioritaskan
            category: 5,
            tags: 1
        }
    });


    // search products with text "mie"
    /**ketika sudah di buat index text, maka quary search 
    * akan mencari data yg sdh di index (name, category, tags)
    */
    db.products.find({
        $text: {
            $search: "mie"
        }
    });

    // search products with text "mie" OR "laptop"
    /**jka ada 2 kata di search kayak gini maka di bacanya OR */
    db.products.find({
        $text: {
            $search: "mie laptop" // dibaca : mie OR Laptop
        }
    });

    // search products with text "mie sedap"
    /**nah kalo mau 2 kata di baca 1 maka tambahkan `""` */
    db.products.find({
        $text: {
            $search: '"mie sedap"' // dibaca : mie sedap
        }
    });

    // search products with text "mie" and NOT "sedap"
    /**mencari kata "mie" tetapi tidak boleh ada kata "sedap" */
    db.products.find({
        $text: {
            $search: "mie -sedap" // "mie" yand tidak ada kata "sedap"
        }
    });


    // Debugging query optimization
    db.products.find({
        $text: {
            $search: "mie -sedap"
        }
    }).explain();
    ~~~




**[⬆ back to top](#top)**

# 25 Wildcard Indexes
[![Video dari youtube](http://img.youtube.com/vi/b3TXEbwxnWY/0.jpg)](http://www.youtube.com/watch?v=b3TXEbwxnWY)


**Apa itu Wildcard Indexes ??** [:link:docs](https://docs.mongodb.com/manual/core/index-wildcard/)
> - MongoDB mendukung wildcard index, dimana ini digunakan untuk membuat index terhadap field yang belum diketahui atau field yang sering berubah-ubah
> - Misal contoh kita punya sebuah embedded document dengan tipe field customFields, dimana isi nya bisa bebas sesuai dengan data yang dimasukkan.
> - Agar bisa mendukung proses query yang cepat pada field tersebut, kita bisa menggunakan wildcard index

- Syntax Wildcard Index :
    ~~~ javascript
    db.collection.createIndex({
        "field.$**" : 1 // assending
    });
    ~~~

- Contoh :
    ~~~ javascript
    // membuat wildcard index
    db.customers.createIndex({
        "customFields.$**" : 1
    });
    /**Maka Semua data yg ada di field "customFields" akan ter index
    * jadi gak perlu buat idex satu persatu
    */


    //TESTER :

    // Insert many customers
    db.customers.insertMany([
        {
            _id: "budi",
            full_name: "Budi",
            customFields: {     // semua data di field ini otomatis ter index
                hobby: "Gaming",
                university: "Universitas Belum Ada"
            }
        },
        {
            _id: "joko",
            full_name: "Joko",
            customFields: {
                ipk: 3.2,
                university: "Universitas Belum Ada"
            }
        },
        {
            _id: "rudi",
            full_name: "Rudi",
            customFields: {
                motherName: "Tini",
                passion: "Entepreneur"
            }
        }
    ])

    // Debug wildcard index
    db.customers.find({
        "customFields.passion": "Enterpreneur"
    }).explain();

    db.customers.find({
        "customFields.ipk": 3.2
    }).explain();

    db.customers.find({
        "customFields.hobby": "Gaming"
    }).explain();
    ~~~
**[⬆ back to top](#top)**

# 26 Index Properties
[![Video dari youtube](http://img.youtube.com/vi/b9VXN-WeZAk/0.jpg)](http://www.youtube.com/watch?v=b9VXN-WeZAk)

+ **Apa itu Index Properties ??** [:link:docs](https://docs.mongodb.com/manual/core/index-properties/)
    > - MongoDB mendukung properties di index
    > - Istilah properties di Index mungkin agak sedikit membingungkan, sederhananya adalah menambahkan behaviour atau kemampuan tertentu terhadap index yang kita buat

+ **TTL Index** [:link:docs](https://docs.mongodb.com/manual/core/index-ttl/)
    > - TTL singkatan dari  Time To Live, yaitu waktu untuk hidup
    > - TTL Index digunakan sebagai waktu hidup document di collection, artinya data akan hilang dalam kurun waktu tertentu secara otomatis
    > - TTL Index hanya dapat digunakan di field dengan tipe data Date
    > - Background proses di  MongoDB akan secara regular melakukan penghapusan data secara otomatis
    > - Sayangnya, proses background tersebut berjalan setiap 60 detik sekali
  
  - Syntax :
    ~~~ javascript
    db.collection.createIndex({
        field: 1 // asending
    }, {
        expireAfterSeconds: 10 // setelah 10 detik semua data akan otomatis di hapus
    })
    ~~~

  - Contoh :
    ~~~ javascript
    //[1] Create session collection
    db.createCollection("sessions");

    //[2] Create TTL Index
    db.sessions.createIndex({
        createdAt: 1
    }, {
        expireAfterSeconds: 10
    })

    //[3] Will expire after 10 seconds, but background job run every 60 seconds
    db.sessions.insertOne({
        _id: 1,
        session: "Session 1",
        createdAt: new Date()
    });

    // setelah 60 detik, data yg di insert di collection "sessions" akan Hilang
    db.sessions.find()
    ~~~

+ **Unique Index** [:link:docs](https://docs.mongodb.com/manual/core/index-unique/)
    > - Unique Index memastikan bahwa field-field di index tersebut tidak menyimpan data duplicate.
    > - Contohnya, di MongoDB, field _id secara otomatis merupakan unique index, sehingga kita tidak bisa membuat document dengan field _id yang sama

  - Syntax :
    ~~~ javascript
    db.collection.createIndex({
        field: 1 // asending
    }, {
        unique: true // data yg masuk tidak boleh duplicate
    })
    ~~~

  - Contoh :
    ~~~ javascript
    // Create unique index
    db.customers.createIndex({
        email: 1
    }, {
        unique: true
    });


    // insert 
    db.customers.insertOne({
        _id: "123",
        full_name : "contoh",
        email: "contoh@example.com"
    });

    /** ketika ada email yang sama "contoh@example.com"
     * maka akan gagal di insert
    */
    // failed duplicate email
    db.customers.insertOne({
        _id: "gagal",
        full_name : "Gagal",
        email: "eko@example.com"
    });

    ~~~

**[⬆ back to top](#top)**

# 27 Transaction
[![Video dari youtube](http://img.youtube.com/vi/RP5Q7u52dZ4/0.jpg)](http://www.youtube.com/watch?v=RP5Q7u52dZ4)
**[⬆ back to top](#top)**

# 28 Security
[![Video dari youtube](http://img.youtube.com/vi/p_5XexsCLNw/0.jpg)](http://www.youtube.com/watch?v=p_5XexsCLNw)

+ **Apa itu Security ??** [:link:docs](https://docs.mongodb.com/manual/tutorial/enable-authentication/)
    > - Secara default, jika kita menjalankan MongoDB, mode yang dijalankan tidaklah aman
    > - Tidak ada Authentication dan tidak ada Authorization
    > - Agar aman, kita harus mengaktifkan fitur access control di MongoDB

+ **User Admin** 
    > - User admin harus ada terlebih dahulu sebelum kita mengaktifkan access control
    > - User admin adalah user yang memiliki role userAdminAnyDatabase dan readWriteAnyDatabase
    > - Setelah membuat user admin, kita bisa menjalankan ulang MongoDB dengan perintah `--auth`

+ contoh :  
    ~~~ javascript
    // use admin database
    // use admin

    db.createUser(
        {
            user: "mongo",
            pwd: "mongo",
            roles: [ 
                "userAdminAnyDatabase",
                "readWriteAnyDatabase" 
            ]
        }
    )

    // Connect to mongodb with username & password
    // mongo --username mongo --password mongo --host localhost --port 27017

    ~~~

**[⬆ back to top](#top)**

# 29 Authentication
[![Video dari youtube](http://img.youtube.com/vi/7-HqgNofQsc/0.jpg)](http://www.youtube.com/watch?v=7-HqgNofQsc)

+ **Apa itu Authentication ??** [:link:docs](https://docs.mongodb.com/manual/core/authentication/)
    > - Authentication adalah proses memverifikasi identitas pengguna ketika mengakses MongoDB
    > - Saat menggunakan authentication, maka client wajib menggunakan username dan password untuk terkoneksi ke MongoDB server
    > - MongoDB mendukung banyak mekanisme authentication, seperti :
    >   - SCRAM : https://tools.ietf.org/html/rfc5802
    >   - Certificate Authentication
    >   - LDAP
    >   - Kerberos, dan lain-lain

+ **User** [:link:docs](https://docs.mongodb.com/manual/core/security-users/)
    > - Di MongoDB, kita bisa menambahkan user, dan juga menambahkan role ke user tersebut
    > - Saat kita membuat user, kita harus menentukan database sebagai authentication database
    > - Namun bukan berarti user hanya bisa mengakses database itu saya, tapi user juga bisa mengakses database lain jika mau
    > - Nama user harus unik per database, namun jika database nya berbeda, kita bisa membuat user dengan nama yang sama

+ **User Function** [:link:docs](https://docs.mongodb.com/manual/reference/method/js-user-management/)
    Function | Keterangan
    --- | ---
    `db.createUser()` | Membuat user
    `db.getUsers()` | Mendapatkan semua user
    `db.dropUser()` | Menghapus user
    `db.updateUser()` | Mengupdate user
    `db.changeUserPassword()` | Mengubah user password

+ **Syntax User**
    ~~~ javascript
    db.createUser(
        {
            user: "user",
            pwd: "password", 
            roles: [
                { 
                    role: "role", 
                    db: "database" 
                },
                "other role"
            ]
        }
    )
    ~~~

    - Contoh :
        ~~~ javascript
        //[1] Use test database as authentication databae
        // use test;

        // Create user with access read only
        db.createUser(
            {
                user: "contoh",
                pwd: "contoh", 
                roles: [
                    { role: "read", db: "test" }
                ]
            }
        )

        // connect using
        // mongo --username contoh --password contoh --authenticationDatabase test
        // karena role hanya read maka hanya bisa membaca data doang

        //[2] Create user with access read
        db.createUser(
            {
                user: "contoh2",
                pwd: "contoh2", 
                roles: [
                    { role: "readWrite", db: "test" }
                ]
            }
        )

        // connect using
        // mongo --username contoh2 --password contoh2 --authenticationDatabase test



        /**karena rolenya hanya readWrite maka perintah dibawah ini tidak akan bisa 
        * contoh nya tidak bisa gunakan dibawah ini :
        */

        // Get all users
        db.getUsers()

        // Change password for user contoh
        db.changeUserPassword("contoh", "rahasia")

        // Drop user contoh
        db.dropUser("contoh")

        // Update user
        db.updateUser("contoh2",
            {
                roles: [
                    { role: "readWrite", db: "test" }
                ]
            }
        )
        ~~~

**[⬆ back to top](#top)**

# 30 Authorization
[![Video dari youtube](http://img.youtube.com/vi/OHzTZ6htW1I/0.jpg)](http://www.youtube.com/watch?v=OHzTZ6htW1I)

+ **Apa itu Authentication ??** [:link:docs](https://docs.mongodb.com/manual/core/authentication/)
    > - Authorization adalah proses yang dilakukan setelah proses Authentication sukses
    > - Authorization dilakukan untuk melakukan pengecekan apakah user memiliki hak akses untuk melakukan sebuah action
    > - Hak akses di MongoDB disimpan dalam bentuk role

+ **Database Roles** [:link:docs](https://docs.mongodb.com/manual/reference/built-in-roles/)
    Role | Keterangan
    --- | ---
    `read` | Bisa membaca data di semua collection yang bukan sistem collection
    `readWrite` | Bisa membaca dan mengubah data di semua collection yang bukan sistem collection
    `dbAdmin` | Bisa melakukan kemampuan administrasi database
    `userAdmin` | Mampu membuat user dan role
    `dbOwner` | Kombinasi readWrite, dbAdmin dan userAdmin


+ **All Database Roles** [:link:docs](https://docs.mongodb.com/manual/reference/built-in-roles/)
    Role | Keterangan
    --- | ---
    `readAnyDatabase` | Seperti read role, tapi untuk semua database
    `readWriteAnyDatabase` | Seperti readWrite role, tapi untuk semua database
    `userAdminAnyDatabase` | Seperti userAdmin, tapi untuk semua database
    `dbAdminAnyDatabase` | Seperti dbAdmin, tapi untuk semua database


+ **Backup & Restore Roles** [:link:docs](https://docs.mongodb.com/manual/reference/built-in-roles/)
    Role | Keterangan
    --- | ---
    `backup` | Kemampuan untuk melakukan backup database
    `restore` | Kemampuan untuk melakukan restore database


+ **Superuser Roles** [:link:docs](https://docs.mongodb.com/manual/reference/built-in-roles/)
    Role | Keterangan
    --- | ---
    `root` | Bisa melakukan apapun

+ **Privileges** [:link:docs](https://docs.mongodb.com/manual/reference/privilege-actions/)
    > - Role membatasi hak akses di level database
    > - Kadang kita ingin membatasi di level collection
    > - Untuk melakukan itu, kita bisa menggunakan privileges


+ **Role Function** [:link:docs](https://docs.mongodb.com/manual/reference/method/js-role-management/)
    Role | Keterangan
    --- | ---
    `db.createRole()` | Membuat role baru
    `db.getRoles()` | Mendapatkan role
    `db.deleteRole()` | Menghapus role
    `db.updateRole()` | Mengubah role

+ **Syntax Role** :
    ~~~ javascript
    db.createRole({
        role: "name",
        privileges: [
            {
                resource: {
                    db: "database",
                    collection: "collection"
                },
                actions: ["action"]
            }
        ],
        roles: [
            {
                role: "role",
                db: "database"
            }
        ]
    });
    ~~~

+ **Contoh** :
    ~~~ javascript
    // Use test database
    // use test;

    // create role
    db.createRole({
        role: "find_and_insert",
        privileges: [],
        roles: [
            {
                role: "read",
                db: "test"
            }
        ]
    });

    // Get all roles
    db.getRoles({ showPrivileges: true });

    // update role
    db.updateRole("find_and_insert", {
        privileges: [
            {
                resource: {
                    db: "test",
                    collection: "products"
                },
                actions: [ "insert" ]
            }
        ],
        roles: [
            {
                role: "read",
                db: "test"
            }
        ]
    });

    // Add use with role
    db.createUser({
        user: "eko",
        pwd: "eko", 
        roles: [ "find_and_insert" ]
    });

    // Connect to mongo server
    // mongo --username eko --password eko --authenticationDatabase test

    // Insert product [SUCCESS]
    db.products.insert({
        "_id" : 10,
        "name" : "iPad Pro 11 2020",
        "price" : NumberLong(20000000),
        "category" : "tablet",
        "tags" : [
            "apple",
            "ipad",
            "tablet",
        ],
        "lastModifiedDate" : new Date(),
        "stock" : 10,
        "ratings" : [
            100
        ]
    });

    // Delete product [FAILED]
    db.products.deleteOne({
        _id: 10
    });

    // Update product [FAILED]
    db.products.updateOne({
        _id: 10
    },{
        $set: {
            category: "food"
        }
    });

    // Insert Customer [FAILED]
    db.customers.insertOne({
        _id: "kurniawan",
        name: "Eko Kurniawan Khannedy"
    });
    ~~~





**[⬆ back to top](#top)**
