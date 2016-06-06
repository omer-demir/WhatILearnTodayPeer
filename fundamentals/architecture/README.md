#### Hexagonal Architecture - AKA Ports&Adapters

Alışık olduğumuz n-tier yapıdaki coupling sorununu çözebilmek için ortaya çıkmıştır. DDD ve TDD açısında gayet kullanışlı olan bu yapı UI ve test anlamında bize güzellikler 
sunmaktadır.

![PortAdapters](https://spin.atomicobject.com/wp-content/uploads/ports_and_adapters_architecture.jpg)

Resimde gözüken sağdakiler **collabratorler** soldakiler ise **event generator**.

** Collobartor ** örnekleri ORM, DB, Ext. WebApi, MQ
** Event Generator ** örnekleri MVC, REPL

**Adapter** olarak tanımladıklarımız **_The adapter’s job is to translate an interface from a framework or class into a compatible interface_**

**_Dependency Diagram_** olarak en dıştan içe doğru olacaktır. Bu sebeple genellikle onion architecture diyebiliyoruz.


#### Making it Cohesive

**Cohesion** dediğimiz şey aslına bakıldığında bir routin'in tutarlılığıdır. Açık bir örnek vermek gerekirse **CreateCustomer()** açıklayıcı bir routindir.
_High Cohesion_ mevzusunu sağlamaktadır. Buna karşılık **CreateCustomerAndChargeEmpty()** is _Low Cohesion_ örneğidir. Yönerge der ki **_Cohesion_** sağlayabilmek 
için küçük metodlara bölünüz ve anlamı olsun. 

Bunlara ek olarak eğer bir routine içerisinde çok fazla **_Cyclomatic Complexity_** var ise o kısmı parçalayın ve metoda bölün demektedir.