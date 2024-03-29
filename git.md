# Git Notları

## Git Config 
git ile localde işlem yapmadan önce gitconfig ayarlamalarımız yapmamız lazım 

~~~
$ git config --global user.name "your_userName"
$ git config --global user.email "your_email@example.com"
~~~

sonrasında private repolara erişim için ssh key oluşturup bunu github'ımıza vermemiz gerekmektedir 

sshKey oluşturma 

~~~
$ ssh-keygen -t ed25519 -C "your_email@example.com"
~~~

oluşan id_rsa.pub adlı dosyayi açıyoruz ve içindekini github ssh key bölümüne açıklamamız ile kopyalıyoruz böylelikle işimiz bitmiş oluyor 


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

## Show 

projeniz üzerinde çalışıyorsunuz ve geçmişte yapmış oldugunuz işlemler ve şu anki değişiklikler hakkında bilgi almak istiyorsunuz o zaman 

dosyada yapılan değişiklikleri `` git status `` ile görebilirsiniz ( tüm değişiklikler önünüze serilecektir ) 

### Dosya bazlı değişiklikleri görmek

Stage'ye alınmayan yapılmış olan değişiklikleri göstermek için `` git diff `` komutunnu kullanabiliriz bu bizlere dosya bazlı(Tüm dosyaları gösterecektir)
fakat bizler commit bazlı değişiklikleri de listelemek isteyebiliriz 

> `` git diff commit1 commit2 `` yazarak 2 commit arasındaki değişiklikleri gözlemleyebiliriz 

Takım arkadaşlarınız kendi değişikliklerini tamamlayıp remote branch'de yayınladıktan sonra siz de bu değişiklikleri inceleyip kendi local branch'inize entegre ederek çalışmanıza devam edebilirsiniz. Ancak remote branch'deki değişiklikleri entegre etmeden önce bu değişikliklere ilişkin bilgileri (dosyaları değil sadece değişikliklere dair Git'de tutulan bilgiler) görmeniz ve incelemeniz gerekir.

`` git fetch origin `` komutu tam olarak üst tarafta yazmış oldugumuz yapmamızı sağlar remote repodaki veriyi localimize çekeriz ve değişikliklere göz atabiliriz böylelikle elimizde bulunan code herhangi bir değişikliğe ugramadan farkları görmemize olanak tanır (`` git pull `` ile arasındaki fark `` git pull `` kodları marge ederken `` git fetch  `` sizlere marge yapılmadan değişikliklere göz atmamıza olanak tanır )


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
