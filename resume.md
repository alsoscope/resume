### 23. 마지막 - API와 CreateServer

#### API(Application Programming Interface)

- fs.readFile 함수 : 파일을 읽을 때 사용한다

  이러한 것을 __Interface__ 라고 한다.<br>
  이 인터페이스를 실행함으로써 어플리케이션을 만들 수 있다.<br>
  
  어플리케이션을 프로그래밍하기 위해 제공하는 인터페이스를 **API** 라고 한다.<br>
  언어가 가진 조작장치가 궁금하다면 API를 찾아본다.

- nodejs 의 공식 API 문서 확인

- `http.createServer([options][, requestListener])` 는 HTTP 모듈이면서 객체이다.

  createServer라는 함수가 객체 안에 있을 땐 메소드라고도 한다.<br>
  인자로 requestListener가 있다.<br>
  인자가 있을 수도, 없을 수도 있다는 대괄호의 의미. 생략가능. []

  -  `requestListener <Function>` 함수이기 때문에,
  
          var app = http.createServer(function(request,response){}
      
      인자로 많은 함수를 작성할 수 있는 것이다.

      웹 서버를 만들어 외부에서 요청이 들어올 때 마다,<br>
      첫 번째 인자에 해당되는 함수function(request, response){}를 호출하면서<br>
      그 함수의 첫 번째 파라미터로는 웹 브라우저로 들어오는 요청에 대한 여러가지 정보를 담고있는 객체인 request 인자로 주기로 약속 함.

      두 번째 파라미터 값으로 함수 안의 구현을 통해 사용자에게 전송하고 싶은 정보를 response를 통해 응답할 수 있다.<br>
      그러기 위해 response 객체를 넘겨주는 것.

      - 처리가 성공하거나 실패했을 때

            response.writeHead(200);
            response.end(html);

        이러한 약속에 따라 요청한 정보와 응답할 정보로 웹 어플리케이션을 만드는 것이다.

- `Returns: <http.Server>` 리턴값으로 http.Server 값을 반환한다.<br>
var app 이라는 변수에 http.Server 객체가 담겨있는 것이다.

      http.Server API
      app.listen(3000);

- listen은 무엇인가

    server.listen()

Starts the HTTP server listening for connections. This method is identical to server.listen() from net.Server.

요청에 대해 응답할 수 있게 HTTP 서버를 구동시킨다.<br>
이 listen API는 server.listen() 이라는 net.Server. 의 또다른 모듈과 같은 것이다.

- server.listen()<br>
Start a server listening for connections. A net.Server can be a TCP or an IPC server depending on what it listens to.

    Possible signatures:

    - signatures:<br>
      함수의 형태, 이름, 들어오는 인자나 리턴값 같은 형식들을 시그니처라 한다.

      현재 사용하고 있는 것은 마지막 시그니처에 해당하는 것이다. 포트가 들어가는 것.

          server.listen([port[, host[, backlog]]][, callback])

          app.listen(3000);

      3000번 포트. localhost:3000 로 접속하면 어플리케이션을 응답한다.
