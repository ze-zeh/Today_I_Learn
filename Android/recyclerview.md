# RecyclerView

- RecycleView 기본 구조

<img width="691" alt="스크린샷 2021-07-29 오후 2 16 30" src="https://user-images.githubusercontent.com/58066704/127435747-c6bbc2a9-5cd0-446e-bf1e-601566064dae.png">

<br>
<br>

- RecyclerView 구성 요소

    - RecyclerView   
        : 사용자 데이터를 리스트 형태로 화면에 표시하는 컨테이너 역할

        <br>

    - Adapter   
        : 데이터 리스트로부터 리사이클러뷰에 표시될 아이템 뷰를 생성하는 역할
        
        <br>

    - LayoutManager   
        : 리사이클러뷰가 아이템을 화면에 표시할 때, 아이템 뷰들이 리사이클러뷰 내부에서 배치되는 형태를 관리

        - 리니어(LinearLayoutManager)   
        : 수평(Horizontal) 또는 수직(Vertical) 방향, 일렬(Linear)로 아이템 뷰 배치.   

        - 그리드(GridLayoutManager)   
        : 바둑판 모양의 격자(Grid) 형태로 아이템 뷰 배치.   

        - 스태거드그리드(StaggeredGridLayoutManager)   
        : 엇갈림(Staggered) 격자(Grid) 형태로 아이템 뷰 배치.

        <br>

    - ViewHolder   
        : 화면에 표시될 아이템 뷰를 저장하는 객체


<br>

- RecyclerView 사용법

    - 워크플로우
        <img width="690" alt="스크린샷 2021-07-29 오후 2 33 09" src="https://user-images.githubusercontent.com/58066704/127437105-069d6a9b-8929-484c-9e3a-d2f4ba5d35d2.png">

    <br>

    - Activity 또는 Fragment에 RecyclerView 추가

        ```xml
        <androidx.recyclerview.widget.RecyclerView
            android:id="@+id/recyclerView"
            android:layout_width="match_parent"
            android:layout_height="match_parent"/>

    <br>

    - 리사이클러뷰 아이템 뷰 레이아웃 추가

        ```xml
        <?xml version="1.0" encoding="utf-8"?>
        <LinearLayout
            xmlns:android="http://schemas.android.com/apk/res/android"
            android:layout_width="match_parent"
            android:layout_height="100dp">

            <ImageView
                android:layout_width="30dp"
                android:layout_height="30dp"/>
            
        </LinearLayout>
    <br>

    - 리사이클러뷰 어댑터 구현
        ```kt
        // 생성자에서 데이터 리스트 객체를 전달받음
        class MyAdapter (val items : ArrayList<String>) : RecyclerView.Adapter<MyAdapter.Viewholder>() {

            // onCreateViewHolder() - 아이템 뷰를 위한 뷰홀더 객체 생성하여 리턴
            override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): MyAdapter.Viewholder {
                val v = LayoutInflater.from(parent.context).inflate(R.layout.rv_item, parent, false)
                return Viewholder(v)
            }

            // onBindViewHolder() - position에 해당하는 데이터를 뷰홀더의 아이템뷰에 표시
            override fun onBindViewHolder(holder: MyAdapter.Viewholder, position: Int) {
                holder.bindItems(items[position])
            }

            // getItemCount() - 전체 데이터 갯수 리턴
            override fun getItemCount(): Int {
                return items.size
            }

            // 아이템 뷰를 저장하는 뷰홀더 클래스
            inner class Viewholder(itemView: View) : RecyclerView.ViewHolder(itemView) {

                fun bindItems(item : String) {

                }
            }
        }

    <br>

    - 리사이클러뷰에 어댑터와 레이아웃매니저 지정하기

        ```kt
        val rv : RecyclerView = findViewById(R.id.myRecyclerView)

            val items = ArrayList<String>()

            items.add("a")
            items.add("b")
            items.add("c")

            val rvAdapter = MyAdapter(items)

            rv.adapter = rvAdapter
            rv.layoutManager = GridLayoutManager(this, 2)