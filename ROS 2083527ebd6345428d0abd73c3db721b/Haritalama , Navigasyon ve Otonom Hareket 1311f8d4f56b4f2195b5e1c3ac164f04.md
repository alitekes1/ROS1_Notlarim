# Haritalama , Navigasyon ve Otonom Hareket

Aracın bulunduğu ortamı haritalandırmak ve bu haritalandırdığı map i kullanarak otonom bir şekilde hareket etmesini sağlamak için navigation ve slam paketini kullanırız.

Bunun için navigation ve slam paketi indirilmesi gerekiyor.

```powershell
sudo apt-get install ros-noetic-navigation
sudo apt-get install ros-noetic-slam
```

Ardından ortamın haritası çıkarmak ilk önce ortamın haritasını çıkartmamız gerekiyor. Bunun için 

```powershell
roslaunch turtlebot3_slam turtlebot3_slam
```

dosyası çalıştırılmalı ve ardından robotun teleop topicine mesaj yayınlayarak hareket etmesi ve ortamın haritasını çıkarmasının sağlanması gerekiyor. 

![ali.png](Haritalama%20,%20Navigasyon%20ve%20Otonom%20Hareket%201311f8d4f56b4f2195b5e1c3ac164f04/ali.png)

Ardından bu haritanın map klasorune kaydedilmesi gerekiyor. Bunun için 

```powershell
rosrun map_server map_saver -f home/tekes/calisma_ws/src/calisma_pkg/map/ali
```

map_server paketi ile map i pmg ve yaml şekilde istediğimiz klasore kaydedebiliriz. -f ile konumunu belirtiyoruz. son parametre dosyanın ismidir. (ali.pgm ve ali.yaml oluşacak).

Bu kaydettiğimiz map i kullanmak ve otonom hareket etmesini sağlamak için  navigation paketindeki  turtlebot3_navigation.launch dosyasında bu oluşan haritanın yaml dosyasını belirtmemiz gerekiyor. Dosyanın konumu:turtlebot3_navigation/home/tekes/calisma_ws/src/turtlebot3/turtlebot3_navigation/launch

![Untitled](Haritalama%20,%20Navigasyon%20ve%20Otonom%20Hareket%201311f8d4f56b4f2195b5e1c3ac164f04/Untitled.png)

Ardından paketi çalıştırılır ve aracın bulunduğu konum ile map in eşleştirilmesi gerekiyor. 

```powershell
roslaunch turtlebot3_navigation turtlebot3_navigation 
```

Bunun için rviz deki estimate butonu ile robotun gazebodaki konumu belirtilir.  

Robot konumunu sağladıktan sonra etrafındaki yeşiller yok denecek kadar az kalır. 

![Untitled](Haritalama%20,%20Navigasyon%20ve%20Otonom%20Hareket%201311f8d4f56b4f2195b5e1c3ac164f04/Untitled%201.png)

Bu işlemden sonra navigation buton ile robotun istenen hedef konumu ve yonu belirtilir. 

![Untitled](Haritalama%20,%20Navigasyon%20ve%20Otonom%20Hareket%201311f8d4f56b4f2195b5e1c3ac164f04/Untitled%202.png)

VEEEE robot otonom bir şekilde istenen konuma ulaşır.