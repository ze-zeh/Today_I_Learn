# ViewHolder

출처 링크 : https://blog.yena.io/studynote/2017/12/05/Android-Kotlin-ViewHolder.html

<br>

## ViewHolder의 필요성

ListView에서 발견된 문제점은, 스크롤을 움직이는 등 View가 보이거나 사라지면 그 때마다 findViewById를 통해 convertView에 들어갈 요소를 찾는다는 점. 스크롤 할 때마다 View를 찾으면 리소스를 많이 사용하게 되고, 속도가 느려짐. ViewHolder를 이용하면 이 View의 재활용(recycle)이 가능.

<br>

## ViewHolder 활용

ListView의 각 View와 실제 데이터를 매칭하는 것이 Adapter의 역할. 따라서 ViewHolder를 사용하려면 Adapter 내에 설정해야함.

<img width="734" alt="스크린샷 2021-08-10 오후 11 55 40" src="https://user-images.githubusercontent.com/58066704/128889939-fef5455b-4409-46f5-b2fe-68641f274d3a.png">

이 ViewHolder는 getView 메소드를 override 할 때 사용함. getView 설정을 할 때, ViewHolder 안에 데이터가 아무것도 없으면 findVidwById 하여 ListView의 View를 생성하고, ViewHolder 안에 데이터가 있을 경우 이를 재활용 하도록 설정.

ViewHolder까지 설정한 MainListAdapter의 최종 모습은 아래와 같음.

<img width="731" alt="스크린샷 2021-08-10 오후 11 57 28" src="https://user-images.githubusercontent.com/58066704/128890245-05d5b179-afaa-4d30-9e39-f99b9f861af4.png">
<img width="729" alt="스크린샷 2021-08-10 오후 11 57 39" src="https://user-images.githubusercontent.com/58066704/128890254-00b06c76-abf4-4327-8447-25adf8ad4a88.png">