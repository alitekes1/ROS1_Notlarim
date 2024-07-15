# Özel Message (.msg) dosyaları ve Paket üzerinde kullanımı

Yayıncı ve abonelerin mesajlar yardımıyla haberleşmesini sağlayan .msg uzantılı basit metin dosyalarıdır. Paket içerisinde msg klasorunun içerisinde bulunması tavsiye edilir.

Birçok tipte mesaj yayınlayabileceğimiz gibi farklı msg dosyalarınıda bir mesaj tipi gibi kullanabiliriz

```cpp
int8 sayi1
int32 sayi2
float64 sayi3
string name
array[] months 
```

Bir message dosyası oluşturmak için paket içierisinde msg dosyasının içinde .msg uzantılı bir dosya oluşturuyoruz. ardından bu dosyaya istediğimiz veri tiplerini ve bu değişkenin adının yazıyoruz. Her değişken tek satırda olmasına dikkat ediyoruz.generate_messages kütüphanesi eklememizin sebebi kendi msg dosyamızı bu kütüphane sayesinde oluşturuyoruz.

![Untitled](images/Message_(msg)_dosyalari_ve_Paket_Uzerinde_Kullanimi/Untitled.png)

![Untitled](images/Message_(msg)_dosyalari_ve_Paket_Uzerinde_Kullanimi/Untitled%201.png)

***Ardından package.xml ve cmakelist dosyalarında bazı değişiklikler yapmalıyız.*** 

Bunlar cmakelist te

- find_package() fonksiyonuna message_generation ı eklemek
    
    ![Untitled](images/Message_(msg)_dosyalari_ve_Paket_Uzerinde_Kullanimi/Untitled%202.png)
    

- add_message_files() fonksiyonuna oluşturduğumuz mesaj dosyasını uzantısıyla beraber eklemek

![Untitled](images/Message_(msg)_dosyalari_ve_Paket_Uzerinde_Kullanimi/Untitled%203.png)

- generate_messages() fonksiyonuna std_msgs pakedini eklemek

![Untitled](images/Message_(msg)_dosyalari_ve_Paket_Uzerinde_Kullanimi/Untitled%204.png)

- catkin_package() a da message_runtime ı eklemek

![Untitled](images/Message_(msg)_dosyalari_ve_Paket_Uzerinde_Kullanimi/Untitled%205.png)

Package.xml de 

- build_depend olarak message_generation
- build_export_depend olarak message_runtime eklemek
- exec_depend olarak message_runtime eklemek

![Untitled](images/Message_(msg)_dosyalari_ve_Paket_Uzerinde_Kullanimi/Untitled%206.png)

---

İlk olarak yukarıdaki işlemleri yaptıktan sonra mesaj dosyamız oluşmuş oluyor. Ardından publisher ve subscriber node umuza eklememiz çok kolay olacak.Dikkat etmemiz gereken nokta bu mesaj dosyasını kullanacağımız yerde ***paket_ismi::mesaj_dosya_ismi*** ikilisini kullanacağız.

```cpp
//PUBLISHER NODE 
#include "ros/ros.h"
#include "deneme_pkg/adsoyad.h"//mesaj dosyamızın .h uzantılı dosyasının ekliyoruz.

using namespace ros;//bu sayede ros:: yazmaya gerek kalmaz.ama genelde kullanırlar.
int main(int argc,char**argv){

	ros::init(argc,argv,"publisher_deneme");

	NodeHandle nh;
	
	ros::Publisher pub=nh.advertise<deneme_pkg::adsoyad>("topic_deneme",10);
	ros::Rate rate(1);

	while(ros::ok()){
		deneme_pkg::adsoyad mesaj;
		mesaj.name="Ali";
		mesaj.surname="Tekeş";
		mesaj.age=19;
		ROS_INFO("Mesaj topic e gonderildi: %s %s %d",mesaj.name.c_str(),mesaj.surname.c_str(),mesaj.age);
		pub.publish(mesaj);
		rate.sleep();
	}
	return 0;
}
```

```cpp
//SUBSCRIBER NODE 
#include "ros/ros.h"
#include "deneme_pkg/adsoyad.h"//mesaj dosyamızın .h uzantılı dosyasının ekliyoruz.

using namespace ros;//bu sayede ros:: yazmaya gerek kalmaz.ama genelde kullanırlar.

void callback(const deneme_pkg::adsoyad::ConstPtr &msg){
		ROS_INFO("Gelen mesaj: %s - %s - %d",mesaj.name.c_str(),mesaj.surname.c_str(),mesaj.age);

}

int main(int argc,char**argv){
	ros::init(argc,argv,"subscriber_deneme");
	NodeHandle nh;
	ROS_INFO("Subscriber calisti");//1 defa yazılır.
	Subcriber sub=nh.subscribe("topic_deneme",10,callback);//her data geldiğinde çağırılacak olan fonksiyonu veriyoruz.
	ros::spin();//işlemin sürekli devam etmesi için
return 0;
```

![Untitled](images/Message_(msg)_dosyalari_ve_Paket_Uzerinde_Kullanimi/Untitled%207.png)