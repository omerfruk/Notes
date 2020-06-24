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
    //hatanın sebebi bilinmiyosa bunu bir parametreye atayalım
    print("hata cıktısı: $e b-ve stack trace:$s");
~~~