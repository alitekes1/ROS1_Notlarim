# Service (Servis) nedir ve Örnek Kullanımı?

Yalnızca bir istek olduğunda bir yanıt döndüren yapıdır.Bir client ve bir server dan oluşur. Talep - Cevap prensibine dayanır. Mantık olarak parametre alan ve geriye değer döndüren fonksiyonlar ile benzer matnıkta çalışır. ***Bir istek göndeririz ve oda bize yanıt gönderir.*** Yanıt tan sonra aradaki bağlantı kesilir.Server kodunda istek gelene kadar beklemesi için spin() methodunu eklemek gerekiyor.

---

Öncelikle bir srv dosyası tanımlamamız gerekiyor. 

```cpp
int32 num1
int32 num2
---       //msg dosyalarından farkı 3 - işaretidir. üst tarafa input lar alt tarafa outputların veri tipi yazılır.
int32 sum
```

Ardından Server ve Client node ları yazmamız gerekiyor.

```cpp
//SERVER Node
#include "ros/ros.h"
#include "deneme_pkg/add_two_ints.h"// paket ismi/srv dosyaismi.h
using namespace std;

bool add(deneme_pkg::add_two_ints::Request  &req,
         deneme_pkg::add_two_ints::Response &res)
{
  res.sum = req.num1 + req.num2;
  ROS_INFO("request: x=%d, y=%d",req.num1, req.num2);
  return true;
}

int main(int argc, char **argv)
{
  init(argc, argv, "add_two_ints_server");
  NodeHandle nh;

  ServiceServer service = nh.advertiseService("add_two_ints_service", add);
  ROS_INFO("Toplama işlemi hazir");
  spin();

  return 0;
}
```

```cpp
//CLIENT Node
#include "ros/ros.h"
#include "deneme_pkg/add_two_ints.h"// paket ismi/srv dosyaismi.h
#include <cstdlib>

using namespace ros;

int main(int argc, char **argv)
{
  init(argc, argv, "add_two_ints_client");
  if (argc != 3)
  {
    ROS_INFO("usage: add_two_ints_client X Y");
    return 1;
  }

  NodeHandle nh;
  ServiceClient client = nh.serviceClient<deneme_pkg::add_two_ints>("add_two_ints_service");
  deneme_pkg::add_two_ints srv;
  srv.request.num1 = atoll(argv[1]);
  srv.request.num2= atoll(argv[2]);
  if (client.call(srv))
  {
    ROS_INFO("Sonuc: %d", srv.response.sum);
  }
  else
  {
    ROS_ERROR("Basaramadik!");
    return 1;
  }

  return 0;
}
```

Ardından cmakelist.txt de bazı düzenlemeler yapmalıyız.Sonra da catkin_make yaptıktan sonra service imiz hazır.

![Untitled](Service%20(Servis)%20nedir%20ve%20O%CC%88rnek%20Kullan%C4%B1m%C4%B1%20cf886159306246fc8cb15146d0f30ff8/Untitled.png)

![Untitled](Service%20(Servis)%20nedir%20ve%20O%CC%88rnek%20Kullan%C4%B1m%C4%B1%20cf886159306246fc8cb15146d0f30ff8/Untitled%201.png)

![Untitled](Service%20(Servis)%20nedir%20ve%20O%CC%88rnek%20Kullan%C4%B1m%C4%B1%20cf886159306246fc8cb15146d0f30ff8/Untitled%202.png)