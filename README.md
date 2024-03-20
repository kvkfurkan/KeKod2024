
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

__11- Kotlinde ve-veya operatörleri lazy çalışma mekanizmasına sahiptir bu ne demek?__
Eğer veya operatörünün solu true ise sağdaki değere bakmaya gerek duymaz ve sonucu true kabul eder. Eğer ve operatörünün solu false ise sağdaki değere bakmaya gerek duymaz ve false kabul eder. Bu optimizasyondan dolayı sağda kalan değerlerin kontrolü yapılmaz.

__12- Verilen bir String dizisinde tekrar eden kaç karatker olduğunu bulan kodu yazınız.__
'''kotlin
print("Bir metin girin:")
val inputString = readLine() ?: ""

val charArray = inputString.toCharArray()

val charFrequencyMap = mutableMapOf<Char, Int>()

for (char in charArray) {
    charFrequencyMap[char] = charFrequencyMap.getOrDefault(char, 0) + 1
}

println("Tekrar eden karakterler:")
charFrequencyMap.filterValues { it > 1 }.forEach { (char, frequency) ->
    println("$char : $frequency")
}

'''

__13- Yıldızlar ile çam ağacı çizimi yapın.__
'''kotlin
fun printPineTree(height: Int) {
    for (i in 1..height) {
        for (j in 1..height - i) {
            print(" ")
        }
        for (k in 1..(2 * i - 1)) {
            print("*")
        }
        println()
    }
}

'''


__14- Değişkenler RAM’de nasıl depolanır?__
Ram iki farklı bölümden oluşur. Bu bölümler “Stack” ve “Heap” olarak isimlendirilir. Primitive tipteki değişkenler Stack bölümünde tutulur. Referans tipli değişkenler ise obje ismi Stack içerisinde tutulurken, içerdiği değer ise Heap içerisinde tutulur. Referans tipli nullable bir değişkene, null değer ataması yaparsak Heap’teki kısımda herhangi bir şey tutulmaz. Ancak bu değişken bir isme sahip olduğu için Stack’te yer kaplar. Stack memory, Heap memory’e kıyasla daha hızlı çalışır. Stack memory’de veriler üst üste LIFO (Last in first out) prensibiyle çalışırken, Heap memory’de veriler karışık bir biçimde saklanır. Stringler primitive değişken olmamasına rağmen özel optimizasyonlarla primitive hızında çalışır. (Java dili için de bu böyledir.)

__15- “++number” ve “number++” arasındaki fark nedir?__
Operatörün sağında ve solunda olması işlem önceliğini belirler. Eğer operatör değişkenden önce geliyorsa ilk önce arttırma işlemi yapılır akabinde diğer işlemler yapılır, ancak operatör değişkenden sonra geliyorsa ilk önce diğer işlemler yapılır ve işlemler bittikten sonra arttırma işlemi yapılır.

__16- Verilen sayının tek mi çift mi olduğunu dönen fonksiyonu yazınız.__
'''kotlin
fun singleOrDouble(number : Int) : String{
    if (number % 2 != 0){
        return "Number is single"
    }else{
        return "Number is double"
    }
}

'''

__17- “+” operatörü ve plus fonksiyonu aynı işi yapıyorsa ne zaman plus fonksiyonunu ne zaman “+” operatörünü kullanmamız gerekir?__
Operatörlerin fonksiyon hali null check yapmaktadır. Bu nedenle iki değerden biri nullable ise ya da iki değer birden nullable ise bu durumda operatör fonksiyonların kullanılması gerekir.

__18- If kullanımı ve else if kullanımı arasında nasıl bir fark vardır?__
Else if kullanımı aynı durumun farklı kontrolleri için kullanılmaktadır, ancak alt alta if kullanımı farklı durumları kontrol etmek için kullanılır. Else if kullanımı yapıldığında satır kontrol edilir eğer false sonucu çıkıyorsa bir alt satıra geçilir. Ancak alt alta if kullanımında satırlar kontrol edildikten sonra sonuçtan bağımsız bir biçimde alt satırlar da kontrol edilir. Bu nedenle else if kullanılması gereken yerlerde if kullanırsak bu performansı negatif yönde etkiler.

__19- Unit ve Nothing arasındaki fark nedir?__
Kotlin’deki Unit ifadesi bir fonksiyonun geriya anlamlı bir değer dönmediği durumlarda kullanılır. (Java’daki void keyword’ü ile aynı işleve sahip.) Nothing ifadesinde ise resmi dokümantasyonda şu şekilde tanımlama yapılır: “a value that never exists (asla var olmayan değer)” Constructor’u private biçimde tutulduğundan ötürü Nothing sınıfının hiçbir değeri ya da objesi olamaz. Nothing ifadesi hiçbir değer döndürmeyen fonksiyonlar için kullanılır. Örneğin sonsuz döngüler ya da her zaman hata dönen bir fonksiyon gibi. Bu ikili dışında bilmemiz gereken bir ifade daha mevcut bu da “Any” isimli class. Bu class diğer tüm classların parent (üst) class’ıdır, Kotlin’deki tüm class’lar Any class’ından türetilir. Java’daki “Object” sınıfına benzer bir rol oynar. Dolayısıyla herhangi bir nesne ya da herhangi bir sınıf türünü temsil etmek için kullanılabilir.

__20- First Class Citizen nedir?__
Türkçe çevirisi birinci sınıf vatandaştır, bir yapının First Class Citizen olabilmesi için belirli şartları sağlaması gerekir. Şartları şu şekilde sıralayabiliriz;
1-	Bir değişkenlere değer olarak atanabiliyorsa
2-	Başka fonksiyonlara parametre olarak verilebiliyorsa
3-	Başka bir fonksiyonun geri dönüş değeri olabiliyorsa
Bu üç özelliği barındıran yapılara First Class Citizen ismi verilir. Kotlin’de fonksiyonlar First Class Citizen’dir.

__21- Fonksiyonlarda Default Argument (Name Argument) ne demektir?__
Bir fonksiyon içerisinde parametre olarak bir değişken oluşturup, o değişkenin içerisine eşittir ile bir değer veriyorsak, bu fonksiyon çağırılırken değeri olan parametrelere değer atama işlemi opsiyonel olur. Hiçbir değer verilmemesi durumunda ilk atanan değer alınır. Buna fonksiyon overload denir. Aynı isimdeki birden fazla fonksiyonu yazıp kullanma olayına fonksiyon overload denir ve biz Kotlin’de fonksiyon overload yapmak zorunda kalmıyoruz çünkü default value’lar bize fonksiyon overload yapmayı sağlıyor.

__22- Fonksiyon Overload nedir?__
Bir isimle yazılmış fonksiyonun parametre sayıları değiştirilerek ya da parametre tipleri değiştirilerek aynı fonksiyon isminde birden fazla fonksiyon yazılması olayına Fonksiyon Overload denir. Kotlin’de default value (name argument) yapmak bize Fonksiyon Overload sağlar.

__23- Fonksiyonlar ne zaman kullanılır?__
Fonksiyonların amacı belirli işlevleri yerine getirmektir. Bu nedenle bir işlemi birden fazla yapacağımız her durumda fonksiyonları kullanabiliriz. Ayrıca kodu modüler hale getirmek ve okunaklılığını arttırmak için de fonksiyonları kullanabiliriz. Sonuç olarak fonksiyonları 3 ana konuda kullanabiliriz;
1-	Gruplayabildiğimiz yapılar için (Business logic içermese bile) kodun okunaklılığını arttırmak adına kullanabiliriz.
2-	Business logic içeriyorsa, data manipülasyonu varsa tek satır kod içerse bile fonksiyonları kullanabiliriz.
3-	Birden fazla yerde aynı kod bloklarının çağırıldığını kullanıldığını görüyorsak fonksiyon kullanabiliriz.

__24- Infix fonksiyona neden default değer atayamayız?__
Infix fonksiyonun kullanılma amacı okunaklılığı arttırmaktır. Ancak infix fonksiyona default değer ataması yapabiliyor olsaydık görünüm şu biçimde olurdu;
awesomeInstance downloadImage
Bu örnekte de görüldüğü üzere bu durumda indirilen dosya url’si açık olmadığı için okunaklılığı imkânsız hale getirir. Bu nedenle infix fonksiyonlarda default değer kullanılamaz.
25- Kotlinde işlem önceliği sıralaması ne şekildedir?
1-	Matematiksel işlemler
2-	Tip dönüşümleri
3-	Range kullanımı
4-	Infix fonksiyonlar
5-	Mantık operatörleri

__26- Extension Function nedir?__
Extension Function read-only bir class’ı ya da zaten değiştirmek istemediğimiz üzerine ekleme yapmak istemediğimiz bir class’ı üzerine bir fonksiyon eklenmiş gibi göstermemizi sağlıyor ama gerçekte arka planda bu class’ın bir üye fonksiyonu yaratılmaz. Extension Function’ı Java’da Util fonksiyonlar şeklinde kullanılır. Hangi class extend ediliyorsa o class’ın instance’sini util fonksiyona vererek bir parametre olarak ve o class’la beraber kullanmak isteyeceğimiz diğer parametreyi ya da parametreleri de ikincil, üçüncül parametreler olarak vererek ve o nesne üzerinden nasıl bir işleme tabii tutulacaksa bu fonksiyonları, util fonksiyon üzerinde gerçekleştiriyoruz. Yani Extension Function’lar yeni değil ancak Kotlin bunu fonksiyonel programlama yaklaşımı ile bizlere sunuyor.

__27- Bir Variable’ı nasıl extend edebiliyoruz?__
Kotlin’de değişkenler aslında bir property yani fonksiyondur. Bu nedenle extend edilebilir haldedirler.

__28- Higher Order Function nedir?__
Bir fonksiyona parametre olarak, bir fonksiyon body’si (gövdesi) veriyorsak, bir fonksiyonun geri dönüş tipine bir fonksiyon verebiliyorsak bu durumda o fonksiyona Higher Order fonksiyon diyebiliriz.


Kaynakça

[Kotlinlang.org](https://kotlinlang.org/docs/basic-syntax.html#variables)

[Developer.android.com](https://developer.android.com/kotlin/learn)

[Medium Val is Read-Only](https://freedium.cfd/https://xabaras.medium.com/kotlin-val-is-read-only-not-immutable-585ce2e5359b)

[Medium Type Inference](https://selimselcuk.medium.com/nil-kavram%C4%B1-fc24b81af566)

[Medium Val vs Const Val](https://mujeebkhan1831.medium.com/what-is-the-difference-between-val-and-const-val-in-kotlin-93ac7e18f5fe)

[Medium "==" vs "==="](https://developer.android.com/kotlin/learn)

[Medium Any vs Unit vs Nothing]([https://medium.com/@wandering.soul/unit-vs-nothing-in-kotlin-1083fca51d5c](https://mfallahpour.medium.com/any-nothing-and-unit-in-kotlin-6b0b9779c197))

[Medium Stack ve Heap Kavramları](https://medium.com/t%C3%BCrkiye/stack-ve-heap-kavram%C4%B1-59adcb29d454)














