# Kameradan görüntü almak ve göstermek

OpenCv ve cv_bridge paketlerini include ediyoruz.

```cpp
#include "ros/ros.h"
#include "sensor_msgs/Image"//kameradan veri almak için
#include "cv_bridge/cv_bridge.h"//ros ve opencv nin haberleşmesini sağlamak için
#include "opencv2/highgui/highgui.hpp"
#include "opencv2/imgproc/imgproc.hpp"
```

Sensorden gelen verileri cv_bridge kütüphanesine ait olan toCvCopy() fonksiyonunu kullanıyoruz.

[sensor_msgs](../Baz%C4%B1%20O%CC%88nemli%20Mesaj%20Ku%CC%88tu%CC%88phaneleri%20333adb71df4c4347b8828bff34fdc948/sensor_msgs%2041d03112c4d5441ca8b6d14ddc778610.md)

```cpp
bool ObjeNode::callback(const sensor_msgs::Image::ConstPtr &data)
{
    CvImagePtr kamera = toCvCopy(data, sensor_msgs::image_encodings::BGR8);//sensor verisini anlamlandırıyoruz.
    cv::imshow("goruntu", kamera->image);//kameradan alınan veri ekranda gösteriliyor
    return true;
}

ObjeNode::ObjeNode()
{
    sub = nh.subscribe<sensor_msgs::Image>("/camera/rgb/image_raw", 1,callback);//ilgili topic e abone oluyoruz.
}
```