## 안드로이드 스튜디오를 활용한 카페 키오스크 개발 프로젝트☕
>XML과 자바를 기반으로 제작된 앱입니다.
### 팀원 [백건우](https://github.com/gunwoo100/ProJect2)🙍‍♂️, [엄정현](https://github.com/Natanal-H/my-kiosk-android)🙍‍♂️, 이새로미🙍‍♀️, 김지욱🙍‍♂️ 
(이름 클릭시 해당 팀원이 담당했던 섹션의 소스 자료를 참고할 수 있습니다.)
#### 이 자료는 스탬프를 적립하고, 쿠폰을 사용하는 부분에 대한 내용입니다.



* **목차**
  * 1.앱 실행
  * 2.실행 영상에대한 기능 분석
  * 3.쿠폰, 스탬프 관리 설계
  * 4.코드 분석
    * 4-1. 데이터 관리 방법
      * 회원정보와 쿠폰정보
    * 4-2. 흐름 제어 관리
      * 쿠폰 컨트롤러
      * 커스텀 다이얼로그
      * 데이터 수정 클래스
  * 5.결론
      * 어려웠던점
      * 느낀점     
        

## **1.앱 실행**
### 앱 실행 영상 보러가기 [🖱️클릭](https://www.youtube.com/shorts/KEcXWBj3QZ8?feature=share) (ctrl키를 누른상태에서 클릭하면 이 페이지는 유지된 채 새 창이 열립니다.)

## **2.기능 분석**
1. 주문, 포장 중 선택한다.
2. 주문할 음료와 hot/ ice 중 하나를 선택한다.
3. 장바구니에 담는다.(리사이클러 뷰)
4.  담긴 리스트들을 전체 삭제하여 장바구니를 비운다.
5.  +,-를 통해 담긴 음료의 수량과 금액을 변경한다.
6.  결제를 누르면 어레이리스트에 담겨 결제 화면으로 이동한다. (결제에 필요한 모든 데이터들이 집결하는 곳이다.)
7.  포인트적립 버튼을 누르면 포인트를 적립할 회원의 전화번호를 입력 받는다.
8.  잔여 포인트를 보여준 후 포인트를 얼마나 사용할지 묻는다.
9.  사용할 포인트를 입력하고 확인을 누르면 포인트 사용금액이 결제금액에서 차감되는게 확인 가능하다.
10.  **쿠폰버튼을 누르면 스탬프를 적립할건지 묻는다. 휴대폰번호를 입력받는다.**
11.   **회원 정보에 등록되어있는 쿠폰을 리사이클러뷰로 보여준다.**
12.   **해당 쿠폰을 누르면 그 쿠폰을 몇개나 사용할건지 묻는 alert 다이얼로그가 열린다.**
13.   **갯수를 입력 후 확인을 누르면 쿠폰 사용금액에 더해진다. (결제금액 이하로는 가진쿠폰 내에서 금액이 얼마든지 사용가능하다.)**
14.   **사용하고 싶은 쿠폰을 모두 입력했다면 확인버튼을 누른다.**
15.   **쿠폰 사용금액도 결제금액에서 차감되는걸 확인할 수 있다.**
16.   **마지막으로 결제 수단을 거치면 결제완료 창에서 사용한 쿠폰과 남은 스탬프를 보여준다.**
