# Git Notları

### Git branch 

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
