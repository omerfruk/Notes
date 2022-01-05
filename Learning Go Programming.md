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

#### go build Komutu 

Eğer kodumuzun binary kısmını sonradan kullanamk istiyorsak yani kodumuzun çıktısını executable bir şekilde elde etmek istersek bunu terminale ``go build hello.go`` yazarak yapabiliriz. Hem elimizde kodun derlenmiş hali bulunurken hem de konsola *Merhaba, Dünya!* yazacağını göreceğiz.

Bazı durumlarda Çıktımız farklı çıktılar ile vaya farklı dosya isimleri ile karışmamasını istersek komutumuza ``-o`` komutumuzu kullanarak yani  ``go build -o hello_world hello.go`` yazarak isimlendirmeyi farklı yapabiliriz.

#### Third-Party kütüphane kullanımı 
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

