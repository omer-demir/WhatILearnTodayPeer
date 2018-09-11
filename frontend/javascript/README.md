- In javascript there is different keywords for object values. We need to know differences. First of all, **undefined** means as it is.
It has no value. 
- **NaN** is a different way to say it is not a number. 
- **Unassigned** means object created but there is no assigned value for it. 
You may not see it in examples but there is. 
- **Null** means object allocates in memory with null value. That means object has an empty value.

- undefined check için aşağıdaki metodlar kullanılır. Bunların en performanslısı **4.** dur 
 ```javascript
	function isUndefined(object){
        return object==undefined;
      }
      function isUndefinedValue(object){
        return object==='undefined';
      }
      function isUndefinedTypeOf(object){
        return typeof object==undefined;
      }
      function isUndefinedVoid(object){
        return object==void 0;
      }
```
