\
# Headers
~~~
# H1
## H2
### H3
#### H4
##### H5
###### H6

Cara Lainnya :

Alt-H1
======

Alt-H2
------
~~~

**Output :**
> ![image](https://i.imgur.com/UyH77Dc.png)


# Styling text
  
| Style                       | Syntax                    | Output                                |
| ----------------------------|:-------------------------:| -------------------------------------:|
| Bold                        | ** ** or __ __            | **This is bold text**                 |
| Italic                      | * * or _ _                | _This text is italicized_             |
| Strikethrough               | ~~ ~~                     | ~~This was mistaken text~~            |
| All bold and italic         | *** ***                   | ***All this text is important***      |
| Subscript                   | \<sub> \</sub>            | <sub>This is a subscript text</sub>   |
| Superscript                 | \<sup> \</sup>            | <sup>This is a superscript text</sup> |
| Highlight                   | \` \`                     | `hightlight`                          |


# Buat Table
~~~
// Cara Ke-1
  | Tables        | Are           | Cool  |
  | ------------- |:-------------:| -----:|
  | col 3 is      | right-aligned | $1600 |
  | col 2 is      | centered      |   $12 |
  | zebra stripes | are neat      |    $1 |

// Cara Ke-2
  Markdown | Less | Pretty
  --- | --- | ---
  *Still* | `renders` | **nicely**
  1 | 2 | 3
~~~
  
**Output :**
> ![image](https://i.imgur.com/hHELbRq.png)
  
# List
~~~
// list dengan urutan no
1. Bisa menggunakan anka urutan `1, 2, 3, ...`
2. And more

// List suka-suka
- Bisa menggunakan tanda `-`
+ Bisa juga menggunakan tanda `+`
* Bisa juga menggunakan tanda `*`

// List dengan sub list
1. First list item
   - First nested list item
     - Second nested list item (enter + space 2x) 
~~~

**Output :**
> ![image](https://i.imgur.com/H5Zuug0.png)


# Task lists
- [x] #739
- [ ] https://github.com/octo-org/octo-repo/issues/740
- [ ] Add delight to the experience when all tasks are complete :tada:

**Output :**
> ![image](https://i.imgur.com/xrSXYW9.png)



# Garis
~~~
// Hyphens

---

// Asterisks
***

// Underscores
___
~~~

**Output :**
> ![image](https://i.imgur.com/3BWRBbf.png)


# LINK
menggunakan Format `[judulnya][linknya]`
~~~
[Langsung diarahkan ke-Linknya](https://www.google.com)

[Klik link anchor ke Judul di satu halaman doc](#garis)

//Bisa dibuat dengan refresi

  [Melalui refrensinya dibawah][ini Adalah Reffrensinya]
  
  [Atau bisa buat refresinya dibawah dengan nomor begini][1]

// ini refrensinya (tidak akan di print)

  [ini Adalah Reffrensinya]: https://www.mozilla.org
  [1]: http://slashdot.org
  [link text itself]: http://www.reddit.com
~~~

**Output :**
> ![image](https://i.imgur.com/llyTU8q.png)


**Output :**
> ![image]()

### Tambahkan Foto
![This is an image](https://myoctocat.com/assets/images/base-octocat.svg)
