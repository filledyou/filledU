<template>
  <div class="box">
      <!-- 타이틀 부분-->
      <div class="title_section">
        <img src="@/assets/school.png" alt="school_icon"> 
        <p class="title">대학 리스트</p>
      </div>

      <hr class="divider">

      <!-- 검색창 부분 -->
      <div class="input_section">
        <input class="searchInput" type="text">
        <button class="searchButton">검색</button>
      </div>

      <!-- 필터부분 -->
      <div class="filter_section" @click="ActiveFilter">

        <div class="filter-dropdown">
          <img src="@/assets/dropdown.png" alt="#">
          <p>필터: <a> {{Filtering}} </a></p> 
        </div>
          
      <!-- end of filter-dropdown -->
     </div>
     <div class="filter-advanced">
          <select class="select_school">
            <option>학교</option>
            <option>B</option>
            <option>C</option>
        </select>
        AND
        <select class="select_date">
            <option>학교</option>
            <option>B</option>
            <option>C</option>
        </select>
      </div>
      <!-- end of filter section   -->
      <div class="list_label">
          <p class="name">이름</p>
          <p class="campus">캠퍼스</p>
          <p class="etcData">생성일자 / 생성자</p>
        </div>

      <div class="list_box">
        <!-- UNIVERSITY ITEMS ON HERE  -->
        <!-- ##########################-->

        
      </div>
      
      <button class="AddSchool">학교추가</button>
    </div>
</template>

<script>
import $ from 'jquery'
export default {
    data(){
        return{
            Filtering: 'OFF'
        }
    },
    methods:{
        ActiveFilter(){
      //V-if로 할 수 있었으나 슬라이드 애니메이션 때문에 css / jquery 사용
      if(this.Filtering == "OFF"){
        $('.list_box').css('height','480');
        $(".filter-dropdown").css("background-color","##fff8f7");
        $("p > a").css("color","violet");
        $(".filter-dropdown > img").css('transform','rotate(180deg)');
        $('.filter-advanced').stop().slideDown()
        this.Filtering = "ON"
      }
      else{
        $('.list_box').css('height','520px');  
        $(".filter-dropdown").css("background-color","#e7e6e6");
        $("p > a").css("color","red");
        $(".filter-dropdown > img").css('transform','rotate(360deg)');
        $('.filter-advanced').stop().slideUp()
        this.Filtering = "OFF"
            }
          
        }
    }
}
</script>

<style>
    /* Container */
.box{
  margin: 0 auto;

  /* position */
  margin-top: 20px;
  

  width: 90%;
  height: 835px;

  border-radius: 15px;
  background-color: rgb(242, 242, 242);
  border: 1px solid rgb(204, 204, 204);

  /* for drop down */
  overflow: hidden;
}

.box > .title_section > img{
  justify-items: left;

  /* position */
  margin-left: 45px;
  margin-top: 10px;

  /* size */
  width: 60px;
  height: 60px;
}

.box > .title_section{
  /* 방향: 가로 */
  display: flex;
}


.title_section > .title{
  font-size: 25px;
  font-family: 'Do Hyeon', sans-serif;

  /* position */
  margin-left: 20px;
  margin-top: 30px;
}

/* 수평선 */
hr{
  /* position */
  margin-top: -15px;

  width: 98%;
  border-top: 0.1px solid rgb(187, 187, 187);
}

.input_section{
  display: flex;

  /* position */
  margin-top: 20px;
}

.input_section > .searchInput{
  width: 90%;
  height: 50px;

  font-size: 20px;

  /* position */
  margin-left: 25px;
  
  background-color: rgb(208, 206, 206);
  border-radius: 10px;
  border: none;
}

.input_section > .searchButton{
  width: 8.5%;
  height: 50px;

  /* position */
  margin-left: 10px;
  margin-right: 15px;

  background-color: rgb(169, 209, 142);
  border-radius: 5px;
  border: none;

  cursor: pointer;
  color: white;

  transition: 0.1s;
}

.searchButton:hover{
  background-color: rgb(116, 167, 69);
  transform: scale(1.05);
}

/* 필터 영역 */
.filter_section{
  width: 100%;
  

  /* position */
  margin-top: 10px;

  background-color: rgb(228, 228, 228);
  cursor: pointer;
}

.filter-dropdown:hover{
  background-color: rgb(233, 232, 232);
}

/* 필터 박스부분 기로로 (block 요소이여서) */
.filter-dropdown{
  display: flex;
  height: 35px;
  

  /* 색깔 트렌지션 */
  transition: 0.3s;
}

.filter_section> .filter-dropdown > img{
  width: 30px;
  height: 30px;

  /* position */
  margin-left: 46%;
  margin-top: 5px;
}

.filter_section .filter-dropdown > p{
  width: 100px;
  height: 30px;

  /* position */
  margin-top: 10px;
  margin-left: 5px;
  
}

/* 필터 expand 하는 부분 */
.filter-advanced{
  display: none;

  width: 100%;
  height: 30px;

  background-color: rgb(236, 236, 236);
}
/* ON OFF 색상 */
p > a{
  color: black;
}


/* 리스트 보기 위한 라벨 */
.list_label{
  display: flex;

  color: rgb(168, 168, 168);
}

.list_label > .name{
  margin-left: 8.5%;
}

.list_label > .campus{
  margin-left: 8.5%;
}

.list_label > .etcData{
  margin-left: 45%;
}

.list_box{
  /* initilalize the postion to center */
  margin: 0 auto;

  /* position */
  margin-top: -5px;

  width: 95%;
  height: 520px;

  /* property */
  background-color: rgb(238, 238, 238);

  transition: 1.25s;
}

.AddSchool{

  position: fixed;
  /* position */
  /* float: right; */
  margin-left: 79.5%;
  margin-top: 10px;
  margin-right: 15px;

  /* size */
  width: 150px;
  height: 50px;

  /* property */
  background-color: rgb(169, 209, 142);
  border-radius: 5px;
  border: 0.1px solid rgb(126, 126, 126);

  cursor: pointer;
  color: white;
  }

.AddSchool:hover{
  background-color: rgb(57, 145, 76);
}
</style>