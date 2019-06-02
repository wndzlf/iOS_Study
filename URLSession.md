# URLSession

* 네트워크 데이터 전송 task 들과 관련된 객체



## Declaration

`class URLSession : NSObject`



## Overview

* URL로 나타난 endpoint로 데이터를 다운로드 하거나 업로드 하는데 필요한 API를 제공
* API는 background 다운로드를 가능하게 해준다.
* 다양한 delegate 메소드가 authentication을 지원하고 redirection과 같은 이벤트를 앱에 알립니다.

* URLSession API를 사용하면서 하나 이상의 sessions을 만들 수 있다.(각 세션들은 전송 tasks들과 연관되어있다.)



## Types of URL Sessions

* 주어진 URL 세션 내의 작업은 단일 세션 호스트의 **최대 동시 연결 수**, 셀룰러 네트워크를 통한 **연결 허용 여부** 등과 같은 연결 동작을 정의하는 **공통 세션 구성 객체**를 공유합니다.
* URLSession은 singleton **shared** session을 가진다. 
  * 하지만 이것은 customizable한 세션이 아니다.
* 다른 세션종류 세가지가 존재한다.
  * **default** session : shared session과 비슷하다. 하지만 더많은 configuration을 제종하고, delegate로 점진적인 데이터를 얻을 수 있습니다.
  * **ephemeral** session: 캐시, 쿠키, 인증을 사용하지 않습니다.
  * **background** session: 앱이 실행중이지 않을때 업로드 하거나 다운로드 하는 것을 도와줍니다.



## Types of URL Session Tasks

* 세션을 사용하면서 tasks를 만드는데 옵셔널하게 서버에 업로드 하고 데이터를 받아오는 역할을 한다.
* 세가지 종류의 URLSession API tasks를 제공한다.
  * **Data** tasks : NSData objects를 이용하여 데이터를 보내거나 받는다. Data tasks는 짧고 interactive한 요청에 사용된다.
  * **Upload** tasks: data tasks와 비슷한 역할을 한다. 하지만 (지정된 형식의 파일을 전송 ) 하고 background upload 를 제공한다. ( 앱이 실행중이지 않을때)
  * **Download** tasks: 파일 형식의 데이터를 받는다. 앱이 실행중이지 않을때 백그라운드와 업로드를 제공한다.



## USing a Session Delegate

* 다양한 이벤트가 발생함에 따라 다양한 델리게이트를 제공한다.
  * 인증 실패
  * 데이터 arrive 실패
  * Data 캐시 준비 등등
* session object는 강한 참조를 델리게이트에 가지고 있다. Invalidate the session 하지 않으면 메모리 누수가 발생함을 명시하자



## Asynchronicity and URL Sessions

* 두가지 방법을 사용하여 데이터를 return하게된다.
  * By calling a **completion handler** block
  * By calling methods on the session`s **delegate** 
    * delegate를 이용하여 정보를 전달하면 URLSession API는 status와 progress 정보를 제공한다. 
* canceling, restarting, resuming, and suspending tasks를 제공
* resume suspended, canceled, failed downloads 를 제공



## Protocol Support

* URLSession 클래스는 기본적으로 사용자의 시스템 환경 설정에 구성된 프록시 서버 및 SOCKS 게이트웨이에 대한 투명한 지원을 통해 데이터 파일, FTP, HTTP, HTTPS URL 스키마를 제공합니다.
* URLSession은 HTTP / 1.1 , SPDY 및 HTTP / 2 프로토콜을 지원합니다.
* RFC 7540 에서 HTTP 2 에 대한 기술이 설명되어있습니다.
* URLProtocol을 하위 클래스 화 하여 자신의 맞춤 네트워킹 프로토콜 및 URL 스키마를 추가할 수 있습니다.
  * Scheme : 프로토콜를 지칭합니다. 인터넷 자원에 접근할 수 있는 프로토콜 ( HTTPS, HTTP 등등)
  * URL ( Uniform Resource Locator)
  * URI ( Universal Resource Identifier) 



## Thread Safety

* URL session API는 완전히 thread-safe하다.