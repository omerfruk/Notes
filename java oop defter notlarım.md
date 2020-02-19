# Java oop defter notlarım

Java platform bağımsız bir dildir. Yani java işletim sistemlerine göre derlenmez. Yazılan codelar oncelikle **javac** derleyicisiyle derlendikten sonra C,C++
tarzındaki diller gibi bizler Executable tarzında işlemcimizin hemen derleyebileceği bir tarzda dosya oluşturmaz. Oluşan dosya **.class** biçiminde bir dosyadır 
**.class** uzantılı dosyamızı açtığımızda bunun içinde yazılan **Byte code** denilen insanlarla işletim sistemlerinin anlayamayacağı bir codedur. Bunların işlemcimiz 
tarafında anlaşılması için  **jvm (java virtual machine )**' ihtiyacımız vardır.

>Compiler(derleyici) :fast_forward: codeları yüksek seviyeli bir dilden daha düşük seviyeli bir dile düşürür **ör:**Compiler'lar bildiğimiz Google translate gibidir 
direk olarak verilen şeyi anlaşılır bir hale gettirir.

>İnterpreter(yorumlayıcı) :fast_forward: yüksek seviyeli dillerde sıklıkla görülür compiler edilen code'lar bilgisayar dillerine dönüştürülemediği için yorumlayıcılar Bunları
işlemciler için anlaşılır bir hale gettirir **ör** İnterpreter'ler birer çevirmen gibi düşüne biliriz konuşulan diyalogları duygu ve düşünce bakımından da karşı tarafa 
aktarım gösterirler

**jvm** bir yorumlayıcıdır fakat buna **virtual machine** dememizin bir sebebi var mı acaba ? tabikide burdaki makineden kastımız ayrı bir işlemci gibi davranır ve 
girilen verileri direk olarak bilgisayarımızın anlayabilecegi kodlara çevirir. fakat C gibi bizlere bir executable dosyası vermez satır satır yorumlar ve yorumlanan
satırları çalıştırır.

    >İşlemciler
        
        1.Fetc(al)
        2.Decode(çözümle)
        3.Execut(çalıştır)
    

tarzında çalışırken **jvm** ilk 2 satırı yapar ve 3. satırımızı yanı **Execut** işlemini işlemcilere bırakır.
    
    graph TD;
        Java code-derleme(javac)->Byte code;
        Byte code-a.class->JVM for Windows;
        Byte code-a.class->JVM for Linux;
        Byte code-a.class->JVM for Mac;

C dilinde 
    *#define Adam = 3
    *Const int Adam = 3
    Diye iki farklı veri tipimiz bulunmaktadır. **#define** ön bellekte adam görülen her yere 3 yazılmasına sebeb olur bizim işlemcimiz Adam diye bir veriyi görmez.
    **Const int** te ise verilen Adam değişkenine başka bir değer atayamayız her zaman Adam 3 olarak kalackatır 

Java dilinde 
    final; diye bir değişkenimiz var bu değişkenimiz ise **C** deki **define** ve **Const int** değerlerimizie benziyorlar **final** değişkenimiz önceden bir değer almaz
    ne zaman biz bir değer veririz o zaman o değeri alır ve kilitler 

####Hafıza

|       |       |   
|adam   |static |  Nesnenin yeri bellidir sabittir program başlar ve değişmez
|-------|-------|   
|       |Runtime|   
|       | Steck |   
|-------|-------|
| nesne | Heap  |   Program içerisinde hafızaya alınan nesneler kulanımı bittikten sonra yerlerini farklı class
|       |       |       verirler


>Refactoring: codun çalışması değiştirilmeden tekrardan inşa edilmesi

Public static void main(string[] args)
    >Public JVM programı yorumlamaya başlarken main metodunu arar bu yüzden JVM in bulabilmesi için public veriyoruz.
    >static class tanımlamadan da çagırabilmemiz için 
    >void metodun değerini belirler 
    metodun değerlerine bir dizi parametresi göndermiyiz. Metodlarda direk olarak dizi parametresi giremediğimizden dolayı bunu bir indes olarak veririz
    >string[] args dizinin indislerini parametre olarak metoda gönderilmesine yarar 

##Nesneye dayalı programlamanın temelleri

###1.**Abstraction-information hiding (soyutlama)**
###2.**Encapsulation (kapsülleme)**
###3.**inheritance (kalıtım-miraslama)**
###4.**Polymorpism (çok biçimlilik)**

####1.Abstraction
>Ayrıntılardan uzaklaşma soyutlama 
    >**ör** bir klavyeyi düşünelim üzerinde tuşlar bulunuyor basınca bişeyleri ekrana yazmamıza yardımcı olan bir aygıt 
    fakat bunu devresel olarak düşündüğümüz zaman ne kadar karmaşık bir hal alacağını düşünebilirz her bir harfin her bir tuşun 
    aslında bir code'a takabul ettiğini düşünerek çalışmak gayet derecede zor olması lazım gelir. Bundan dolayı nesneye dayalı programlamada ne kadar 
    sade, insanların daha basit anlayıp kompleks yapılardan uzaklaştıra işlemidir. 


            sınıf içi class içi  kalıtım  paket
public  +   |  /+/   |   /+/    |  /+/   |  /+/  |
            |        |          |        |       |
private  -  |  /+/   |   /-/    |  /-/   |  /-/  |
            |        |          |        |       |
protected # |  /+/   |   /+/    |  /+/   |  /-/  |
            |        |          |        |       |
pakege   ~  |  /+/   |   /+/    |  /+/   |  /-/  |

