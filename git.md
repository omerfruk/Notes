# Git Notları

## Create 

### Proje oluşturma 

çalışılan dizide .git uzantılı bir dosya ile beraber working tree nizi oluşturan komut
`` 
git init 
``

git çalışma dizininizi(working tree) staging area ye eklenmesini sağlayan komut 
``
git add .
``

staging area daki verilerimizin local repomuza taşınmasını sağlayan komut 
``
git commit -m "girilecek_mesaj"
``

commit -m seçenegi commit massage eklenecegini söylüyor 

daha fazla commit parametresi icin [git commit parameters](https://git-scm.com/docs/git-commit)

local repodaki verilerimizi remote repoya taşımak için 
``
git push 
``

### Var olan projeler 

herhangi bi uzak sunucuda(platform) bulunan projelerimizi localimize indirip kendi bilgisayarımızda çalışmak isteyebiliriz böylelikle yapmamız gereken işlemler basit 

#### HTTPS 

Projeninin uzantısını(https içeren)  `` git clone https://github.com/omerfruk/Notes ``  şeklinde verildiği taktirde proje localinize inmiş olacaktır fakat repo gizli ise ve işlem gerçekleşmiyorsa bunun sebebi git config eksiğinden kaynaklanıyordur 

[git config için dokümantasyon](https://git-scm.com/docs/git-config)

#### SSH 

git config ekledikten sonrasında oluşturulan ssh key'i uzak sunucunuza vermeniz gerekli (*ben git hub kullanıyorum ve github in ayarlar bölümünde ssh key bölümüne ekliyorum*)
bundan sonra komut satırına ```git clone git@github.com:omerfruk/Notes.git `` komutunu yazarak local reponuza çekebilirsiniz 

ya ben uğraşamam böyle komut satırı ne imiş derseniz derseniz **(inşallah yazılımcı değilsinizdir)** aynı yerde download bölümünden projeyi zip olarak indirebilirsiniz   

## .gitignore 

girilen format dosyaların git working tree den staging area(index) e girmesini engeller 

>logların bulundugu dizinin working tree den staging area ye girmesini engeller 
``
logs/
``

>styl uzantılı tüm dosyların working tree den staging area ye girmesini engeller 
``
*.styl
``




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

---
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
---
## Git merge
branch lar arasındaki değişiklikleri görmek için 
~~~git
git diff master branch2
~~~
master ile branch2 arasındaki fakları gösterir.

### Merge etme 
Önce dalı nereye merge etmek istiyorsak o dala **git checkout** ile geçiş yapmamız gerekiyor.

geçildikten sonra **git merge "branch_ismi"** diyerek merge işlemimizi gerçekleştiriyoruz 
