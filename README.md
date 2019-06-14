# MediaWiki-installation-with-Nginx-MariaDB
Description of Installing MediaWiki using Nginx and MariaDB As Korean
우분투에 엔진엑스와 마리아디비를 통해 미디어위키 엔진을 설치하는 방법
#Ubuntu 16.04.06

 apt-get install nginx //Nginx설치  
 apt-get install mariadb-server//MariaDB설치  
 apt-get install php5-fpm//php설치  
 apt-get install php5-mysql//php와 mysql  

sudo service nginx start || /etc/init.d/nginx start   //nginx시작
sudo service mysql start//mysql시작

ip주소or서버이름을 치거나 뒤에 :80을 붙여 80포트를 보게 되면 Welcome to Nginx가 뜹니다.

Nginx가 잘 실행된 것을 확인할 수 있습니다.

매번 이렇게 브라우저를 통해 들어가는 것이 아니더라도
service nginx status나 service mysql status
를 통해 active(running)이 뜨는지 안뜨는지 확인 할 수 있습니다.

이후 mysql을 들어가서 사용자를 만들고 깔 MediaWiki의 데이터베이스로 사용 될 database를 만듭니다.
잘 만든 후에는 SHOW DATABASES를 통해 데이터베이스가 만들어 졌는지 확인합니다.

