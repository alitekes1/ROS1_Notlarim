# geometry_msgs

## Twist

Linear ve angular olmak üzere 2 farklı vektörden oluşur.Vektör tipleri x y z bileşenlerinde oluşur.

```cpp
 linear:
  x: 0.5  # X ekseni boyunca 0.5 m/s lineer hız
  y: 0.2  # Y ekseni boyunca 0.2 m/s yanlama hızı
  z: 0.1  # Z ekseni boyunca 0.1 m/s yükseklik değişimi
angular:
  x: 0.0
  y: 0.0
  z: 0.3  // Z ekseni etrafında 0.3 rad/s açısal hız
//genellikle açısal hız yani dönme hareketleri için bu değer kullanılır.

geometry_msgs::Twist example_twist;
twist.linear.x=0.1;
twist.angular.z=0.5;//radyan cinsinden değer alır
```

![Untitled](geometry_msgs%20fa2f58b2dfec48958d38a1f9a9e2b3da/Untitled.png)

 

derecenin radyan karşılığı derece*pi/180 = radyan ile bulunur. Mesela bir robotun sağa doğru 30 derece dönmesini istiyoruz. Bunun için ilk önce angular.z değerinin pozitif(saat yonunda olduğu için) olacağının bilmeliyiz. ardından yukarıdaki formulden veya direkt açı değerini 0,1745 ile çarparak radyan karşılığını buluruz ve atarız. bu sayede robot 30 derece sağa sadece döner. eğer o yönde hareket etmesini istiyorusak linear.x değerini vermeliyiz.

---