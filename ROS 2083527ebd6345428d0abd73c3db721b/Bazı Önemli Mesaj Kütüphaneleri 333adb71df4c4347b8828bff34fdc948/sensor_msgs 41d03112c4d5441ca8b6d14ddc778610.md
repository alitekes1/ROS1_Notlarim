# sensor_msgs

### *LaserScan*

Genellikle lidar gibi lazer sensorunden veri elde etmek için kullanılır. Yapısında ;

```cpp
std_msgs/Header header       //sensor ile ilgili bilgiler yer alır

float32 angle_min            //taramaya başlanan minumu açı 
float32 angle_max            //taramamnın bittiği maksimum açı
float32 angle_increment      //2 lazer atışı arasındaki açı ( radyan cinsinden )

float32 time_increment       //2 lazer atışı arasındaki zaman 
float32 scan_time            //tarama için gereken toplam süre  

float32 range_min            //sensorun okuyabileceği minumum mesafe
float32 range_max            //sensorun okuyabileceği maksimum mesafe

float32[] ranges             //mesafe verisi dizisi
                            
float32[] intensities        //ışın yansıma şiddeti dizisidir. çok önemli değil
```

### ***Image***

Görüntü verisi üretne sensorlerden verileri iletmek için kullanılır.

```cpp
std_msgs / Header header; // Mesajın başlığı, genellikle zaman damgası ve koordinat çerçevesi bilgisini içerir.
uint32 height;            // görüntü yükseliği
uint32 width;             // görüntünün genişliği
string encoding;          // görüntünün kodlama türü belirtilir. bgr8 rgb8 mono8 gibi türleri bulunur.
uint8 is_bigendian;       // verilerin büyük uçtan mı yoksa küçük uçtan mı düzenlendiğini belirten değer
uint32 step;              // bir görüntü satırının bayt cinsinden tam uzunluğu
uint8[] data;             // görüntünün bgr ye göre renk değerlerini içeren veri dizisi
```