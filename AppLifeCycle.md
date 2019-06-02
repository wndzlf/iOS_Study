## App LifeCycle

* 앱 실행시 

  * UIApplication 객체 생성
    * UIApplication 객체는 싱글톤
    * EventLoop에서 발생하는 여러 이벤트를 감지하고 Delegate에 전달
    * 메모리 부족경고를 Delegate에 전달
  * @UIApplicationMain 어노테이션이 있는 클래스를 찾아 AppDelegate 객체를 생성
    * AppDelegate 객체는 UIApplication 객체로부터 메시지를 받았을 때 해당 상황에서 실행될 함수를 정의
  * Main Event Loop를 실행 (touch, text input등 유저의 액션을 받는 루프) 및 기타 설정

  

### 앱의 실행 상태 5가지

1. Not Running: 앱이 실행되지 않은 상태

   (**Inactive**와 **Active** 상태 == **Foreground**)

2. Inactive: 앱이 실행중인 상태 그러나 아무런 **이벤트** 를 받지 않은 상태

3. Active: 앱이 실행중이며 **이벤트가 발생**한 상태

4. Background: 앱이 백그라운드에 있는 상태 그러나 **실행되는 코드가 있는** 상태

5. Suspend: 앱이 백그라운드에 있고 실행되는 **코드가 없는** 상태



### AppDelegate 함수

*  application(_:didFinishLaunching:) - 앱이 처음 시작될때 실행

* applicationWillResignActive: - 앱이 active에서 inactive로 이동될 때 실행

* applicationDidEnterBackground: - 앱이 background 상태일 때 실행

* applicationWillEnterForeground: - 앱이 background에서 foreground로 이동 될때 실행 

* applicationDidBecomeActive: - 앱이 active 상태가 되어 실행 중일 때

* applicationWillTerminate: - 앱이 종료될 때 실행

