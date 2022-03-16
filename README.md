> # 🌐 WebServer-WAS
> 
> <br>
>
> ### 정적 페이지 (Static Page)
> - 데이터베이스에서 정보를 가져오거나 별도의 서버에서의 처리가 없어도, 사용자들에게 보여줄 수 있는 페이지. 어떠한 사용자가 오던간에 동일한 페이지를 보여줍니다. <br>
> - 정적인 요소에는 Html, Css, Js, Image 같은 요소들이 있습니다. Js는 클라이언트 단에서 Html과 Css 와 같은 요소들을 컨트롤 하는데 쓰입니다. <br>
> <br>
>
> ### 동적 페이지 (Dynamic Page)
> - 서버에서 데이터베이스에서 정보를 가져와서 처리하는 것처럼, 어떠한 요청에 의하여 서버가 일을 수행하고 해당 결과가 포함된 파일을 보여주는 페이지. 사용자들마다 다른 페이지가 보여질 수 있습니다.
> <br>
>
> ### 웹 서버
> - 웹 서버는 클라이언트가 요청한 정적인 콘텐츠를 HTTP 프로토콜을 통하여 제공해주는 서버입니다. 정적 페이지를 보내줍니다. 정적인 콘텐츠 제공 이 가장 큰 역할입니다. <br>
> - 다른 역할으로는 동적인 요청이 클라이언트로부터 들어왔을 때, 해당 요청을 웹 서버에서 처리할 수 없기 때문에 컨테이너(Container)로 보내주는 역할을 합니다. <br>
> - 웹 서버에는 Nginx, Appach HTTP Server, IIS가 있습니다.
> <br> <br> 
>
> ### 컨테이너 (Container)
> - 컨테이너는 동적인 데이터들을 처리하여 정적인 페이지로 생성해주는 소프트웨어 모듈 입니다. <br>
> - 사용자가 로그인해서 My Page 메뉴에 들어간다고 가정해보겠습니다. 이 메뉴에서는 각자 사용자에 따라 보여질 정보가 다릅니다. 사용자의 요청이 들어오면 웹 서버는 정적인 요소만 클라이언트 측에 보낼 수 있고, 동적으로 처리해야 하는 부분은 처리할 수 없습니다. 컨테이너는 이러한 부분을 대신 처리해서 웹 서버에 정적인 파일로 만들어서 보내주는 모듈입니다. <br>
> - 클라이언트 측에서 크롬 개발자 도구를 이용하여 파일을 살펴보면 php, ejs 파일도 만든 소스코드도 전부 html로 전송됩니다. 이는 해당 파일에서 처리해야할 부분을 처리하고 정적 파일로 만든 후에 클라이언트에게 보냈다고 생각하면 좋을 것 같습니다. <br>
> - 자바 기반의 서버에서는 서블렛이라는 용어도 많이 사용 <br>
>
> <br>
> 
> ### WAS (Web Application Server)
> - 웹 서버로부터 오는 동적인 요청을 처리하는 서버를 말합니다. 웹 서버와 컨테이너를 붙여놓은 서버 라고 보시면 될 것 같습니다. <br>
> ![79986821-0AE3-4389-83E8-4AFC4FD2EABF](https://user-images.githubusercontent.com/76691954/158160745-245758e0-bdb4-4924-9866-12d9caddd7cf.jpeg) <br>
> - 예를 들어서, 클라이언트에서 http://caffelove.com 이라는 도메인을 가진 서버에서 ‘내 정보’를 눌러 http://caffelove.com/myinfo 라는 경로에 들어간다고 가정해보겠습니다. <br> 내 정보를 볼 수 있는 홈페이지라고 하겠습니다. 환경은 node.js 라고 가정하겠습니다. <br> /myinfo 라는 경로로 요청하면 WAS는 자신의 라우팅 정보를 통하여 어떤 처리를 해야될지 살펴봅니다. 이 때, myinfo를 라우팅 할 때, ‘myinfo.html 이라는 파일을 보여줘!’ 라는 요청을 하게 된다면 정적인 요소이기 때문에, 웹서버에서 클라이언트에게 myinfo.html 파일을 보내주기만 하면 됩니다.  관련된 Css, Js, Image 파일도 함께요. <br> 하지만, myinfo는 자신의 정보를 보여주는 페이지이니 위처럼 반응하지 않겠죠. WAS에서는 대게 먼저 데이터베이스에서 데이터를 가져옵니다. <br> 그 다음에 원하는 데이터를 가공하여, myinfo.ejs 파일로 해당 데이터를 보내줍니다. .ejs파일에서는 node.js 에서의 변수나 정보를 사용할 수 있게 만들어 놓았습니다. <br> 정보를 넣어야 할 곳에 데이터베이스에서 가져온 정보를 넣고, ejs 파일을 html 로 바꿔준 다음에 웹서버로 전송합니다. (node.js 의 Javascript와 클라이언트의 UI를 동적으로 보여주는 Javascript는 다른 것이니 유의해서 봐주세요!) <br> 웹 서버는 위의 html 요소를 클라이언트에게 다시 보내주는 것이죠. WAS에 Tomcat, Jeus 같은 것들이 있다고 합니다. <br>
> 
> <br>
>
>
> ### Apache(아파치) httpd.conf(설정파일)
> #### httpd.conf
> - 기본 설치 시 경로는 /etc/httpd에 설치가 되며, 설정 파일은 /etc/httpd/conf 경로의 httpd.conf 파일이 존재한다. <br>
>   /etc란?
>   - /etc와 /usr/etc 디렉토리는 시스템의 부팅, 셧다운 시에 필요한 파일들과 시스템의 전반에 걸친 설정 파일들 및 초기 스크립트 파일들이 있다. 시스템에 어떠한 문제가 발생한다거나, 시스템 전체 환경에 관한 설정을 바꾸기 위해서는 이들 디렉토리내에 포함되어 있는 파일들에 대하여 잘 알아야 한다. <br>
> #### httpd.conf값
> 1. ServerRoot <br>
> -아파치의 기본 Root 경로이며, 절대경로로 설정해주어야 한다. <br>
> 2. timeout [300 : default] <br>
> -클라이언트와 서버 간에 300초(5분) 동안 아무런 메시지가 발생하지 않으면 타임아웃을 시키고 연결을 끊는다. <br>
> 3. KeepAlive [On : default / Off] <br>
> -특정 클라이언트의 지속적인 요청 작업들을 계속해서 처리하도록 허용할 것 인가 아닌가에 대한 여부를 설정한다.(서버 요청이 많고 메모리를 많이 잡아먹는다면 Keepalive off 하는 것이 좋다.) <br>
> 4. KeepAliveTimeout [5 : default] <br>
> -KeepAlive가 On인 경우 유효한 값으로, 설정 시간(초)동안 요청이 없으면 타임아웃 시킵니다. <br>
> (낮을수록 동시접속 수를 늘릴 수 있습니다.) <br>
> 5. MaxKeepAliveRequests [100 : default] <br>
> -Keepalive 값이 On인 경우 클라이언트와 연결된 작업의 최대 개수를 100개로 제한한다. 해당 회수를 초과하면 현재 프로세스는 종료되고 다른 프로세스가 처리한다. (0으로 설정하면 무제한 요청이 허용됩니다.) <br>
> 6. Directoryindex index.htm, index.html, index.php <br>
> -웹 디렉토리 접근 시 인식되는 인덱스 파일의 순서를 index.htm, index.html, index.php 순으로 지정한다. <br>
> 7. Listen 1120 <br>
> -사용할 포트 지정 <br>
> 8. ServerName [www.example.com : default] <br>
> -서버의 도메인을 입력(도메인이 없다면 IP주소라도 꼭 적어야 한다.) <br>
> 9. UseCanonicalName [Off : default / On] <br>
> -On : 지정한 ServerName 를 사용합니다 <br>
> -Off : 호스트네임과 포트를 사용합니다. <br>
> 10. DocumentRoot "/var/www/html/webadmin" <br>
> -웹 문서가 위치하는 디렉토리를 지정 <br>
> 11. SeverAdmin dukkoong@gmail.com <br>
> -서버 관리자 이메일을 입력 <br>
> 12. ExtendedStatus [Off : default / On] <br>
> -Apache의 상태를 모니터링 할 때, 자세한 상태정보 기능을 제공할 것 인지에 대한 설정입니다. <br>
(server-status에 영향을 줍니다.) <br>
> 13. User [apache : default] Group [apache : default] <br>
> -Apache 자식 프로세스들의 실행소유자와 소유그룹을 설정하는 값입니다. <br>
(보안을 위해 nobody로 설정합니다.) <br>
> 14. NameVirtualHost [*:80] <br>
> -이름기반 가상 호스트를 사용하겠다는 설정입니다 <br>
> 15. <VirtualHost *:80> ~ </VirtualHost> <br>
> -ServerAdmin : 해당 가상호스트의 관리자 이메일 주소 <br>
> -DocumentRoot : 해당 가상호스트의 홈페이지디렉토리 위치 <br>
> -ServerName : 해당 가상호스트의 도메인명 <br>
> -ErrorLog : 해당 가상호스트의 웹에러로그 파일 위치 <br>
> -CustomLog : 해당 가상호스트의 웹로그파일 위치 <br>
> 
> <br>
>
> #### http 접근제어 
> ```
> <Directory "/www/html/admin"> <br>
> Order Deny,Allow <br>
> Deny from All <br>
> Allow from 192.168.2.0/24 <br>
> </Directory>
> ```
> - Order : Deny와 Allow 의 순서를 정한다. <br>
> - Allow,Deny 또는 Deny,Allow 둘 중에 하나를 적는다. <br>
> - 최종적으로 읽히는 정책이 동작. <br>




   







