- Angular'da 'digest in progress' hatası alındığında safeApply kullanılması uygundur
```javascript
function safeApply(scope, fn) {
    (scope.$$phase || scope.$root.$$phase) ? fn() : scope.$apply(fn);
}
```
