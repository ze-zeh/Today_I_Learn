# Glide

안드로이드에서 이미지를 빠르고 효율적으로 불러올 수 있게 도와주는 라이브러리이다. 사용 방법도 간단하고 확장성도 넓어서 이미 메이저하게 사용되고 있는 라이브러리이다. 이미지, Gif, 비디오 스틸의 로딩과 디코딩, 캐싱 등의 다양한 API를 사용할 수 있다. 기본적으로는 커스텀하게 만들어진 HttpUrlConnection 기반이지만, Volley나 OkHttp 라이브러리를 사용할 수 있는 플러그인도 지원한다.

Glide는 어떠한 종류의 이미지이더라도 빠르고 부드럽게 스크롤 하는 것을 목적으로 한다. 공식 페이지의 설명을 보면 이 부분을 참 많이 강조하는 것 같다. 실제로도 Glide를 사용하면서도 그러한 인상을 받고 있다.

<br>

- app Gradle 파일의 dependencies에 다음을 추가
    ```gradle
    implementation 'com.github.bumptech.glide:glide:4.11.0'
    annotationProcessor 'com.github.bumptech.glide:compiler:4.11.0'

- 외부 통신을 통해 이미지를 가져와야 한다면 인터넷 권한을 매니페스트 파일에 추가

    ```xml
    <uses-permission android:name="android.permission.INTERNET" />
    
- 뷰에 이미지 로드
    ```kt
    /* Activity에서 사용할 경우 */

    Glide.with(this)
        .load(imageUrl)
        .into(imageView)
    ```
   
   
    ```kt
    /* ViewHolder에서 사용할 경우 */
    Glide.with(itemView)
        .load(imageUrl)
        .into(itemView.imageView)
    ```

