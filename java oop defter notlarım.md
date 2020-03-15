# Java oop defter notlarım

Java platform bağımsız bir dildir. Yani java işletim sistemlerine göre derlenmez. Yazılan codelar oncelikle **javac** derleyicisiyle derlendikten sonra C,C++
tarzındaki diller gibi bizler Executable tarzında işlemcimizin hemen derleyebileceği bir tarzda dosya oluşturmaz. Oluşan dosya **.class** biçiminde bir dosyadır 
**.class** uzantılı dosyamızı açtığımızda bunun içinde yazılan **Byte code** denilen insanlarla işletim sistemlerinin anlayamayacağı bir codedur. Bunların işlemcimiz 
tarafında anlaşılması için  **jvm (java virtual machine )**' ihtiyacımız vardır.

>Compiler(derleyici) :fast_forward: codeları yüksek seviyeli bir dilden daha düşük seviyeli bir dile düşürür **ör:**Compiler'lar bildiğimiz Google translate gibidir 
direk olarak verilen şeyi anlaşılır bir hale gettirir.

> İnterpreter(yorumlayıcı) :fast_forward: yüksek seviyeli dillerde sıklıkla görülür compiler edilen code'lar bilgisayar dillerine dönüştürülemediği için yorumlayıcılar Bunları
işlemciler için anlaşılır bir hale gettirir **ör** İnterpreter'ler birer çevirmen gibi düşüne biliriz konuşulan diyalogları duygu ve düşünce bakımından da karşı tarafa 
aktarım gösterirler

**jvm** bir yorumlayıcıdır fakat buna **virtual machine** dememizin bir sebebi var mı acaba ? tabikide burdaki makineden kastımız ayrı bir işlemci gibi davranır ve 
girilen verileri direk olarak bilgisayarımızın anlayabilecegi kodlara çevirir. fakat C gibi bizlere bir executable dosyası vermez satır satır yorumlar ve yorumlanan
satırları çalıştırır.

      İşlemciler
        
        1.Fetc(al)
        2.Decode(çözümle)
        3.Execut(çalıştır)
    

tarzında çalışırken **jvm** ilk 2 satırı yapar ve 3. satırımızı yanı **Execut** işlemini işlemcilere bırakır.


```mermaid

graph TD

A[Java code ] -- Derleme*javac*  --> B((Byet code ))
B -- a.class --> D{JVM for different OS}

```

C dilinde 

  define Adam 3
  Const int Adam = 3
  Diye iki farklı veri tipimiz bulunmaktadır. **#define** ön bellekte adam görülen her yere 3 yazılmasına sebeb olur bizim işlemcimiz Adam diye bir veriyi görmez.
  
 **Const int** te ise verilen Adam değişkenine başka bir değer atayamayız her zaman Adam 3 olarak kalackatır 

Java dilinde

   final; diye bir değişkenimiz var bu değişkenimiz ise **C** deki **define** ve **Const int** değerlerimizie benziyorlar **final** değişkenimiz önceden bir değer almaz
    ne zaman biz bir değer veririz o zaman o değeri alır ve kilitler 

#### Hafıza

|adam   |static |  
|-------|-------|   
|       |Runtime Steck|   
| nesne | Heap  |   


Nesnenin yeri bellidir sabittir program başlar ve değişmez

Program içerisinde hafızaya alınan nesneler kulanımı bittikten sonra yerlerini farklı class
verirler


> Refactoring: codun çalışması değiştirilmeden tekrardan inşa edilmesi

Public static void main(string[] args)
    >Public JVM programı yorumlamaya başlarken main metodunu arar bu yüzden JVM in bulabilmesi için public veriyoruz.
    >static class tanımlamadan da çagırabilmemiz için 
    >void metodun değerini belirler 
    metodun değerlerine bir dizi parametresi göndermiyiz. Metodlarda direk olarak dizi parametresi giremediğimizden dolayı bunu bir indes olarak veririz
    >string[] args dizinin indislerini parametre olarak metoda gönderilmesine yarar 

## Nesneye dayalı programlamanın temelleri

### 1.**Abstraction-information hiding (soyutlama)**
### 2.**Encapsulation (kapsülleme)**
### 3.**inheritance (kalıtım-miraslama)**
### 4.**Polymorpism (çok biçimlilik)**

#### 1.Abstraction
> Ayrıntılardan uzaklaşma soyutlama 
> **ör** bir klavyeyi düşünelim üzerinde tuşlar bulunuyor basınca bişeyleri ekrana yazmamıza yardımcı olan bir aygıt 
 fakat bunu devresel olarak düşündüğümüz zaman ne kadar karmaşık bir hal alacağını düşünebilirz her bir harfin her bir tuşun 
aslında bir code'a takabul ettiğini düşünerek çalışmak gayet derecede zor olması lazım gelir. Bundan dolayı nesneye dayalı programlamada ne kadar 
sade, insanların daha basit anlayıp kompleks yapılardan uzaklaştıra işlemidir. 

### Abstraction
* bir varlığın **ne** olduğu ile ilgilenir **nasıl** olduğuyla değil 

![](https://images.pexels.com/photos/979247/pexels-photo-979247.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940)

şimdi kediyle ilgili bir class oluşrutalım ve buradan türetecegimiz nesneler farklı bakış açılarından oluşsun (bi veteriner bi petshop vb.) 

~~~java
   public class kedi{
        string: kuyruk
        string: cinsi
        yasi: int 
        asıdurumu: boolean
        fiyati: duble
       ------------------------- 
        miyav()
        asiyap(asix)
        getFiyat
    }
~~~

* bir bakış açısı ile bir varlıgın ne oldugu üzerinde durur **(böylelikle yazdığımız kılastaki bakış açıları birden çok olduğundan yanlıştır)** 

* single responsibility prhciple
     > bir sınıfın yanlız bir sorumluluğu olmalı
      
     ~~~java
     fiyat:duble
     texture:jpg
     koordinat:3D koordinat 
     -------------------------------
     ciz();
     getFiyat();
     ~~~
     
## Abstract Data Type (ADT) ((steck-yığın örneği))

~~~java
    public class stack{
        public int[] array;
        public int top;
        
        public stack(){
            array =new int [10];
            top=0;
          }
        public boolean isEmpyty(){
        if (top <=0)
        return true;
        return false;
        } 
        public boolean isFull(){
        if (top >= array.lenght)
        return true;
        return fasle;
        }  
        public void push(int value){
        if (!isFull())
        array[top++]=value;
        else 
        System.out.print("stack full");
        }
        public int pop(){
        if (!isEmpty())
        return array[--top];
        }
    }
~~~
yukarıda verilmiş olan bir kod dizisinde stack data type örnek kodu verilmiştir aşagılarda açıklayarak ilerliyeceğiz

![](https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2013/03/stack.png )

yukarıda görüldüğü gibi stack yapısında veriler üst üste biner ve sadece **üstten ekleme olur ve en üstten çekme olur**     

   > örnek verecek olursak bir tabak yığını düşünelim bu tabakları alırken ve yerlerine koyarken sadece en üsten alıp en üstten ekleme yapıyoruz 

şimdi bizim stacke kodumuzu kulanacak bir program geliştiricisi kalkıp şöyle bir code yazdı 

~~~java
public class Deneme{
public static void main(String[] args){
static s = new static();
s.push(5);
s.push(3);
int a = s.pop();
s.array[5]=7;   //1.hata
s.top = 20;     //2. hata
}
}
~~~

   > şu anda gördüğümüz üzere **array[5]**'i 7 ye eşitledik peki bizim top noktamız orasımıydı ya daha üstte iken biz          > kalkıp onun üzerine yazmış bulunduk veya daha altta iken biz stack yapısını bozup arada boşluk bıraktık  
   > aynı şekilde **s.top=20** yazan bölmede bizim önceden tanımladığımız top değeriniz bozup 20 yaptı

Şu anda bizim yazmış oldugumuz stacke kodunun bir anlamı bulunmamaktadır çünki yapı tamamıyla bozulmuştur peki biz bu olanların önüne nasıl geçicez ?
Tabikide bunun bir yöntemi var 

#### Bilgi saklama (infarmatıon hiding)
- Gerçekleştirme ayrıntılarını gizlenmesi 
- Bilgi sakalam 
   - Kapsülleme 
   - Erişim kısıtlama 
- Bilgi sakalama olmazsa 
    1. Abstraction ortadan kalkar 
    2. Kullanıcının hata yapmasına neden olur 
    3. Bakımı zorlaşır 
    
    
##### Bundan dolayı sınıf tanımlamalarında önem vermemiz lazım gelir 

## Sınıf öğeleri 

#### Methodlar (prosedür? - fonksiyon?)

syntax:
~~~java
ErişimOperetörü DönenTip methodAdı (parametre){
-
-
-
-
}
~~~

> Metod adı : parametrelerden önceki isim
> Metod imzsaı : metodların tamamen aynı yazılması 
#### Method overloading
Bir sınıfın içinde aynı adlı farklı imzaya sahip methodların bulunmasıdır 

### Static method 
Method tanımında static eklenen sınıf methodları  

### Dinamik method 
Method tanımında static eklenmeyen nesne metodları

--------------------------------------------------------------

## Construction

- **Görevi** 
    - 1-> Nesneyi ilklemek (oluşturmak deği)
            - olusturulan classlara ilk degerleri verir
    - 2-> "new" operetörlerine sınıfın bir örneğini (nesnesini) üretmesi gerektiğini söyler 
- Yapılandırıcı method adı sınıf adı ile aynıdır 
- Bir sınıfın içinde birden fazla yapılandırıcı bulunabilir 
- Bir sınıf içerisinde yapılandırıcı method yoksa varsayılan **(default)** yapılandırıcı devreye girer 
 ~~~java 
 stack s = new stack();
 ~~~
 - Sınıf içinde bir construction varsa varsayılan constructor devreden çıkar 

### Constuctor type 
#### 1-> Default constructor
    * Parametre almaz.
    * Eğer sınıfta bir constructor yazılmadıysa Java otomatik üretir 
~~~java
public SınıfAdi (){
}
~~~

bu yapılandırma alt alanlara var sayılan değeri atanır 
Java varsayılan değerler
String, Dizi, referans için Null
int, double, float için 0

#### 2-> Parametrized constructor (parametreli yapılandırıcı)
    * Dışardan parametre alır
    * Dışardan alınan parametre alt alanların ilklemesinde kullanılır
~~~java
public class Ogrenci{
private int no ;
private String adi;
    public Ogrenci(int snot String sadi){
        no=sno;
        adi=sadi;        
    }
// Eğer default constructor yapmak istersek

Ogrenci ogr = new Ogrenci ();

//parametrized constructor için ise 

Ogrenci ogr = new Ogrenci (2563 ,"ali");
}
~~~
#### 3-> Copy constroctor 
    * Parametre olarak kopyası alınacak nesnenin referansı geçirilir
    * Bu referans ile nesnenin alt alanları ilklenir 
~~~java 
public Ogrenci(Ogrenci kopya){
no = kopya.getNo();
adı = kopya.getAdi();
Ogrenci ogr3 = new Ogrenci(ogr2)
} 
~~~
        clone() Metodu bir nesnenin kopyasını almak için kullanılır
~~~java
Ogrenci ogr5 = ogr2.clone();
~~~

## Parametre Geçirme Yöntemleri 

### 1-> pass-by-value;
**Metoda sadece değer geçirilir**
### 2-> Pass-by-reference;
**Metod değişkeni sadece adresi geçirilir**
### 3-> pass-by-OutputValue;
**Metoda geri döndürülecek değeri tutacak adresi bilgisi gönderilir**
### 4-> pass-by-Name;
**Metoda değişkenin adı geçirilir**

        **JAVADA HERŞEY PASS-BY VALUE OLARAK GEÇİRİLİR**
## Sınıflar -Nesneler Arasındaki İlişkiler 
1-> **Sınıfta** **öğrenciler** vardır 

2-> Her **öğrencinin** bir **kartı** vardır  

3-> **Fakülte** **böümlerden** oluşur 

4-> **Üniverste** bir **eğitim kurumudur**

5-> **Ali** bir **öğrencidir**

6-> Bir **dersin** bir **hocası** bulunur 

7-> **Öğrenciler** **kart** ile giriş yapar 

8-> Bir **öğrencinin** **kayıt** tarihi vardır 

---------------------------------------------------------------

1-) **Sınıf** :fast_forward: **Öğrenci** (has (vardır))

2-) **Öğrenci** :fast_forward: **kartı** (has (vardır))

3-) **Fakülte** :fast_forward: **Bölüm** (has (vardır))

4-) **Üniverste** :fast_forward: **Eğitim kurumu**  ("is a" ("-dir"))

5-) **Ali** :fast_forward: **Öğrenci**  ("is a" ("-dir"))

6-) **Ders** :fast_forward: **Hoca** (has (vardır))

7-) **Öğrenci** :fast_forward: **Kartı** (use (kullanır))

8-) **Öğrenci** :fast_forward: **Tarih** (has (vardır))
      
> yapısal olarak bakıldığında 1. ile 6. **A** benzerken 2. 3. ve 8. de **B** (**A** ile **B** aşağıda açıklanacaktır). 
      
### Has a (Vardır ilişkisi)
1-) Kapsayan kapasanan ilişkisi

2-) Kapsayan kapsanan'a sahip mi ?

**A**  :fast_forward:  :small_blue_diamond: Has a ilişkisi 		
:small_blue_diamond: "is a part of " veya "owns" ilişkisi var. (**Composition**)

**B**  :fast_forward:   Sadece "has a" ilişkisi (**Aggregation**)

> Has a ilişkisi **Aggegation** ile kullanılır **Composition** **Aggegation**'ın özel bir türüdür  

#### Aggregation 
1) Has a ilişkisi
2) Nesnelerin yaşamları birbirlerine bağlı değildir 

~~~java
public class Ders {
	private string dersAdı;
	private hoca;
	private ogrenci [] ogrenciler;
public ders (string Adı, hoca,int k )
{
	dersAdı = adı;
	this.h = hoca;
	ogrenciler = new Ogrenci[k]; 
}
public void set hoca(hoca h)
{
	this.h=h;
}
public static main (String args[])
{
	dersAdı ndp = new Ders("nesne,100");
	hoca d = new Hoca("dogan");
	ndp.setHoca(d);
	ders td = new Ders("tasarım",d,30);
	ndp = null; // ndp yı yoketme 
}
}
~~~

> Yukarda gördüğümüz üzere (ndp = null) tarzında bir kod yazarak (ndp)  yi sıfırlıyoruz burada **Aggregation** mantığı ile bakacak olursak nesnemiz silinse bile ona bağlı özellikler veya başka nesneler metodlar her hangi bir verimiz başka bir nesneye de bağlı olabileceğinden nesnenin sıfırlanmasından etkilenmeyebilir.

#### Composition
1) "Has a" + "is part of " ilişkisi.

2) Kapsayanın hayatı biterse kapsananın da hayatı sona erer.

~~~java
public class Ogrenci{
	private string adı;
	private kart k;
public Ogrenci(int k-id,string adı)
{
	this.adı=adı;
	k= new kart (k-id);
}
	public class kart {
	private int k-id;
	public kart (int d){
	k-id=d;
}
public Ogrenci(string adı)
{
	this.adı=adı;
	k= null; //1. ihtimal 
	k= new kart (); //2. ihtimal
}
public void set kart (int id)
{
	k= new kart (id);
}
public int getkartId()
{
	return k.getId();
}
}
public static void main (string args[])
{
Ogrenci ogr = new Ogrenci(1234586,"Ali");
int id = ogr.getkartId();
}
}
~~~

> **Composition** bilgileri saklar ve dişardan ne bilgi alır ne de dışarıya bilgi verir böylelikle bir nesnenin referansı başka bir ver tarafından tutulamaz ve buradaki nesnemizi öldürdüğümüz zaman tüm metodlar veriler beraberinde ölürler. 
