- Angular'da 'digest in progress' hatası alındığında safeApply kullanılması uygundur
```javascript
function safeApply(scope, fn) {
    (scope.$$phase || scope.$root.$$phase) ? fn() : scope.$apply(fn);
}
```

- $http vs $resource : 
        * $http: http ile gelen response eğer manipule edilmesi gereken bir yapıdaysa $http modülünü kullanmamız gerekir.
        * $resource: kullandığımız api restful bir yapıdaysa, gelen response kullanabileceğimiz ve direk son kullanıcımıza sunabileceğimiz 
        basitlikte olacağından $resource gibi daha high-level bir modülü kullanmamız bizi kompleks işlerden kurtarabilir.
- Iframe içerisinde veri olarak url vermek istediğimizde unsafe context hatasını almamak için
```$sce.trustAsResourceUrl($scope.selectedBlogItem.url)``` kullanmak sorununuz çözecektir.