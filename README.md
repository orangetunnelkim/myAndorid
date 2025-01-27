## 안드로이드 스튜디오를 활용한 카페 키오스크 개발 프로젝트☕
>XML과 자바를 기반으로 제작된 앱입니다.
### 프로젝트 기간: 2주
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
<br><br><br>
        

## **1.앱 실행**
### 앱 실행 영상 보러가기 [🖱️클릭](https://www.youtube.com/shorts/KEcXWBj3QZ8?feature=share) (ctrl키를 누른상태에서 클릭하면 이 페이지는 유지된 채 새 창이 열립니다.)
<br><br><br>

## **2.기능 분석**
10.  **쿠폰버튼을 누르면 스탬프를 적립할건지 묻습니다. 휴대폰번호를 입력받는다.** <br><br><br>![KakaoTalk_20250127_191613528_06](https://github.com/user-attachments/assets/33a70683-fbc5-4d97-8d90-d5da3300c502)

<br><br><br><br><br><br><br><br><br>




11.   **회원 정보에 등록되어있는 쿠폰을 리사이클러뷰로 보여줍니다.** <br><br><br>![KakaoTalk_20250127_191613528_05](https://github.com/user-attachments/assets/c5e46a94-8e40-4cbe-880e-048052190671)
<br><br><br><br><br><br><br><br><br>
13.   **해당 쿠폰을 누르면 그 쿠폰을 몇개나 사용할건지 묻는 alert 다이얼로그가 열립니다.** <br><br><br> ![KakaoTalk_20250127_191613528_04](https://github.com/user-attachments/assets/1a8fe170-5b3c-42a3-883f-6ca80ed98a0b)
<br><br><br><br><br><br><br><br><br>
14.   **갯수를 입력 후 확인을 누르면 쿠폰 사용금액에 더해집니다. (결제금액 이하로는 가진쿠폰 내에서 금액이 얼마든지 사용가능합니다.)** <br><br><br>![KakaoTalk_20250127_191613528_03](https://github.com/user-attachments/assets/55f76234-73e9-4bc0-b03b-25f275eebe25)
<br><br><br>
15.   **사용하고 싶은 쿠폰을 모두 입력했다면 확인버튼을 누릅니다.** <br><br><br>
16.   **쿠폰 사용금액도 결제금액에서 차감되는걸 확인할 수 있습니다.** <br><br><br>![KakaoTalk_20250127_191613528_02](https://github.com/user-attachments/assets/56b8f921-d6ff-48a2-9a4c-12f118b75aa0)
<br><br><br><br><br><br><br><br><br>
17.   **마지막으로 결제 수단을 거치면 결제완료 창에서 사용한 쿠폰과 남은 스탬프를 보여줍니다.**
<br><br><br>![KakaoTalk_20250127_191613528_01](https://github.com/user-attachments/assets/57ff4555-7e14-431a-941b-7a4993e4f458)
<br><br><br>![KakaoTalk_20250127_191613528](https://github.com/user-attachments/assets/82a43e65-7d28-4ac6-8f20-5da723249ae9)
<br><br><br><br><br><br><br><br><br>

## **3.쿠폰, 스탬프 관리 설계**
### 쿠폰 
**쿠폰**은 <br>
1,000원 ~ 5,000원, 천원 단위로 회원별로 차등 제공되어있도록 회원정보를 만들었습니다. <br>
회원가입시 1,000원에 해당하는 웰컴 기프트 쿠폰을 제공합니다. <br><br>

**스탬프**는 <br>
음료 1개당 1개의 스탬프가 적립되고 10개를 모을때마다 1,000원 쿠폰이 한개씩 생성됩니다.<br>
10개가 되는 시점에 스탬프는 다시 0개로 갱신됩니다.<br>
스탬프는 음료의 갯수이므로 다이얼로그 객체 생성시 음료의 갯수를 인자로 받습니다. <br>
<br><br>
**※쿠폰, 스탬프** 모두 사용자가 결제를 해야만 회원 정보의 데이터를 바꾸는 것이기 때문에<br>
쿠폰 사용에 대한 다이얼로그가 모두 닫힌 상태에서 사용자가 다른 작업을 하더라도
<br>쿠폰,스탬프에 대한 객체를 유지하는것이 
이 프로젝트의 핵심이었고 가장 어려웠던 부분 중 하나였습니다.

<br><br><br><br>
## **4.코드 분석**
### **4-1.데이터의 관리 방법**
>회원정보
#### 휴대폰번호와 스탬프갯수, 쿠폰들의 갯수를 관리하는 정보
```java
private void initializeUserData() {
        userList.add(new UserData("01050188065", 3, 2, 1, 3, 0, 1, 1));
        userList.add(new UserData("0", 3, 2, 1, 3, 0, 1, 1));
        userList.add(new UserData("01012345678", 5, 3, 0, 1, 2, 1, 0));
        userList.add(new UserData("01026328065", 6, 3, 1, 0, 0, 2, 1));
    }
```
**userList**는 어레이리스트입니다. 객체 배열은 없기때문에 일일히 하나씩 객체에 값을 할당합니다.
<br><br><br>
```java
public UserData(String phone, int stamp, int coupon_1000, int coupon_2000, int coupon_3000, int coupon_4000, int coupon_5000, int coupon_welcome){
        this.phone=phone;
        this.stamp=stamp;
        this.coupon_1000=coupon_1000;
        this.coupon_2000=coupon_2000;
        this.coupon_3000=coupon_3000;
        this.coupon_4000=coupon_4000;
        this.coupon_5000=coupon_5000;
        this.coupon_welcome=coupon_welcome;
    }
```
userData 클래스의 생성자가 이렇게 정의되어 있습니다. 휴대폰 번호에 해당하는 쿠폰들의 갯수와 스탬프의 갯수가 각각 적용되었습니다. <br><br><br>
```java
 phoneSearch.setOnClickListener(c -> {
            initializeUserData();
            userdata = searchUserByPhone(Sendphone); // 전화번호에 맞는 객체 하나 찾아옴
            if (Sendphone != null) {
                if (userdata != null) {
```
<br>

```java
 private UserData searchUserByPhone(String phoneNumber) { // 휴대폰번호와 맞는 객체 하나 갖고옴
        for (UserData user : userList) {
            if (user.getPhone().equals(phoneNumber)) {

                return user;
            }
        }
        return null;
    }
```

사용자가 휴대폰 번호를 입력한 후 정보 가져오기 버튼을 누를때 무명함수가 호출됩니다. 
<br>이때 회원정보 리스트가 만들어짐과 동시에 리스트중 입력한 휴대폰번호에 해당하는 한줄의 객체만을 리턴하는 함수 searchUserByPhone()이 실행됩니다.
<br><br><br>
>쿠폰정보
#### 1.리사이클러뷰에 동적으로 표현할 쿠폰의 상세정보
#### 2.결제시 쿠폰의 갯수를 업데이트 하고, 사용될 쿠폰의 전체금액을 표현하는것에도 필요함
<br><br>
```java
public Coupon(String name, String description, String Period, String available, int qty, int value) {
        this.name = name;
        this.description = description;
        this.Period=Period ;
        this.available=available;
        this.qty=qty;
        this.value=value;
    }
    public Coupon(int UsedQty, int value) {
        this.UsedQty=UsedQty;
        this.value=value;
    }
```
**Coupon** 클래스는 
<br>목적에 맞게 오버로딩된 생성자를 사용합니다. 위 소스코드중 위는 리사이클러 뷰 용도
<br> 아래는 업데이트, 쿠폰사용금액 표시 용도입니다.
<br><br><br>
```java
couponList=new ArrayList<>();
        couponList.add(new Coupon("1000원 쿠폰","결제금액 1000원에 대해 쿠폰으로 사용합니다.","2024-12-01~2025-11-30","사용가능",userData.getCoupon_1000(),1000));
        couponList.add(new Coupon("2000원 쿠폰","결제금액 2000원에 대해 쿠폰으로 사용합니다.","2024-12-01~2025-11-30","사용가능",userData.getCoupon_2000(),2000));
        couponList.add(new Coupon("3000원 쿠폰","결제금액 3000원에 대해 쿠폰으로 사용합니다.","2024-12-01~2025-11-30","사용가능",userData.getCoupon_3000(),3000));
        couponList.add(new Coupon("4000원 쿠폰","결제금액 4000원에 대해 쿠폰으로 사용합니다.","2024-12-01~2025-11-30","사용가능",userData.getCoupon_4000(),4000));
        couponList.add(new Coupon("5000원 쿠폰","결제금액 5000원에 대해 쿠폰으로 사용합니다.","2024-12-01~2025-11-30","사용가능",userData.getCoupon_5000(),5000));
        couponList.add(new Coupon("웰컴 기프티콘","결제금액 1000원에 대해 쿠폰으로 사용합니다.(회원가입시 발급) ","2024-12-01~2025-11-30","사용가능",userData.getCoupon_welcome(),1000));
```
<br>
useData의 쿠폰 갯수를 couponList라는 리사이클러 뷰 용 리스트의 쿠폰갯수 인자로 전달합니다.
<br>이렇게 되면 입력한 휴대폰과 매칭되는 쿠폰 갯수들이 동적으로 리사이클러뷰에 표시되어 입체적으로 객체 관리가 된것입니다.
<br><br><br>

used.add(new Coupon (useCoupon,coupon.getValue()));


<br>

**used리스트는** <br>
사용자가 사용할 쿠폰의 갯수를 누르고 확인 입력시 생성되는 리스트로<br>
사용될 쿠폰의 전체금액을 표시하고, 결제시 회원정보를 업데이트 하기위해 뒷단으로 전달 해야합니다.
<br><br><br>

### 4-2.흐름 관리
>**콜백리스너**

처음엔 사용자에게 보여지는 화면에따라 클래스를 나누고 
<br>다음 다이얼로그로 이동할때 객체를 생성하면서 현재의 다이얼로그를 종료하는 방법으로 흐름을 관리했습니다.
<br>하지만, 코드가 많아지면서 어떤 인자값이 필요한지, 상황에따른 다음객체를 생성할지 여부를 가독성있게 판단해야할 필요를 느꼈습니다.
<br>그래서 **couponController** 클래스로 다이얼로그의 생애주기와 인자들의 이동을 관리했습니다.
<br>
```java
public void showDialog() {
        dialog1 = new Dialog1(context, stamp, totalCount);
        dialog1.setDialogListener(state -> { //seton 메써드호출 / onDialogResult 매써드정의
            if (state.equals("member")) {
                dialog2 = new Dialog2(context, dialog1.getUserdata(), stamp, totalCount);
                dialog2.setDialogListener(state2 -> {
                    useCoupon = dialog2.getTotalCoupon();
                    if (useCoupon != 0) ((CheckOrderActivity) context).setCoupon(useCoupon);
                    if (state2.equals("useCoupon")) {//적립하고, 쿠폰 사용하고
                        savecoupon = new saveCoupon(dialog2.getUsed(), stamp, dialog1.getUserdata());
                    } else savecoupon = new saveCoupon(null, stamp, dialog1.getUserdata());

                });
                dialog2.show();
            }
        });
        dialog1.show();
        Log.v("stamp","stamp: "+stamp);
    }
```
쿠폰 컨트롤러 클래스입니다.
<br>
<br> 이부분에서의 핵심은
<br> dialog1.setDialogListener, dialog2.setDialogListener 처럼 각 다이얼로그에 인터페이스로 정의된 **콜백리스너**를 사용하는 것입니다.
<br> 다이얼로그가 열리고 그 다이얼로그가 dismiss 되기 전까지 자바런처가 기다리는게 아니고
<br> 아래로 계속해서 코드를 읽으며 수행합니다.
<br><br><br>
```java
 public interface DialogListener{
        void onDialogResult(String state);
    }

    public void setDialogListener(DialogListener listener) {
        this.listener = listener;
    }
```
```java
 phoneSearch.setOnClickListener(c -> {
            initializeUserData();
            userdata = searchUserByPhone(Sendphone); // 전화번호에 맞는 객체 하나 찾아옴
            if (Sendphone != null) {
                if (userdata != null) {
                    if (listener != null) {
                        listener.onDialogResult("member"); //메써드호출
                        dismiss();
                    }
```
Dialog1 클래스입니다.
<br>
<br>
Dialog1에서 이벤트가 발생했고 컨트롤러에서 dialog1.setDialogListener를 호출했다면 listener는 null이 아닌 객체가 되어
<br>컨트롤러에 정의된 onDialogResult에 member라는 인자값을 주면서 비동기식으로 컨트롤러의 구문을 실행하는것입니다.
<br>위에서 설명드렸던 바와 같이 컨트롤러의 흐름은 멈춘것이아니라 런처가 아래로 계속 실행은 되고있지만,
<br>if 조건문에 의해 마치 멈춰있는 것처럼만 보이는 것입니다.

<br><br><br>
>**싱글톤 패턴**
<br>


쿠폰컨트롤러의 객체가 단일객체만을 생성하도록 처리하지 않을 경우 데이터의 끊김이 발생합니다.
<br>
![KakaoTalk_20250127_191613528_02](https://github.com/user-attachments/assets/4b1f013f-8aa6-40d6-82f2-9bf7494e7e26)
<br>
**①** 에서 사용자로부터 사용할 쿠폰을 입력받으면 
<br> saveCopon이라는 회원정보를 업데이트하는 클래스에 객체를 올려두고 대기합니다.
<br> **②** 실행시 saveCopon클래스 내에 함수를 실행시켜 회원정보의 데이터를 덮어씁니다.
<br>하지만 coponContoroller 처음에 올려둔 객체를 매인액티비티에서 전역변수로 선언하여 **②** 클릭시
<br> **①** 에서 올려둔 객체가 null값이 되는 문제를 해결하기 어려웠습니다.
<br> Garbage Collector가 더이상 사용하지않는 메모리로 간주하고 삭제할 가능성이 있습니다.
<br>
```java
public static CouponController getInstance() {
        if (instance == null) {
            instance = new CouponController();
        }
        return instance;
    }
```

쿠폰컨트롤러 클래스입니다.
<br><br><br>

```java
 public void onClickCouponRedeem(View view) {
        couponController=couponController.getInstance();
        couponController = new CouponController(this,CoffeeData.getTotalCount(),CoffeeData.getTotalPrice());
        couponController.showDialog() ;    //

    } //쿠폰 추가
```

CheckOrderActivity 클래스 입니다.

<br> 이렇게 싱글톤 처리를 해주면 처음에 생성한 인스턴스를 잃어버리지 않고 **②** 에서 사용이 가능합니다.
    
