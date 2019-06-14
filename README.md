# MediaWiki-installation-with-Nginx-MariaDB
Description of Installing MediaWiki using Nginx and MariaDB As Korean
우분투에 엔진엑스와 마리아디비를 통해 미디어위키 엔진을 설치하는 방법
#Ubuntu 16.04.06

>apt-get install nginx             //Nginx설치  
>apt-get install mariadb-server    //MariaDB설치  
>apt-get install php5-fpm          //php설치  
>apt-get install php5-mysql        //php와 mysql  

>sudo service nginx start 또는 /etc/init.d/nginx start     //nginx시작
>sudo service mysql start                                 //mysql시작

ip주소or서버이름을 치거나 뒤에 :80을 붙여 80포트를 보게 되면 Welcome to Nginx가 뜹니다.

Nginx가 잘 실행된 것을 확인할 수 있습니다.

매번 이렇게 브라우저를 통해 들어가는 것이 아니더라도  
>service nginx status나 service mysql status  
를 통해 active(running)이 뜨는지 안뜨는지 확인 할 수 있습니다.  

이후 mysql을 들어가서 사용자를 만들고 깔 MediaWiki의 데이터베이스로 사용 될 database를 만듭니다.  
만든 후에는 SHOW DATABASES;를 통해 데이터베이스가 만들어 졌는지 확인합니다.  
데이터베이스를 만든 후에는 아까 만들었던 사용자에게 데이터베이스에 접근 할 수 있도록 권한을 주어야 합니다.  
>GRANT ALL PRIVILEGES ON *.* TO 'USERID'@'%'; // 사용자에게 모든 데이터베이스에 대한 접근 권한을 줌  

여기까지 설정이 되었으면 https://www.mediawiki.org/wiki/Manual:Running_MediaWiki_on_Debian_or_Ubuntu 에 들어가서 매뉴얼을 읽고 따라할 수 있는 조건이 갖춰진 것이다.  

위 사이트에서 도움을 얻을 수 있는 부분은  
>wget이다.  
Ctrl+F를 눌러 wget을 찾아간다. wget부분의 명령어를 통해 ftp등을 사용하지 않고 CLI상의 Ubuntu에 파일을 다운 받을 수 있다. 파일을 다운 받은 후에는 나와있듯이 tar명령어를 통해 압축을 푼다. //tar는 윈도우의 Zip과 같은 압축파일임.  
풀어진 파일은 폴더에 모아/var/www/html아래에 넣어준다. //폴더에 풀면 편함.  
폴더의 이름에 따라 도메인orIP주소/폴더이름/대문이라는 이름으로 뜨기 때문에 보통 w나 wiki등으로 설정한다.  

이후 Apache에는 없는 Nginx만의 설정이 있다.  
Nginx의 같은 경우에는 PHP가 설정되어있지 않기 때문에 PHP를 해석하지 못해 그냥 도메인orIP주소/w/로 들어가면 502가 뜰 것이다.  

이런 경우 이 레퍼지토리에 있는 Nginx.conf를 참고해 /etc/nginx/nginx.conf에 php를 심어주면 된다.  

이후에는 아까 다운받아 놓은 /var/www/html/w/파일 안에 있는 mw-config파일을 열어주기 위해 브라우저에 도메인orIP주소/w를 친다.  
치면 Install MediaWiki라는 창이 뜬다. 이후 차례차례 해주면 된다. DB설정 부분이 안된다면 mysql에 등록된 사용자와 데이터베이스의 문제이다. 잘 넘어가서 마지막 설치단계에서 에러가 뜨면 mysql에 등록된 사용자오 데이터베이스 간의 권한 문제이다.

이렇게 설정을 하면 서버에 Mediawiki엔진을 성공적으로 설치하였다. 나머지 설정은 MediaWiki위키에서 보면서 위키설정들을 커스터마이징 해주면 된다.
