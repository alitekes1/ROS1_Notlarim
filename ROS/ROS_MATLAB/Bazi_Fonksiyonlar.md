# Bazı Fonksiyonlar

Fonksiyonları sadece ekranda gösterilmesi için kullanıyorsak tıpkı terminaldeki gibi bir syntax ımız olur. Ama eğer bu fonksiyonlardan dönen değerleri bir değişkende tutmak istiyorsak MATLAB a özel bir şekilde yazmamız gerekiyor.

```matlab
msgData=rosmsg('show','messageName');
actionList=rosaction('list');
```

```cpp
rosinit;//ros sistemini başlatır. eğer başka bir cihazdaki ros a bağlanmak istiyorsak o cihazın id adresini yazmalıyız.
rosshutdown; // ros sistemi ile bağlantıyı sonlandırır.
velocityMsg=rosmessage("geometry_msgs/Twist");//belirtilen tipte message objesi oluşturur.Örneğin bir topic e abone olduk ve yayınlanan mesajı bir değişkende tutmamzı gerekiyor. Bu değişene atayarak tutabiliriz.

```