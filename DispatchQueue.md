## DispatchQueue

* serial: 하나의 작업이 **끝나고** 나서 다른 작업을 실시
  * main dispatchqueue는 앱의 main 스레드에서 task를 실시하는 전역적으로 사용 가능한 **serial queue**
* concurrent: 동시에 여러 작업을 실행
  * Global dispatch queue 는 동시에 여러 task를 실행



## Serial - sync, Serial -async, concurrent-sync , concurrent-async

* 우리가 흔히 사용하는 Dispatchqueue.main.async는 serial 한 queue에서 실행하는 async한 작업이다. 따라서 이 queue내에서는 작업이 비동기적으로 진행되고 task가 다 끝나고 나서 다음 작업이 실행된다.



