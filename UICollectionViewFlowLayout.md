## UICollectionViewFlowLayout

* 실제하는 레이아웃 오브젝트 
* 그리드 혁앹의 아이템을 organizes한다. 
* optional한 헤더와 푸터 뷰들과 각각의 섹션들로



## 플로우 레이아웃 구성단계 

1. **플로우 레이아웃** 객체를 작성해 컬렉션뷰의 레이아웃 객체로 지정합니다.
2. 셀의 너비와 높이를 구성합니다.
3. 필요한 경우 셀의 간격을 조절합니다.
4. 원할 경우 섹션 헤더 혹은 섹션 푸터 크기를 지정합니다. 
5. 레이아웃 스크롤 방향을 설정합니다.



* 플로우 레이아웃의 프로퍼티는 기본값을 가지지만. **셀의 너비와 높이** 의값은 모두 0값으로 되어 있기에 꼭꼭 지정해야 합니다.
* 셀간의 최소간격을 항상 설정했던 이유? 
  * 셀간의 크기가 다르면 최소간격이 중요한 지표가 되기 때문에!!!



## 콘텐츠 여백 수정하기

`let inset = UIEdgeInsetsMake(top, left, bottom , right)`

헤더와 푸터 오른쪽 왼쪽에 여백을 줄 수 있습니다.



## 셀 예상(Estimated) 크기 지정

* ios 8 버전 이후 부터 셀 스스로 크기를 결정한 후 이를 UICollectionViewLayout 객체에 알려주는 방식으로 셀의 크기를 정할 수 있습니다. 이방법을 사용하려면 estimatedItemSize 프로퍼티를 사용해 대략적인 셀의 최소 크기를 미리 알려줍니다.



`let flowLayout: UICollectionViewFlowLayout = UICollectionViewFlowLayout()`

`flowLayout.estimatedItemSize = CGSize(width: 50.0, height: 50.0)`

`collectionView.collectionViewLayout = flowLayout`





## UICollectionViewDelegateFlowLayout 

UICollectionViewDelegateFlowLayout 프로토콜은 UICollectionViewFlowLayout 객체와 상호작용 하여 레이아웃을 조정할 수 있는 메서드가 정의 되어 있습니다. 이 프로콜의 메서드는 셀의 크기와 셀 간의 사이 간격을 정의합니다. 전부 선택 사항인 메서드 입니다. 



### 주요 메서드

* collectionView(_:layout: sizeForItemAt:) -> CGSize: 지정된 셀의 크기를 반환하는 메서드
* collectionView(_:layout:insetForSectionAt:) -> UIEdgeInstes: 지정된 섹션의 여백을 반환하는 메서드.
* collecionView(_:layout:minimumLineSpacingForSectionAt:)-> CGFloat: 지정된 섹션의 행 사이 간격 최소 간격을 반환하는 메서드 . scrollDirection이 horizontal이면 수직이 행이되고 vertical이면 수평이 행이된다.
* collectionView(_:layout: minimuminteritemSpacingForSectionAt:) -> CGFloat: 지정된 셀 사잉의 최소 간격을 반환하는 메서드.
* collectionView(_:layout:referenceSizeForHeaderInSection:)->CGSize: 지정된 섹션의 헤더뷰의 크기를 반환하는 메서드. 크기를 지정하지 않으면 화면에 보이지 않습니다.
* collectionView(_:layout:referenceSizeForFooterInSection:) -> CGSize: 지정된 섹션의 푸터뷰의 크기를 반환하는 메서드. 크기를 지정하지 않으면 화면에 보이지 않습니다.