# win10、Ubuntu 蓝牙共用

1. win10下连接

2. Ubuntu下连接

3. cat /var/lib/bluetooth/电脑蓝牙Mac地址/设备蓝牙Mac地址/info

4. 记录[linkKey]下Key值

5. 使用PSTools，cmd=PsExec.exe -s -i regedit，找到[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\BTHPORT\Parameters\Keys\]，写入Key值
