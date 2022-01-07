# Learning Go: An Idiomatic Approach to Real-World Go Programming Kitabından almış olduğum notlar 

## Çalışma ortamınızı Kurma

Go code yazmak için öncelikle Go geliştirme araçlarını indirip yüklemeniz gerekir. Araçların en son sürümünü Go web sitesindeki yüklemeler sayfasında bulabilirsiniz.

> Bir terminal veya komut istemi açıp aşağıdaki komutu yazarak ortamınızın doğru şekilde kurulduğunu doğrulayabilirsiniz: 

~~~go
 $ go version 
 ~~~

> Her şey doğru şekilde kurulduysa, bu şekilde yazdırılmış bir şey görmeniz gerekir:
~~~go 
go version go1.15.2 darwin/amd64
~~~

### go run ve go build 

Aslına bakılırsa ``go run`` ve ``go build`` komutlarının yaptığı işler aynı gibi gözükür fakat aralarında birkaç farklılıklar bulunmaktadır.

#### go run Komutu 

Basit bi Merhaba dünya ile başlayalım 

~~~go 
package main

import "fmt"

func main() { fmt.Println("Merhaba, Dünya!")
}
~~~

Dosyayı **hello.go** olarak  kaydedip terminale ``go run hello.go`` yazdığımızda terminalede *Merhaba, Dünya!* yazdığını göreceğiz eğer doyamızın içerisine baktıgımız zaman binary biçiminde kaydedilmediğini göreceğiz.

çünkü ``go run`` komutunu çalıştırdığımızda binary çıktımız geçici bir dizinde oluşturulur ve program çalışmasını durdurduğu vakit bu geçici dizin silinir

----

#### go build Komutu 

Eğer kodumuzun binary kısmını sonradan kullanamk istiyorsak yani kodumuzun çıktısını executable bir şekilde elde etmek istersek bunu terminale ``go build hello.go`` yazarak yapabiliriz. Hem elimizde kodun derlenmiş hali bulunurken hem de konsola *Merhaba, Dünya!* yazacağını göreceğiz.

Bazı durumlarda Çıktımız farklı çıktılar ile vaya farklı dosya isimleri ile karışmamasını istersek komutumuza ``-o`` komutumuzu kullanarak yani  ``go build -o hello_world hello.go`` yazarak isimlendirmeyi farklı yapabiliriz.

---

### Third-Party kütüphane kullanımı

Bazen başkalarının yazmış oldugu kütüphaneleri kodumuzda kullanmak isteriz.

Go’nun kod yayınlama yöntemi diğer birçok dilden biraz farklıdır. Go yazılım geliştiricileri, JavaScript için NPM kayıt defteri gibi merkezi olarak barındırılan bir hizmete güvenmez. Bunun için, projelerin kaynak kodlarını kod repolarında paylaşırlar. ``Go install`` komutu, yüklemek istediğiniz projenin kaynak kodu repo konumu olan bir bağımsız değişken alır ve ardından **@** ve istediğiniz aracın sürümü (yalnızca en son sürümü almak istiyorsanız **@** en son sürümünü kullanın). Ardından aracı $GOPATH/bin dizininize indirir, derler ve yükler.

Hızlı bir örneğe bakalım. Hey, yük testleri HTTP sunucuları olarak adlandırılan harika bir Go aracı var. ``Go install ``komutuyla nasıl yükleneceğini görelim:

~~~go
$ go install github.com/rakyll/hey@latest
    go: downloading github.com/rakyll/hey v0.1.4
    go: downloading golang.org/x/net v0.0.0-20181017193950-04a2e542c03f
    go: downloading golang.org/x/text v0.3.0
~~~

Hey kütüphanemizi ve onun içerisindeki tüm bagımlılıkları idnirir ve ``$GOPATH/bin`` uzantısına binary şekilde yükler.

---

## Types 

### Arrays 

> Go da diziler pek fazla kullanılmaz bunun sebebi ``[3]`` ve ``[4]`` boyutundaki dizileri farklı tipler olarak tanımlar ve yanı sıra dizinin uzunluğunu bir değişkende tutamazsınız çünkü çünkü tipler çalışma zamanında değil, derleme zamanında çözümlenmelidir.

> Ayrıca, farklı boyuttaki dizileri aynı türe dönüştürmek için *type conversion* uygulayamazsınız. Farklı boyutlarda dizileri birbirine dönüştüremeyeceğiniz için, herhangi bir boyuttaki dizilerle çalışan bir *Fonksiyon* yazamazsınız ve aynı değişkene farklı boyutlarda diziler atayamazsınız.

### Slices

Çoğu zaman, bir değer dizisi tutan bir veri yapısı istediğinizde, kullanmanız gereken bir **slices** olur. **Slices**'i bu kadar kullanışlı kılan şey, uzunluğun bir **slices** için type belirteci olmamasıdır. Bu işlem, dizilerin sınırlamalarını kaldırır. Her boyuttaki **slices**'ı işleyen tek bir fonksiyon yazabiliriz ve gerektiğinde **slices**'ı büyütebiliriz.

> Eğer ``[...]`` kullanımı uygulanırsa bu bir **dizi**, ``[]``  kullanımı uygulanırsa bu bir **slice** olur. 

### Capacity

Her *Slices*, ayrılan ardışık bellek konumu sayısı olan bir kapasiteye sahiptir. Bu, uzunluktan daha büyük olabilir. *Slices*'lara ekleme yapıldıgında *Slices*'in sonuna bir veya daha fazal değer eklenir. Eklenen her değer uzunluğu bir artırır. Uzunluk kapasiteye ulaştığında, değer koymak için daha fazla alan olmaz. Uzunluk kapasiteye eşit olduğunda ek değerler eklemeye çalışırsanız, Ekleme fonksiyonu, daha yüksek kapasiteli yeni bir dilim atamak için Go runtime'nı kullanır. **Orijinal slices'ta bulunan değerler yeni slices'a kopyalanır, yeni değerler sona eklenir ve yeni slices geri döndürülür.**

> Slices'lar ne kadar da otomatik kapasite artmasına olanak tanısa da iyi tahmin edilmiş kapasiteli Slices oluşturmak performans açısından daha iyi olacaktır.

### Make 

Slices oluştururken dinamik olarak kapasitenin girilebileceğini söyledik 
~~~go 
x := make([]int,5)
~~~
> oluşan slices in tüm elemanları default olarak 0 değerini alır.

burada uzunlugu 5 olan ve kapasitesi 5 olan bir *slices* oluşturduk fakat en çok yapılan hatalardan biri 

~~~go 
x = append(x,10)
~~~
> append fonksiyonu her zaman *slices*'in uzunlugunu arttırır. Bu yüzden yeni oluşacak dizimiz **[0,0,0,0,0,10]** olur.

Kapasiteyi dinamik olarak vermek istersek
~~~go
x := make([]int, 5, 10)
~~~

Kodumuz 5 uzunlugunda 10 kapasiteli bir **Slices** oluşturur.

~~~go
 x := make([]int, 0, 10) 
 x = append(x, 5,6,7,8)
~~~

x in değeri şimdi **[5,6,7,8]** şeklinde **4** uzunlukta **10** kapasitede hali hazırda bulunan **slices**'ımız.

### Slice oluşturma

 Birincil hedef, **slice** büyümesi gereken sayıyı en aza indirmektir. Eğer dilimin hiç büyümesine gerek kalmayacaksa (çünkü fonksiyonunuz hiçbir şey dönmeyebilir)

 ~~~go
 var data []int
 ~~~

Başlangıç değerlerinden bazılarınız varsa veya bir **slice** değerleri değişmiyorsa

~~~go
data := []int{2,4,6,8}
~~~

Dilimin ne kadar büyük olması gerektiği konusunda iyi bir fikriniz varsa ancak programı yazarken bu değerlerin ne olacağını bilemezseniz, make  seçeneğini kullanın.ardından 0 uzunlukta, kapasitesi 0 olmayan **slice** oluşturmanın önerilen 3 yolu vardır: 

1 ->  Dilimi arabellek olarak kullanıyorsanız, sıfır olmayan bir uzunluk belirleyin.

2 ->  Tam olarak istediğiniz boyutu bildiğinizden eminseniz, değerleri ayarlamak için ***slice*** uzunluğunu ve indexini belirleyebilirsiniz. 

3 -> Diğer durumlarda sıfır uzunlukta ve belirli bir kapasitede make seçeneğini kullanın. Bu, **slice** öğe eklemek için ***append***'i kullanmanızı sağlar. Öğe sayısı daha küçük gibi çıkarsa, sonunda dışarıdan sıfır değeri olmaz. Öğe sayısı daha büyükse, kodunuz panik olmaz.

---

### Slice parçası (Slicing Slices)

> Bir **slice**'tan kesit aldığınızda, verilerin bir kopyasını almıyorsunuz. Bunun yerine, artık belleği paylaşan iki değişkeniniz oluyor. Bu, bir **slice**'taki bir öğede yapılan değişikliklerin o öğeyi paylaşan tüm **slice**'larda da etki oluşturacagı anlamına gelir. 

> Karmaşık **slice** yapılarından kaçınmak için ya alt **slice** lara ekleme yapmayın yada ana **slice**'a etki etmediğinden emin olun.

---

### Diziden slice elde etme 

> Bir diziniz varsa, bir slice ifadesi kullanarak bu diziden bir **slice** alabilirsiniz. Bu, bir diziyi yalnızca **slice** alan bir *fonksiyona* köprüleme için kullanışlı bir yoldur. Ancak, bir diziden **slice** almanın, bir **slice**'tan **slice** alma ile aynı bellek paylaşımı özelliklerine sahip olduğunu unutmayın.

~~~go
x := [4]int{5, 6, 7, 8} 

y := x[:2]
z := x[2:]

x[0] = 10 

fmt.Println("x:", x)
fmt.Println("y:", y)
fmt.Println("z:", z)
~~~

Çıktı olarak 

    x: [10 6 7 8]
    y: [10 6]
    z: [7 8]
---

### Copy

Eğer bir **slice**'ın aynısı fakat daha özgürü(adres paylaşımı olmadan) lazım ise ``copy()`` methodunu kullanabiliriz 
~~~go 
x := []int{1, 2, 3, 4} 
y := make([]int, 4) 
num := copy(y, x) 
fmt.Println(y, num)
~~~

Çıktı olarak 
    
    [1 2 3 4] 4

Aynı zamanda tüm diziyi kopyalamamıza gerek yoktur 

~~~go 
x := []int{1, 2, 3, 4} 
y := make([]int, 2) 
copy(y, x[2:])
~~~

---

## Strings, Runes ve Bytes
> bir diziden veya slice tan bir değer çıkartabileceğiniz gibi, bir index ifadesi kullanarak bir stering tek bir değer çıkartabilirsiniz:

~~~go 
var s string = "Hello there" 
var b byte = s[6]
// veya stringten slice elde etme 
var s2 string = s[4:7]
var s3 string = s[:5]
var s4 string = s[6:]
~~~

