Radiojs basit olarak **observer pattern**'i implemente etmiş pub/sub kütüphanesidir. Key özellikleri ise;

1. Dependency free olması. Tam olarak olmasada minimal seviyede olması
2. Chainable method desteği olması ki bu bence güzel bir özellik. Bknz **Fluent Api**
3. **this** sorunsalını çözebilmek için çağırdığı metodlara context alması.
4. Callback methodları olması
5. boyutunun küçük olması yaklaşık 1kb

Örnek olarak bakmamız gerekirse;

```javascript

//Event adında bir pub-sub oluşturuyoruz.
radio('event').subscribe(yourFunction);

//bu event e bağlı tüm subscriberlara datayı publish ediyoruz.
radio('event').broadcast(data);

//ve silebiliyoruz.
radio('event').unsubscribe(yourFunction);
```

Subscribe methodu callback alırken bahsettiğimiz üzere callback contexti'de verebiliyoruz. bknz **this sorunsalı** 

`radio('event').subscribe([callback,context]);`

Ayrıca subscribe'a n tane callback tanımlayabiliyoruz.
```javascript
radio('event').subscribe(callback,callback2,callback3,[callback4.init,callback4]);
//or
radio('event').subscribe(callback).subscribe(callback2)...
```