# ROS Nedir?

Ros yapı olarak düğüm- mesaj - konu - servis ana konseptlerinde oluşur.

Düğüm proseslerin işlendiği yerdir.bu düğümler arasındaki haberleşme mesajlar ile gerçekleşmektedir.Mesajlar konular üzerinden aktarılmaktadır.Konular yayıncı-abone yapısında haberleşmektedir.bundan dolayı konular asenktron haberleşme sağlamaktadır.Yani belli bir sıra yoktur. Farklı görevler aynı anda gerçekleşebilmektedir.

![Untitled](images/ROS_Nedir%20/Untitled.png)

![Untitled](images/ROS_Nedir%20/Untitled%201.png)

package.xml dosyasında herbir pakedin lisans bilgileri bağımlılıkları derleyici işaretleri gibi bilgileri saklanır.

Birçok paket birleşerek yığınları oluşturur.

### Mesaj Tipleri

Farklı farklı düğümleri ile haberleşmemiz için önceden tanımlanmış mesaj tiplerini kullanırız.Eğer biz yeni bir mesaj tipi tanımlamak istiyorsak msg klasorundeki .msg uzantılı yeni bir mesaj tipi ekleyebiliriz.

### Servis Tipleri

Ros daki servislerin haberleşmesi için kullanılan servis tipleridir. Mesaj tipleriyle benzer özellikleri taşır. Yeni bir servis tanımlayacaksak srv klasoründeki .srv uzantılı olacak şekilde yeni bir tanımlama ypaılması gerekmektedir.

---

![Untitled](images/ROS_Nedir%20/Untitled%202.png)