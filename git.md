# Git Notları

## Git branch 

### Branch ekleme 

İki yöntem vardır 

#### 1. si branc oluşturup sonrasında geçiş yapmak 
~~~git
git branch “branch_ismi”
~~~
yukarıdaki kod ile **branch_ismi** adinda branch oluştururuz

~~~git
git checkout “branch_ismi”
~~~
yukarıdaki kod ile **branch_ismi** isimli branch e geçiş yaparız 

işlemimizde hata bulunmaz ise alt taraftaki gibi mesaj alırız.
~~~git
Switched to new branch “carpma_islemi”
~~~


#### 2. si direk olarak branch oluşturup geçiş yapmaktır 
~~~git
git checkout -b “branch_ismi”
~~~
burada yapilan işlem **branc_ismi** isminde branch oluşturup geçiş yapar.

işlemimizde hata bulunmaz ise alt taraftaki gibi mesaj alırız.
~~~git
Switched to new branch “carpma_islemi”
~~~

### Branch silme 

Branch silmek için branch komutuna **-d** veya **--delete** parametrelerini veriyoruz. 

~~~git
git checkout -d “silinecek_branch_ismi”
~~~
##### **Note :** 
> brench içerisinde iken branch i silemessiniz (Bindigimiz dalı kesemeyiz)
> 
> branch bir yere merge edilmemiş ise hata vericektir zorunlu silmek için **-D** parametresi verilebilir
