# Hướng dẫn sử dụng

[Cài đặt thư viện]

    - Thư viện Bluez :https:https://learn.adafruit.com/install-bluez-on-the-raspberry-pi/installation
    - Thư viện libbluetooth-dev : sudo apt-get install libbluetooth-dev
    - Thư viện libncurses5-dev  : sudo apt-get install libncurses5-dev
    
[Folder: beacon_scan ]

    1.File scan_one_beacon.cpp : Đọc rssi của 1 beacon
    - B1. gcc scan_one_beacon.cpp -lbluetooth -o scan_one_beacon
    - B2. sudo setcap 'cap_net_raw,cap_net_admin+eip' scan_one_beacon
    - B3. ./scan_one_beacon  

    2.File scan_all.cpp : Đọc rssi của các beacon tìm được
    - B1. gcc scan_all.cpp -lbluetooth -o scan_all
    - B2. sudo setcap 'cap_net_raw,cap_net_admin+eip' scan_all
    - B3. ./scan_all 

    3.File scan_kalman.cpp : Đọc rssi của 1 beacon đã qua bộ lọc Kalman
    - B1. gcc scan_kalman.cpp -lbluetooth -o scan_kalman
    - B2. sudo setcap 'cap_net_raw,cap_net_admin+eip' scan_kalman
    - B3. ./scan_kalman  
[Folder: beacon_rssi]

    - Node beacon_rssi được viết trên ROS.
    - Subcribe topic /beacon để lấy thông tin rssi và khoảng cách đã sử dụng bộ lọc.
    - Bạn có thể  gộp catkin_make và setcap bằng cách sau :
        B1: cd catkin_ws/
        B2: gedit ~/.bashrc
        B3: copy dòng sau vào cuối file : alias aa='catkin_make -DCATKIN_WHITELIST_PACKAGES="beacon_rssi" && sudo setcap 'cap_net_raw,cap_net_admin+eip' ~/catkin_ws/devel/lib/beacon_rssi/beacon_rssi_publisher '
        B4 : source ~/.bashrc
        B5 : aa 

[Folder: images ]

    - Thí nghiệm với 5 beacon với thông sô : TxPower = 4dBm , Broadcasting Interval = 100 ms, Measured Distance = -59 dBm ) , 5 beacon đặt trên mặt phẳng, với khoảng cách giữa các beacon trong 2 bài test được thể hiện trong 2 ảnh TEST1.PNG và TEST2.PNG .
    - Board Jetson TK2 đặt trên mô hình xe 
        + Bài test 1 : Xe bắt đầu ở vị trí Beacon 1, đi theo hướng mũi tên , mỗi quang đường tương ứng với 1 biểu đồ dữ liệu trong file bieudo.ods ( ex: dữ liệu quãng đường 1 tưỡng ứng biều đồ FILE1 )
        + Bài test 2 : Xe đi theo hướng mũi t

