### Exeption Istisna kavrami 
Exeption (Istisna kavramı) nerde ve nasıl kullanılır burada ele alıcaz

Istisna kavramı program çalışırken olası bir hatayı düzeltmek veya hatanın sebebini bulmak için kullanabiliriz

~~~dart
print("olasi hatanın sebebini veya adı biliniyorsa ");
try{        // turkcesi eger hata varsa bunları dene de diyebliriz
    int sonuc = 12~/0 ; 
    print("bolum = $sonuc");    
} on IntagerDivisionByZeroExeption {
    print("bolen 0 olamaz");
} 
~~~
~~~dart 
print("hatanın sebebi ve adı bilinmiyorsa");
try{
    int sonuc = 12~/0 ; 
    print("bolum = $sonuc");
}catch(e){ 
    //hatanın sebebi bilinmiyosa bunu bir parametreye atayalım
    print("hata cıktısı $e");
}
~~~
~~~dart
print("hatanın sebebi ve adı bilinmiyorsa ve stackrac'i gormek istiyorsak");
try{
    int sonuc = 12~/0 ; 
    print("bolum = $sonuc");
}catch(e , s){ 
    print("hata cıktısı: $e b-ve stack trace:$s");
}
~~~
~~~dart
print("Finally blogu");
try{
    int sonuc = 12~/0 ; 
    print("bolum = $sonuc");
}catch(e , s){ 
    print("hata cıktısı: $e b-ve stack trace:$s");
}finally(){ 
    print("finally blogu calisti");
}
~~~

~~~dart 
// eger kendi exeption umuzu yazmak istersek 
try{
    paraYatir(-60);
}catch(e){
    print("hata" + e.hataGoster());
}

paraYatir(int miktar){
    if(miktar<0){
        throw new ParaYatirExeption();
    }else print(hesabınıza $miktar TL yatirildi);
}

class ParaYatirExeption implements Exeption{
    String hataGoster() =>"negatif sayi giremezsiniz"
} 
~~~
>> öncelikle para yatırma metodumuzu yazıyoruz sonrasında ona uygun bir class ile hata parametresine gönderiliyor gönderilen hata catch blogunda hata parametresiyle geri döndürülüyor