<template>
  <div id="app">
    <div id="app-content">
      <div id="title">
        <span>사회적 </span>
        <span style="color: var(--color-point);">거리두기</span>
      </div>
      <div class="meeting-container">
        <div class="article horizontal">
          <div class="point box">사적모임</div>
          <b-card>
            <b-card-text>전국 8인 (백신접종자·미접종자 구별 없이, 수도권·비수도권)</b-card-text>
          </b-card>
        </div>
        <div class="article horizontal">
          <div class="point box">행사·집회</div>
          <b-card>
            <b-card-text>접종 여부 관계없이 299명까지 가능<br>300명 이상 행사(비정규공연장·스포츠대회·축제)는 관계부처 승인 하에 관리</b-card-text>
          </b-card>
        </div>
      </div>
      <b-card class="left">
        <b-card-text>
          사회적 거리두기, 사적인원 소폭 조정(3.21~4.3)
        </b-card-text>
        <a class="point box" target="_blank" href="http://ncov.mohw.go.kr/tcmBoardView.do?brdId=3&brdGubun=31&dataGubun=&ncvContSeq=6496&contSeq=6496&board_id=311&gubun=ALL">보러가기</a>
      </b-card>
      <rule-list></rule-list>
      <b-card class="left">
        <b-card-text>
          위 자료는 코로나바이러스감염증-19(COVID-19)에서 제공하는 보도자료를 기반으로 제작되었습니다. 
        </b-card-text>
        <button class="point box" href="#" @click="showFeedbackArea">오류제보</button>
      </b-card>
      <feedback 
        v-if="feedbackArea == true"
        @_closeFeedbackArea = "closeFeedbackArea"
      ></feedback>
    </div>
  </div>
</template>

<script>
import ruleList from "./components/rule-list.vue"
import feedback from "./components/feedback.vue"

export default {
  name: 'App',
  components: {
    ruleList, feedback
  },
  data() {
    return {
      fields: [
        {key: '시설'}, 
        {key: '운영시간', formatter: 'openingHour'}, 
        {key: '이용가능대상'}],
      feedbackArea: false
    }
  },
  methods: {
    showFeedbackArea() {
      console.log("showFeedbackArea");
      if (this.feedbackArea === false) {
        this.feedbackArea = true
      }
      else {
        this.feedbackArea = false
      }
    },
    closeFeedbackArea() {
      this.feedbackArea = false
    }
  }
}
</script>

<style>
@font-face {
    font-family: "GmarketSans";
    src: url('../resources/fonts/GmarketSansTTFLight.ttf') format('truetype');
    font-weight: 100;
}

@font-face {
    font-family: "GmarketSans";
    src: url('../resources/fonts/GmarketSansTTFMedium.ttf') format('truetype');
    font-weight: 400;
}

@font-face {
    font-family: "GmarketSans";
    src: url('../resources/fonts/GmarketSansTTFBold.ttf') format('truetype');
    font-weight: 700;
}

:root {
  /* color */
  --color-point: #1CA7EC;
  --color-sky-blue: #EAF5FA;
  --color-gray: #E5E5E5;
  --color-light-gray: #F4F4F4;

  /* font-size */
  --font-small: 14px;
  --font-medium: 18px;
  --font-title-1: 36px;
}

.content {
  height: 300px;
  overflow-y: scroll;
}

#app {
  padding: 40px;
  margin-bottom: 30px;
  font-family: GmarketSans, Avenir, Helvetica, Arial, sans-serif;
  font-size: var(--font-small);
  font-weight: 400;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  vertical-align: middle;
  color: #2c3e50;
  box-sizing: border-box;
}

#title {
  font-size: var(--font-title-1);
  font-weight: 700;
}

#app-content {
  width: 630px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: auto;
  gap: 40px;
}

.horizontal.container {
  display: flex;
  flex-direction: row;
  gap: 10px;
}

.container.center {
  justify-content: center;
  align-content: center;
}

.point.box {
  width: 100px;
  padding: 6px 12px;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  background-color: var(--color-point);
  color: white;
  text-align: center;
  line-height: 1.5;
  cursor: pointer;
  border: 1px solid transparent;
  border-radius: 0.25rem;
  box-shadow: 2px 2px 10px var(--color-gray);
  text-decoration: none;
}

.card {
  width: 100%;
  text-align: left;
  box-shadow: 2px 2px 5px var(--color-gray);
}

.card.left {
  text-align: left;
}

.small.card {
  width: 300px;
}

.card-header {
  font: bold;
}

.card-body {
  vertical-align: center;
}

.article.horizontal {
  width: 100%;
  display: flex;
  flex-direction: row;
  gap: 10px;
}

.meeting-container {
  width: 100%;
  display: flex; 
  flex-direction: column; 
  gap: 20px;
  justify-content: center;
}

#feedbackArea {
  margin-top: 20px;
}

</style>
