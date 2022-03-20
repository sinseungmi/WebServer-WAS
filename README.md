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
> - 최종적으로 읽히는 정책이 동작. <br> <br>
>
> <br>
>
> ### Apache Tomcat 구조
> **스크립트란?**
>
>-인터프리트 방식으로 동작하는 컴파일되지 않은 프로그램. 프로그램의 한 라인을 읽어 해석하고 실행하는 과정을 반복하도록 만들어진 프로그래밍 언어로 작성된 컴파일 되지 않은 파일에 저장된 프로그램. <br>
> 쉽게 말하면, 텍스트 형식으로 저장되는 프로그램으로, 한줄씩 순차적으로 읽어 실행되도록 작성된 프로그램!
>
> **CATALINA**
>
> -톰켓은 여러개의 기능(부품)으로 구성한다. 톰캣의 코어 컴포넌트는 카탈리나라고 칭한다.카탈리나는 톰켓의 서블렛 스펙의 실질적인 구동을 제공한다. 톰켓 서버를 가동시킬 경우, 카탈리나를 구동 시킨 것이라 생각하면 된다.
>
> **Class Path**
>
> -클래스패스란 말 그대로 클래스를 찾기위한 경로이다. 자바에서 클래스패스의 의미도 똑같다. 즉, JVM이 프로그램을 실행할 때, 클래스파일을 찾는 데 기준이 되는 파일 경로를 말하는 것이다. 소스 코드(.java로 끝나는 파일)를 컴파일하면 소스 코드가 “바이트 코드”(바이너리 형태의 .class 파일)로 변환된다. java runtime(java 또는 jre)으로 이 .class 파일에 포함된 명령을 실행하려면, 먼저 이 파일을 찾을 수 있어야 한다. 이때 .class 파일을 찾을 때 classpath에 지정된 경로를 사용한다. classpath는 .class 파일이 포함된 디렉토리와 파일을 콜론으로 구분한 목록이다. java runtime은 이 classpath에 지정된 경로를 모두 검색해서 특정 클래스에 대한 코드가 포함된 .class 파일을 찾는다. 찾으려는 클래스 코드가 포함된 .class 파일을 찾으면 첫 번째로 찾은 파일을 사용한다. <br>
>
> <br>
>
> ### **톰캣 디렉토리 구조**
>
> | 디렉토리 | 설명 |
> | --- | --- |
> |/bin |Tomcat Server의 동작을 제어할 수 있는 스크립트 및 실행파일 포함      (sh 파일(유닉스 시스템)과 bat 파일(윈도우 시스템)은 기능적으로 동일하다.) |
> | /conf | 설정 파일과 DTD와 연관된 파일이 존재한다. 가장 중요한 파일인 server.xml이 있으며 이 파일은 컨테이너의 주요 설정 파일이다. |
> | /logs | 서버의 로그 파일이 저장되는 디렉토리이다. |
> | /webapps | 톰캣이 제공하는 웹 애플리케이션의 기본 위치이다. (웹 어플리케이션 루트 폴더) |
> | /lib | classpath에 추가되는 리소스가 위치한 디렉토리이다. |
> | /work | Jsp 파일을 서블릿 형태로 변환한 java 파일과 class 파일이 저장되는 디렉토리이다. |
> | /temp | JVM에 사용되는 임시 디렉토리이다. |
> - bat 파일은 윈도우에서 실행하는 batch 파일, sh 파일은 유닉스 계열에서 실행하는 shell script 파일이다.
>
> <br>
>
> **bin 디렉토리 파일**
> 
> | 파일 | 설명 |
> | --- | --- |
> | bootstrap.jar | Tomcat 서버가 구동될 때 사용되는 main() 메소드가 포함되어 있으며 클래스 로더가 클래스를 구현하는데에 필수적이다. |
> | tomcat-juil.jar | 로깅을 구현하는 java.util.logging API를 포함하고 있는 클래스이다. |
> | common-daemon.jar | Apache Commons Daemon 프로젝트에 필요한 클래스이다. Catalina.sh 파일에 의해 빌드되지 않으며 bootstrap.jar 파일에 의해 참조된다. |
> | catalina.sh | CATALINA 서버의 제어 스크립트이다. |
> | ciphers.sh | 지정된 알고리즘을 사용하는 다이제스트 암호를 설정하는 스크립트이다. |
> | configtest.sh | CATALINA 서버의 설정 스크립트이다. |
> | daemon.sh | Common Daemon에 사용되는 스크립트이다. |
> | digest.sh | 지정된 알고리즘을 사용하는 다이제스트 암호를 설정하는 스크립트이다. |
> | makebase.sh | Tomcat 실행에 필요한 분산 디렉토리 구조를 생성하는 스크립트이다. |
> | setclasspath.sh | JAVA_HOME 또는 JRE_HOME이 세팅되지 않았을 경우 세팅한다. |
> | shutdown.sh | CATALINA 서버를 중지하는 스크립트이다. |
> | startup.sh | CATALINA 서버를 시작하는 스크립트이다. |
> | tool-wrapper.sh | 커맨드 라인 도구에서 사용되는 Wrapper 스크립트이다. |
> | version.sh | Tomcat의 정보를 표시해주는 스크립트이다. |
>
> <br>
>
> **conf 디렉토리 파일**
> 
> | 파일 | 설명 |
> | --- | --- |
> | catalina.policy | Tomcat의 보안 정책을 설정하는 파일이다. Catlina가 –security 옵션으로 실행될 때 시행되는 보안 정책을 설정할 수 있다. |
> | catalina.properties | 서버를 시작할 때 검색하는 서버, 공유 로더, JAR 등의 정보를 포함한다. |
> | context.xml | 세션, 쿠키 저장 경로등을 지정하는 설정 파일이다. |
> | jaspic-providers.xml | 사용자 인증 제공 방법에 대해 정의한 파일 |
> | logging.properties | Tomcat 인스턴스의 로깅 설정 파일이다.tomcat-juli.jar 라이브러리를 활용하여 로깅 서비스를 제공한다. |
> | server.xml | Tomcat 설정에서 가장 중요한 파일이다. Service, Connector, Host 등과 같은 주요 기능을 설정할 수 있다. |
> | tomcat-users.xml | Tomcat의 manager 기능을 사용하기 위해 사용자 권한을 설청하는 파일이다. |
> | web.xml | Tomcat의 환경설정 파일이며 서블릿, 필터, 인코딩 등을 설정할 수 있다. |
>
> <br>
>
> **lib 디렉토리 파일**
> 
> | 파일 | 설명 |
> | --- | --- |
> | annotations-api.jar | 자바EE 어노테이션 클래스 파일 |
> | catalina.jar | Tomcat의 Catalina 서블릿 컨테이너를 구현하는 파일 |
> | catalina-ant.jar | Tomcat Catalina Ant 작업 파일 |
> | catalina-ha.jar | 고가용성 패키지 파일 |
> | catalina-storeconfig.jar | 서버 상태의 흐름을 XML 설정파일로 생성한다. |
> | catalina-tribes.jar | 그룹 커뮤니케이션 패키지 파일 |
> | ecj-*.jar | 이클립스 JDT 자바 컴파일러 파일 |
> | el-api.jar | EL 3.0 API 파일 |
> | jasper.jar | Tomcat Jasper JSP 컴파일러와 런타임 파일 |
> | jasper-el.jar | Tomcat Jasper EL 구현 파일 |
> | jsp-api.jap | JSP 2.3 API 파일 |
> | servlet-api.jar | Servlet 4.0 API 파일 |
> | tomcat-api.jar | Tomcat에 의해 정의되는 몇몇 인터페이스 파일 |
> | tomcat-coyote.jar | Tomcat connector와 유틸리티 클래스 파일 |
> | tomcat-dpcp.jar | 데이터베이스 커넥션 풀을 구현하는 파일 |
> | tomcat-i18n-**.jar | Tomcat 언어 패키지 파일 |
> | tomcat-jdbc.jar | Tomcat JDBC pool로 알려진 대체 데이터베이스 커넥션 풀을 구현하는 파일 |
> | tomcat-util.jar | Apache Tomcat의 다양한 컴포넌트에서 사용되는 일반 클래스 파일 |
> | tomcat-websocket.jar | WebSocket 1.1 구현 파일 |
> | websocket-api.jar | Websocket 1.1 API 파일 |
>
>
> <br>
>
> 요구되는 형태로 웹 어플리케이션 보관소 생성을 용이하게 하기 위해서, 웹 어플리케이션의 "실행" 파일들(즉, 웹 어플리케이션을 실행할 때 톰캣이 사용하는 파일들)을 WAR 형식에서 요구하는 것과 같은 구성으로 정리하는게 편합니다. 이렇게 하려면, 웹 어플리케이션의 "문서 루트 document root" 디렉토리에 다음 내용으로 구성합니다 <br>
>
> - .html, *.jsp, 등. - 웹 어플리케이션에서 클라이언트 브라우저로 전송이 되는 HTML 과 JSP 페이지와 다른 파일들 (예를 들면 자바스크립트, 스타일시트, 이미지 같은). 대규모 어플리케이션에서 이 파일들을 서브디렉토리 체계로 나누어 놓을 수 있습니다. 그러나 규모가 작은 어플리케이션이라면 보통은 하나의 디렉토리에서 전체를 관리하는 것이 보다 단순하고 쉽습니다. <br> 
> - /WEB-INF/web.xml - 웹 어플리케이션의 웹 어플리케이션 배치 설명자 Web Application Deployment Descriptor. 서블릿과 웹어플리케이션을 구성하는 다른 컴포넌트들을 설명하고, 각종 초기화 파라메터들과 서버 기능을 활용하기 위한 컨테이너가 관리하는 보안 제한 구역을 지정하는 XML 파일입니다. 다음 섹션에서 좀 더 자세히 알아보도록 하겠습니다. <br>
> - /WEB-INF/classes/ - 이 디렉토리에는 웹 어플리케이션에서 사용하는 모든 자바 파일(그리고, 관련 자원)이 들어있습니다. 서블릿과 비서블릿 클래스 파일들이며 jar 형태로 묶여있지 않은 것입니다. 패키지가 선언된 클래스라면 /WEB-INF/classes/ 를 기준으로 패키지의 디렉토리를 만들어 구성하면 됩니다. 예를 들어, 클래스명이 com.mycompany.mypackage.MyServlet 라면 파일의 저장경로는 /WEB-INF/classes/com/mycompany/mypackage/MyServlet.class 이 됩니다. <br>
> - /WEB-INF/lib/ - 이 디렉토리에는 웹어플리케이션에서 사용하는 자바 클래스파일을 포함하는 JAR 파일들이 위치합니다. 외부 클래스 라이브러리나 JDBC 드라이버 같은 것들입니다. <br>



   







