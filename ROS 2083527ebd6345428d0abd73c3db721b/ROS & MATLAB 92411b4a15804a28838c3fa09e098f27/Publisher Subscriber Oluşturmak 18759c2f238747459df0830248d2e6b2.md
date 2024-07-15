# Publisher Subscriber Oluşturmak

```matlab
pub = rospublisher('/topic_name', 'MessageType');%% publish edilecek topic name ve publish edilen verinin tipini belirtiyoruz.
publishMessage=rosmessage(pub);%% publish edilecek veriye uygun message oluşturuyoruz.
publishMessage.property=0.5;%% şeklinde mesajın içeriğini oluşturuyoruz.
send(pub,publishingData);%% publisher ı ve publish edilen veriyi topic e gönderiyoruz.

pub=rospublisher("topicName","messageType");%% yayın yapılacak topic in ismi ve bu topic e yayınlanacak olan mesajın tipi 
%%eğer bu şekilde bırakırsak yayınlanan mesaj matlab struct yapısı şeklinde
%%iletilir. bunun yerine 
pub1=rospublisher("topicName","messageType","DataFormat","object");%%şeklinde yaparsak belirttiğimiz mesaj tipine uygun olarak 
%%yayın yapılır.
```

### 5 sn boyunca 0.5 hızda ilerleyen robot

```cpp
pub2=rospublisher("/turtle1/cmd_vel","geometry_msgs/Twist");//ilgili topic e ve bu topice yayınlanacak olan mesaj tipini belirtiyoruz.
hizMessage=rosmessage(pub2);//yayınlanacak veritipine uygun mesaj oluşturuyoruz.
hizMessage.Linear.X=0.5;//mesajın içeriğini oluşturuyoruz.
tic;//zamanlayıcı
sub = rossubscriber("/turtle1/pose","turtlesim/Pose",@callbackFunction);//istenen topic e abone oluyoruz.mesaj tipini belirtiyoruz.ve her mesaj geldiğinde çalışacak olan fonksiyonun ismini belirtiyoruz.
while toc<5
send(pub2,hizMessage);//oluşturduğumuz mesaj ı topic e yayınlıyoruz.
end

function callbackFunction(src, msg)//subscriber dan daima bu mesajı yayınlayan ve mesajın kendisi gelir.
    //mesajı istediğimiz şekilde kullanabiliriz.çeşitli matematiksel işlemler yapabiliriz. vs vs
		disp('Turtle''ın Konumu:');
    disp(['X: ', num2str(msg.X)]);
    disp(['Y: ', num2str(msg.Y)]);
    disp(['Theta (Yön): ', num2str(msg.Theta)]);
end
```