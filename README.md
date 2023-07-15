
[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/0mNoXTBm)

# Sipay&Patika.dev .NET Bootcamp - Case #1: FluentValidation

Bu proje, ASP.NET 6.0 uygulamasında FluentValidation kütüphanesinin temel kullanımını göstermektedir. Proje, bir `PersonController` sınıfı içerir ve bu sınıfın `POST` yöntemi, gelen `Person` nesnelerini FluentValidation kurallarına göre doğrular.

---
FluentValidation, .NET platformunda kullanılan bir doğrulama kütüphanesidir. Özellikle ASP.NET gibi web uygulamalarında ve API'lerde kullanılan veri doğrulama işlemlerini kolaylaştırmak için tasarlanmıştır. 

FluentValidation, kuralları nesne tabanlı bir şekilde tanımlamanıza olanak tanır. Doğrulama kuralları, nesne özelliklerine (property) veya nesne üzerindeki metotlara uygulanabilir. Bu kurallar, nesnelerin belirli bir kriter veya kurala uygun olup olmadığını kontrol eder. Örneğin, bir metin alanının boş olmaması veya belirli bir karakter uzunluğunda olması gibi kriterler belirtebilirsiniz.

FluentValidation, geniş bir doğrulama kuralı koleksiyonuna sahiptir. Örneğin, boşluk kontrolü, uzunluk kontrolü, desen eşleme, sayısal değer aralığı kontrolü gibi birçok doğrulama kuralını kolayca uygulayabilirsiniz. Ayrıca, özelleştirilmiş doğrulama kuralları oluşturmanıza ve bunları kullanmanıza olanak tanır.

Kurallar, FluentValidation'da doğrulama sınıfları olarak tanımlanır. Bir doğrulama sınıfı, doğrulanacak nesnenin türüne ve özelliklerine ilişkin kuralları içerir. Doğrulama sınıfları, `AbstractValidator<T>` sınıfından türetilir ve `RuleFor` metoduyla doğrulama kuralları tanımlanır.

Örneğin, aşağıdaki örnek FluentValidation kullanarak bir `Person` sınıfının doğrulama kurallarını tanımlar:

  
    public class PersonValidator : AbstractValidator<Person> {
      
      public PersonValidator()
    
      {
    
          RuleFor(person => person.Name)
        
              .NotEmpty().WithMessage("Name is required.")
            
              .Length(2, 50).WithMessage("Name must be between 2 and 50 characters.");
            
          RuleFor(person => person.Age)
              .GreaterThanOrEqualTo(18).WithMessage("Age must be 18 or greater.");
      }}
    



Yukarıdaki örnekte, `PersonValidator` doğrulama sınıfı, `Person` nesnesinin `Name` özelliği için boşluk kontrolü ve uzunluk kontrolü, `Age` özelliği için ise yaş sınırı kontrolü tanımlar.

FluentValidation, ASP.NET projelerinde kolayca entegre edilebilir. Örneğin, bir API Controller'ında gelen verileri doğrulamak için doğrulama sınıfını kullanabilirsiniz. Doğrulama işlemi başarısız olduğunda, uygun hata mesajlarıyla birlikte hata yanıtları dönebilirsiniz.

FluentValidation, doğrulama işlemlerini daha esnek ve okunabilir bir şekilde gerçekleştirmenize olanak sağlar. Modellerinizin doğrulama kurallarını merkezi bir yerde tanımlayarak, kod tekrarını azaltabilir ve daha sürdürülebilir bir yapı oluşturabilirsiniz.

Umarım bu bilgiler, FluentValidation hakkında size detaylı bir anlayış sağlamıştır.
