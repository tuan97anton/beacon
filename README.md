# Hướng dẫn sử dụng

// run file scan_one_beacon.cpp
-B1. gcc scan_one_beacon.cpp -lbluetooth -o scan_one_beacon
-B2. sudo setcap 'cap_net_raw,cap_net_admin+eip' scan_one_beacon
B3. ./scan_one_beacon  

// run file scan_all.cpp
-B1. gcc scan_all.cpp -lbluetooth -o scan_all
-B2. sudo setcap 'cap_net_raw,cap_net_admin+eip' scan_all
-B3. ./scan_all 

// run file scan_kalman.cpp
-B1. gcc scan_kalman.cpp -lbluetooth -o scan_kalman
-B2. sudo setcap 'cap_net_raw,cap_net_admin+eip' scan_kalman
-B3. ./scan_kalman  


// node beacon_rssi 
- Subcribe topic /beacon để lấy thông tin rssi và khoảng cách đã sử dụng bộ lọc.
- Bạn có thể  gộp catkin_make và setcap bằng cách sau :
    B1: cd catkin_ws/
    B2: gedit ~/.bashrc
    B3: copy dòng sau vào cuối file : alias aa='catkin_make -DCATKIN_WHITELIST_PACKAGES="beacon_rssi" && sudo setcap 'cap_net_raw,cap_net_admin+eip' ~/catkin_ws/devel/lib/beacon_rssi/beacon_rssi_publisher '
    B4 : source ~/.bashrc
    B5 : aa 
