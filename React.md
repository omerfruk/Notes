# React Nedir?
React, kullanıcı arayüzleri oluşturmak için açık, verimli ve esnek bir JavaScript kütüphanesidir.
## Metodlar 

### Render (){};
**render** metodu, *ekranda neyi görüntülemek istiyorsanız* onunla ilgili bir tanımlama geri döndürür. **React** de bu tanımlamayı alır ve görüntüler.

**React.createElement('div')** şeklinde bir JavaScript metot çağrısına dönüştürülür. Üstteki örneğin derlenmiş hali aşağıdaki gibidir:
~~~js
return React.createElement('div', {className: 'shopping-list'},
  React.createElement('h1', /* ... h1 içeriği ... */),
  React.createElement('ul', /* ... ul içeriği ... */)
);
~~~