## EF Validations

Entity framework ile validation gereksinimi çeşitli yollardan sağlayabiliyoruz. Bunlar

#### 1. DataAnnotations
```csharp
public class User{
    public int Id{get;set;}
    [Required]
    public string Name{get;set;}
}
```
```xml
//in web config
<appSettings> 
    <add key="ClientValidationEnabled"value="false"/> 
    ... 
</appSettings>
```

#### 2. Fluent Api
```csharp
 modelBuilder.Entity<Blog>().Property(p => p.BloggerName).HasMaxLength(10); 
```

#### 3. IValidateObject
```csharp
public class Blog : IValidatableObject 
 { 
     public int Id { get; set; } 
     [Required] 
     public string Title { get; set; } 
     public string BloggerName { get; set; } 
 
     public IEnumerable<ValidationResult> Validate(ValidationContext validationContext) 
     { 
         if (Title == BloggerName) 
         { 
             yield return new ValidationResult 
              ("Blog Title cannot match Blogger Name", new[] { "Title", “BloggerName” }); 
         } 
     } 
 }
```


------------------

 Hepimizin .NET ortamında C#'ta kullandığımız extension metodlara ait bir kaç küçük hatırlatma yapmak istedim.

#### 1. Extension methodların compile time binding 
Binding konusunda eğer objenin metodu aynı isim ve signature'da varsa onu kullanır aksi halde extension metod arar.

#### 2. Statik Constructor

- A static constructor does not take access modifiers or have parameters.
- A static constructor is called automatically to initialize the class before the first instance is created or any static members are referenced.
- A static constructor cannot be called directly.
- The user has no control on when the static constructor is executed in the program.
- A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.
- Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the LoadLibrary method.
- If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.