# Firebase Realtime Database

## 문서
https://firebase.google.com/docs/database/android/start?hl=ko

<br>

## 1. Firebase Console로 이동
Realtime Database탭 선택

잠금모드 / 테스트모드 중 선택

잠금모드에서는 규칙 탭에서 read/write 권한 수정 가능

[파이어 베이스 기본 보안 규칙](https://firebase.google.com/docs/rules/basics?hl=ko)


<br>

## Realtime Databse에 추가

```kt
val database = Firebase.database
val ref = database.getReference("child_name")
ref.push().setValue(Data("title", "name"))
```
