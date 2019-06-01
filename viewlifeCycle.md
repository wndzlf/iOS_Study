## viewWillAppear

* 뷰가 보여질때마다 콜된다.
* 뷰는 bounds를 가지지만 orientation은 아직 가지지 않는다.



## viewWillLayoutSubviews

* 처음엔 아무것도 하지 않습니다.
* 뷰의 bounds가 변화되면 뷰는 그의 서브뷰들의 position을 세팅합니다.
* 이 함수를 오버라이드 해서 뷰가 서브뷰들을 레이아웃 하기전에 콜한다.



## viewDidLayoutSubviews

* 그의 서브뷰들의 바운즈가 적용된 이후에 호출
* 서브뷰들의 변화가 된 이후 먼가 코드를 작성하고 싶다면 이 코드를 작성해라



## viewDidAppear

* 보통 애니메이션 시작 하거나 비디오나 사운드를 시작.
* 혹은 네트워크



## viewWillDisappear

* 뷰가 뷰 하이아라키에서 사라지고 호출된다.
* 뷰는 hierarchy에 는 존재하지만 아직 사라지지 않았다.
* 타이머 핸들, 키보드 숨키기, 네트워크 요청 캔슬 등등



## viewDidDisappear

* 뷰컨트롤러의 뷰가 사라지고 호출된다.
* 노티피케이션을 스탑할때 사용



## didReceiveMemoryWarning()

* 메모리가 다 찰때 
* 몇몇 오브젝트를 삭제해야 한다.



## viewWillTransition(to:with:)

* 인터페이스 orientation이 변화할때 , UIKit이 이 메소드를 부른다. 

