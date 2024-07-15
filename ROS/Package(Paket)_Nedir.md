# Package(Paket) Nedir?

içerisinde klasör hiyerarşisine uygun olacak şekilde ;

- node ların yer aldığı ***src*** ve ***scripts*** klasorleri bulunur ve içerisinde cpp ve py uzantılı dosyalar yer alır.
- c++ header dosyalarının bulunduğu ***include*** klasorleri bulunur.
- çalıştırılacak nodeların bilgilerinin yer aldığı ***launch*** dosyası yer alır.
- package ile ilgili tüm bilgi ve diğer bağımlılıklarının bilgileri yer alan ***package.xml*** dosyası bulunur.
- ***CMakeLists.txt*** dosyasında cmake derleyecisi için gerekli talimatlar yer alır.
- Topic lere gönderilen mesajların yer aldığı ***msg*** klasorunu içerir.
- ***srv*** ***klasörü***, bir ROS düğümünden diğerine özel görevler gerçekleştirmesi için talepte bulunma ve bu taleplere cevap verme mekanizmasını sağlarlar. Servisler, genellikle bir düğümün başka bir düğüme belirli bir işlemi gerçekleştirmesi için bir talepte bulunmasını ve bu işlemin sonuçlarını almasını sağlar.