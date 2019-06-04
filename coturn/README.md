# docker coturn

請事先下載coturn源碼
https://github.com/coturn/coturn/archive/4.5.1.1.tar.gz

Coturn WebRTC stun/turn Server

指令:

mysql connect : host=127.0.0.1 dbname=coturn user=coturn password=c7oturnW# port=3306 connect_timeout=30 read_timeout=30

turnadmin -a [-b <sqlite-db-file> | -e <db-connection-string> | -M <db-connection-string>  | -N <db-connection-string> ] -u <username>	-r <realm>  -p	<password>
turnadmin -a -M "host=127.0.0.1 dbname=coturn user=coturn password=c7oturnW# port=3306 connect_timeout=30 read_timeout=30" -u online -u online -p online
"host=localhost dbname=coturn user=coturn password=coturn port=3306 connect_timeout=5 read_timeout=15"
turnadmin -A -u jason -p jason -M "host=localhost dbname=coturn user=coturn password=c7oturnW# port=3306 connect_timeout=5 read_timeout=15"