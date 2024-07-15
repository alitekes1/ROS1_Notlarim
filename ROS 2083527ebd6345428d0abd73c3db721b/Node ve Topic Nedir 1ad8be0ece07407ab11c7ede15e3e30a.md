# Node ve Topic Nedir ?

Ros da c++ veya python ile yazılan her biri belli bir görevi yerine getiren birimdir.Mesela a düğümü lidar sensöründen veriler alır ve bunu bir topic e yayınlar. Bu sayede diğer düğümlerin bu sensörden elde ettiği veriler kullanabilir hale gelir. Bir işyerindeki çalışan bir kişi olarak düşünülebilir.    

İşleyiş şekli ise bir node bir topic e bir yayın yapar ve bu alıcıdan bağımsızdır. Bu topic e abone olan herkes bu yayınlanan mesajı alabilir.

![Untitled](Node%20ve%20Topic%20Nedir%201ad8be0ece07407ab11c7ede15e3e30a/Untitled.png)

Buradaki Publisher ve Subscriber birer Node dur. ve bunlar c++ veya python ile yazılabilir.Aşağıda örnek bir publisher nodu bulunmaktadır.

```cpp
//PUBLISHER NODE 
#include "ros/ros.h"
#include "std_msgs.h"

using namespace ros;//bu sayede ros:: yazmaya gerek kalmaz.ama genelde kullanırlar.
int main(int argc,char**argv){

	ros::init(argc,argv,"publisher");

	NodeHandle nh;
	
	ros::Publisher pub=nh.advertise<std_msgs::String>("subpub_topic_cpp),10);
	ros::Rate rate(1);

	while(ros::ok()){
	std_msgs::String msg;
	msg.data="Yayinlanacak olan data bu ifadedir.";
	pub.publish(msg);
	rate.sleep();
	}
	return 0;
}
```