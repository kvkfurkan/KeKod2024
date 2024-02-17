
# KeKod 2024

![Logo](https://yt3.googleusercontent.com/ytc/AIf8zZSbMmEvgQpw7UYGdKI5wXealLHkO83P3u8k2jpr=s300-c-k-c0x00ffffff-no-rj)

__İş Görüşmesi Soruları__

__1-Type Inference Nedir?__

Type Inference bir değişken tipinin geliştirici tarafından tanımlanmamış olsa dahi eşitliğin diğer tarafı incelenerek ide tarafından tanımlanması işlemine verilen isimdir.

__2-Var ve Val nedir? Farkları nelerdir?__

Kotlin dilinde değişken tanımlamak için iki keyword bulunur: “val” ve “var”.
Değerlerini değiştirmek istemediğimiz değişkenleri tanımlamak için “val” kullanmalıyız. Ancak tanımlayacağımız değişken farklı değerler alabiliyorsa bu değişkeni “var” ile tanımlamalıyız.  Bu konu özelinde birçok medium makalesi ve farklı kaynakta val = immutable (değişmez), var = mutable (değiştirilebilir) ifadesi kullanılmaktadır bu ifade teknik olarak doğru değildir.
Developer Android sitesinde dahi “val” değişkenler için “whose value never changes” (değeri asla değişmeyen) ifadesi kullanılsa da “val” ile tanımlanmış bir değişken farklı sonuçlar tutabilir. Bu nedenle “val” keyword’ü için doğru tanımlama “immutable” (değişmez) değil, “read-only” (sadece okunur) olmalıdır. Konuyla alakalı kaynakları kaynakça bölümünde bulabilirsiniz.

__3-Var ve Val arasında performans farkı var mıdır?__

Var ve Val arasında dikkate alınmayacak ölçüde bir performans farkı vardır. Ancak bu performans farkı duruma göre değişiklik göstermektedir. Eğer Threading ile alakalı işlemler gerçekleştiriyorsak val ile tanımlama bize daha fazla performans sağlar. Ancak salt kod yazıyorsak var keyword’ü daha performanslı olacaktır.



__4- Bir Var değişkenini Val keyword kullanmadan nasıl val haline getirebiliriz?__

Kotlinde her değişken bir property’dir bu nedenle değişkenin set fonksiyonunu private yaparak, bu değişkeni read-only hale getirebiliriz.

__5-Kotlin’de her şey class ise değişkenler de birer class ise primitive tipler Kotlin’de bulunmaz mı?__

Kotlin’de class gibi görünen değişken tipleri (normalde primitive olduğunu bildiğimiz.) özel optimizasyonlarla byte code’a çevrilirken yine primitive olacak şekilde tanımlanır.

__6- Val ve Const Val arasındaki fark nedir?__

Temelde her ikisi aynı gibi görünmesine rağmen aralarındaki ana fark “val” ile tanımlanmış bir değişkene runtime’da değer atanırken, “const val” ile tanımlanmış bir değişkene compile time’da değer atanıyor olması. Tabii ki de tek farkları bu değil bir diğer fark “const val” yalnızca bir kotlin dosyasının top level’i olarak ya da obje içerisinde tanımlanabilir, ancak “val” herhangi bir yerde tanımlanabilir. Bu iki kavram arasındaki son fark ise “const val” runtime hesaplamaların elimine ederek performansa katkı sağlayabilir ancak bu durum “val” için geçerli değildir.

__7- “==” ve “===” operatörleri ile neleri kontrol ederiz?__

İki eşittir “Structural Equality Operator” (Yapısal Eşitlik Operatörü) olarak tanımlanmaktadır. Tanımdan da anlaşılacağı üzere bu operatör ile iki değişkenin veya nesnenin değerlerinin (içeriklerinin) eşit olup olmadığını kontrol ederiz ve değerler eşitse bize true değeri döner. Üç eşittir operatöründe ise durum değişiyor bu operatör ile iki değişkenin veya nesnenin aynı bellek konumuna atıfta bulunup bulunmadığını kontrol ediyoruz yani üç eşittir operatöründe bizim için önemli kıstas bellek adresleri.


__8- Primitive tipteki değişken nullable yapılır ve “===” operatörü ile referansı kontrolü edilirse nasıl bir sonuç alırsınız ve neden bu sonucu alırsınız?__

Eğer primitive tipteki bir değişken nullable olup üç eşittir operatörü ile refarans kontrolü yapılırsa ve Byte değer aralığının (-128, +127) dışında ise bu durumda false değer üretir farklı bellek alanlarını işaret ettiğinizi gösterir ama Byte aralığının içindeyse değerler farklı bile olsa true değerini üretir.

__9- İki tane sayısal değeri matematiksel işleme sokarsanız çıkan sonuç hangi tipte olur? (Örneğin = Long + Int)__

Sonuç değer aralığı daha geniş olan tipe göre belirlenir. Örneğin Long + Int işleminde sonuç Long tipinde olur.

__10- Aynı tipteki maksimum değere sahip iki değişkeni birbiriyle çarparsam sonuç ne olur?__

Bu durumda değer aralığının dışında bir sonuç olacağı için çıkan sonuç negatif rastgele bir sayı olarak gösterilir.

Kaynakça

[Kotlinlang.org](https://kotlinlang.org/docs/basic-syntax.html#variables)

[Developer.android.com](https://developer.android.com/kotlin/learn)

[Medium Val vs Var](https://freedium.cfd/https://xabaras.medium.com/kotlin-val-is-read-only-not-immutable-585ce2e5359b)

[Medium Type Inference](https://selimselcuk.medium.com/nil-kavram%C4%B1-fc24b81af566)

[Medium Val vs Const Val](https://mujeebkhan1831.medium.com/what-is-the-difference-between-val-and-const-val-in-kotlin-93ac7e18f5fe)

[Medium "==" vs "==="](https://developer.android.com/kotlin/learn)














