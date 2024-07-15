# Temel komutlar

**pwd** :ilgili klasorun tam adını verir.(print working dictionary)

**mkdir** : dosya oluşturmak (make dictionary)

**cd** klasor_ismi : istenilen klasore gidilir.

**ls** : ilgili klasordeki dosyaları listeler.dosyanın daha detaylı bilgilerinin ls -l ile alınabilir. ls -a ile gizli dosyalar da gözükebilir.

---

### Dosya İşlemleri

yeni bir dosya oluşturmak için **touch dosyaismi.txt** (istenen uzantı olabilir)

txt dosyalarını açmak için nano editörü kullanılır.ilgili klasöre gelindikten sonra **nano dosyaismi.txt** ile istenen dosya nano editorunde açılır. istenirse dosya da bazı değişklikler yapılabilir. ardından ctrl x ile kaydetme ekranı çıkar yes diyince kaydeder.

birden fazla dosyayı birleştirmek için cat komutu kullanılır. **cat dosya1.txt dosya2.txt …** şeklinde kullanılır.

**head -n 15 dosyaismi.txt** : istenen dosyanın baştan ilk 15 satırını gösterir.

**tail -n 15 dosyaismi.txt** : istenen dosyanın sondan ilk 15 satırını gösterir.

**tee dosyaismi.txt** ile kullanıcıdan aldığımız hem dosyaya hemde ekrana yazılır.

---

***echo*** ile terminal ekranını istenilen şey yazdırılabilir. echo “deneme” || echo deneme

---

**history** komutu ile geçmişte yazılan tum komutlar listelenebilir. eski bir komut çalıştırılımak istenirse !komutNo ile tekrardan çalıştırılabilir. !86 gibi

!! ile en son çağırılan komut tekrardan çağırılır.

---

### Process ler

Bir program işlemler toplamıyken ,bir proses bunların gerçek ortamda yürütülmesidir.Linux işletim sisteminde her prosesin bir id değeri vardır.Buna PID (process id) denir. O ank itüm process leri görmek için ps komutu ,son process in id değerini görmek için ise  echo $$ kullanılır. 

![Untitled](images/Temel%20komutlar/Untitled.png)

---

```powershell
history ile geçmiş kodlara bakılabilir.

cd (change dictionary) klasör de değişklik yapmamızı sağlar.
cd .. bir üst dizine dönmemeizi sağlar. cd - bi önceki dizine gitmemizi sağlar.
pwd komutu ile bulunudğumuz konumun yerini söyler
ls Desktop/ ile desktop da bulunan dosyları listeler
ls -a ile gizli dosyaları listeler.
mkdir -p deneme (make dictionary) deneme adında klasör oluşturmamızı sağlar.
touch deneme.txt ile bulunan dizine istenen dosyayı uzantısıyla beraber yazarak oluşturmamızı  sağlar.
cp deneme.txt a ile deneme.txt dosyasını a klasörüne kopyalar
cp -r klasor1 a   ile klasor1 i a klasorüne kopyalar.
mv klasor1 a/ ile kalsor1 i a nın içine taşır.
mv deneme.txt deneme2.txt ile dosyanın adını değiştirebiliriz.
rm deneme.txt ile dosya silinir.
rm -rf ile klasor1 ile klasor silinir.

sudo apt-get install nano ile nano paketini indirme işlemi yapılabilir.
sudo apt-get remove nano ile nano paketini kaldırma işlemi yapılabilir.
sudo apt-get update nano ile nano paketini güncelleme işlemi yapar.
sudo apt-get upgrade nano ile nano paketini güncelleme işleminin kurulumunu yapar.
```