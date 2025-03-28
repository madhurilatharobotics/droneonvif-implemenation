1.To enable network bridge 
sudo nano /etc/network/interfaces
modify the file 
2.Gsoap installation ans onvif implement
sudo apt install gsoap
sudo apt install libgsoap-dev
3.generating header and source file 
wsdl2h -O4 -P -x -o onvif.h -t /usr/share/gsoap/WS/typemap.dat https://www.onvif.org/onvif/ver10/device/wsdl/devicemgmt.wsdl https://www.onvif.org/ver10/media/wsdl/media.wsdl`
soapcpp2 -2 -I /usr/share/gsoap/import onvif.h`
4.Incase after this if even some soap files are not generated
soapcpp2 -I /usr/share/gsoap/import -2 -x -w -C onvif.h
This command should display the path to stdsoap2.cpp, typically located in /usr/share/gsoap/
find /usr -name "stdsoap2.cpp"
Once located, copy stdsoap2.cpp to your project directory:
cp /usr/share/gsoap/stdsoap2.cpp ~/onvif_server/
