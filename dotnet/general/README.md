**Neden fonksiyonlarda null döndürmemeliyiz**

 - Çünkü null döndürmek uygulamanın diğer katmanlarında sorunların çıkmasına ve slowly fail mevzusuna döner ve null kontrolünü her katmanda yapmak gerekiyor. Bunun yerine;
- Null Object return et örn: Class.Empty
	- Exception throw edilmesi gerekir
	- Bknz: [Yegor](http://www.yegor256.com/2014/05/13/why-null-is-bad.html)

**Util ya da helper sınıf kullanımından uzak dur.**

- DRY – dont repeat yourself- kuramı doğrultusunda biz helper ve utility sınıfı oluşturup static metodlar ile yazarız. Lakin bu yapı OOP’den ziyade procedural dillerde kullanımı uygundur.
- SRP – single responsiblity principle – dediğine göre her sınıf kendi işlerini yapmalı. Lakin biz helper class larda herşeyi koyuyoruz buda bu prensibi çöp yapıyor.
- LSP – liskov subsitution principle – aynı base class tan türeyen sınıflar birbiriyle değişebilmeli. Lakin helper bu durumu sağlamıyor. Prensip çöp olmuyor ama oop yapısına uymuyoruz.
- ISP – interface segregation principle – interfaceler iyi tanımlanmalı ve parçalanmalı. Lakin helper bu durumu sağlamıyor. Prensip çöp olmuyor ama oop yapısına uymuyoruz
- O/CP – open closed principle – prensibe göre sınıflar gelişmeye açık değişikliğie kapalı olmalılar. Lakin helper bu durumu sağlamıyor
- DI – dependency inversion – abstract lara bağlı olmalıyız, concrete sınıflara değil. Lakin helper hepsini kullandığı için dependency inversion’a ters düşüyor ve patlatıyor.

**Objeler genellikle immutable – değişmez olmalı**

- Köpek sınıfı constructor’ında tanımlanmalı tüm özellikleri örnğ, sonradan ismi ya da cinsi değişmemeli. Bu bilgileri ancak öğrenebiliriz.

**Getter/Setter is evil**

- Don't ask for the information you need to do the work; ask the object that has the information to do the work for you
- Bir obje diğer objeyi parçalayabilir çünkü başka değer set edilme işlemi var
- Objenin değerini set ederken diğer objeyi kullanıyorsak bu implementation detaylarını bildiğimizi varsayar ve değişiklik olduğunda orada değişiklik yapmak gerekir.
- Gözden kaçan şey şu bize göre objeler data tutan yapılar ama bu tamamen yanlış çünkü objeler yaşayan organizmalar, özellikleri, fonksiyonları ve yaşam çevrimi olan yapılardır. Örneğin;
 - Dog dog = new Dog();dog.setBall(new Ball());Örnek yanlış çünkü köpeğin topu olmaz
 - Dog dog = new Dog();Ball ball = dog.getBall(); buda yanlış çünkü köpekten topu yuttuysa alırsınız.
 - Dog dog = new Dog();dog.take(new Ball());Ball ball = dog.give();

**ORM kullanılmasını kısmak lazım**

- ORM, instead of encapsulating database interaction inside an object, extracts it away, literally tearing a solid and cohesiveliving organismapart.
- ORM iş olarak SQL işlemlerini saklaması gerekir lakin tam tersine SQL ile işlemler yapabiliyor oluşumuz OOP’ye encapsulation’a aykırı
- Test işlemini ve mock işlemini zorlaştırması

**Internal ile İşaretlenmiş Sınıfların Diğer Namespacelere açma**
Bu işlemi yapabilmek için *AssemblyInfo* üzerinden `[assembly: InternalsVisibleTo("namespace")]` yeterli olacaktır.

**Static classı özel kullanım durumları dışında kullanmamak gerekir**

- Static class, bir instance'ı alınamayan, bir interface ya da diğer bir classtan kalıtım alamayan, constructor'ı olmayan method ve property'ler kümesidir esasında. Object Oriented kavramına hiç uymayan bir yapıdır.
- Extension methodlar, Helper methodlar, global sabit değerler veya builder methodlar (örn: Firma.BosTekilFirma() gibi) vb durumlar haricinde kullanımının bize getirisinden çok götürüsü olacaktır.
- Peki static class bizi hangi noktalarda kısıtlar? 
	*	Static methodlar üzerinde test yazabilme kapasitemiz oldukça kısıtlanır. Örneği, interface'i, mock'u oluşturulamayan bir yapıdan söz ediyoruz sonuç olarak.
	*	SOLID prensiplerine uymaz. Her seferinde bizzat static class'ımızı değiştirmek zorunda kalırız. Her değişen veya eklenen durum için if'ler else'ler switch'ler kullanarak takla atmak durumunda kalırız. Static class'ımız herhangi bir bütünlük taşıyamayacağı için zaman geçtikçe method yığını olarak hizmet edecektir. 





