# PHP VE MYSQL NOTLARIM

***

### **DB** ayarları

***

Öncelikle **PHP** ve **MYSQL** ile bağlantı yapmamız lazım.

```php
<?php
    // Veritabanı Bağlantı ayarları
    $host     = "localhost";
    $DBname   = "db ismi";
    $username = "root";
    $password = "root";

    try {
        // Veritabanına bağlan
        $DB = new PDO("mysql:host={$host};dbname={$DBname}", $username, $password);
        // Hata Modunu Ayarla
        $DB->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    } catch (PDOException $exception){
        die("Veritabanına bağlantı kurulamadı: " . $exception->getMessage());
    }
?>
```
 ***
Sonrasında **PHP** kodu ile bu kodumuzu ilgili sayfalara **İNCLUDE** yani 
dahil etmemiz gerekecek

```php
<?php
       include '"db bağlanma ismi".php';
?>
``` 
***

### DB'ye veri yükleme çıkartma ve düzenleme  ile ilgili kodlar 

***

#### YÜKLEME

***
```php
<?php
    //db bağlantımızı kurduk
    include 'db_baglan.php';

    if(isset($_POST['submit'])){
        // Sorguyu hazırlayalım
        $SORGU = $DB->prepare("INSERT INTO "eklenecek_db_ismi"(parametre1, parametre2, parametre3)
        VALUES (:parametre1,:parametre2,:parametre3)");
        $SORGU->bindParam(":parametre1", $parametre1_değişkeni);
        $SORGU->bindParam(":parametre2",  $parametre2_değişkeni);
        $SORGU->bindParam(":parametre3",    $parametre3_değişkeni);
        // SQL Sorgumuzu çalıştıralım
        $SORGU->execute();
        // İşlem tamam. Ana sayfaya yönlendirelim.
        header("location: index.php");
        die();
    }
?>
```
***
Bir veri üzerinde çalışmadan önce verinin bizim **DB**'mizde var mı diye veriyi kontrol etmemiz lazım 
***
```php
<?php
    // verilen kontrolünde onların ID'lerini sorgulamamız yeterlidir
    if(!isset($_GET['id'])){
        die("verimesi gereken hata");
    }

```
***

#### VERİ ÇIKARTMA

***

```php

<?php
    //db ile bağlantımızı kurduk
    include 'db_baglan.php';
    //çıkartılmak istene veri varmı kontrol ettik 
    if(!isset($_GET['id'])){
        die("HATA: ID Değeri yok!");
    }

    // Sorgumuzu hazırlayalım
    $SORGU = $DB->prepare("DELETE FROM rehber WHERE id=:id");
    // Silinecek kayıt için ID değerini sorguda yerine koyalım
    $SORGU->bindParam(":id", $_GET["id"]);
    // Sorguyu çalıştıralım
    $SORGU->execute();
    // İşlem tamam. Ana sayfaya yönlendirelim.
    header("location: index.php");
    die();
?>


```
***
#### VERİ DÜZENLEME

***
```PHP

<?php
    //db ile bağlantımızı kurduk
    include 'db_baglan.php';
    //düzenlenecek veri elimizde varmı kontrol ettik
    if(!isset($_GET['id'])){
        die("HATA: ID Değeri yok!");
    }

    // Sorgumuzu hazırlayalım
    $SORGU = $DB->prepare("SELECT * FROM rehber WHERE id = :id");
    // Düzenlenecek kayıt için ID değerini sorguda yerine koyalım
    $SORGU->bindParam(":id", $_GET['id']);
    // Sorguyu çalıştıralım
    $SORGU->execute();
    if($SORGU->rowCount() == 0){
        // Düzeltimek istenilen böyle bir kayıt yok
        die("HATA: Böyle bir kayıt bulunamadı");
    }else{
        // Kaydı getirelim
        $KAYIT = $SORGU->fetch();
    }

    if(isset($_POST['parametre1'])){

        $parametre1 = $_POST['parametre1'];
        $parametre2  = $_POST['parametre2'];
        $birimi    = $_POST['parametre3'];

        // Sorgumuzu hazırlayalım
        $SORGU = $DB->prepare("UPDATE rehber SET parametre1=:parametre1, parametre2=:parametre2, parametre3=:parametre3 WHERE id=:id");
        // Sorgudaki parametrelerimizi yerlerine koyalım
        $SORGU->bindParam(":parametre1", $parametre1);
        $SORGU->bindParam(":parametre2", $parametre2);
        $SORGU->bindParam(":parametre3", $parametre3);
        $SORGU->bindParam(":id", $_GET['id']);
        // Sorguyu çalıştıralım
        $SORGU->execute();
        // İşlem tamam. Ana sayfaya yönlendirelim.
        header("location: index.php");
        die();
    }
?>

```


