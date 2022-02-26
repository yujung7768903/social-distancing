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
            <b-card-text>전국 6인</b-card-text>
          </b-card>
        </div>
        <div class="article horizontal">
          <div class="point box">행사·집회</div>
          <b-card>
            <b-card-text>50명 미만 | 접종자·미접종자 구분없이 가능<br>50명 이상 | 접종완료자 등으로만 구성하여 299명까지 가능</b-card-text>
          </b-card>
        </div>
      </div>
      <b-card class="left">
        <b-card-text>
          사적모임 인원 전국 6인 유지, 영업시간 22시로 완화, 내일부터 즉시 시행(2.19~3.13)
        </b-card-text>
        <a class="point box" target="_blank" href="http://ncov.mohw.go.kr/tcmBoardView.do?brdId=&brdGubun=&dataGubun=&ncvContSeq=370247&contSeq=370247&board_id=&gubun=ALL">보러가기</a>
      </b-card>
      <rule-list></rule-list>
      <b-card class="left">
        <b-card-text>
          위 자료는 코로나바이러스감염증-19(COVID-19)에서 제공하는 보도자료를 기반으로 제작되었습니다. 
        </b-card-text>
        <button class="point box" href="#" @click="showFeedbackArea">오류제보</button>
        <b-form-textarea
          id="feedbackArea"
          size="sm"
          v-model="text"
          v-if="feedbackArea == true"
          placeholder="오류를 제보해주세요. 피드백은 언제나 환영합니다. 감사합니다:)"
        ></b-form-textarea>
      </b-card>
    </div>
  </div>
</template>

<script>
import ruleList from "./components/rule-list.vue"

export default {
  name: 'App',
  components: {
    ruleList
  },
  data() {
    return {
      fields: [
        {key: '시설'}, 
        {key: '운영시간', formatter: 'openingHour'}, 
        {key: '이용가능대상'}],
      items: [
        { isActive: false, 시설: '식당‧카페', 운영시간: {close: '22'}, 이용가능대상: '접종 완료자' },
        { isActive: false, 시설: '영화관‧공연장', 운영시간: {open: '22', close: '24'}, 이용가능대상: '접종 여부 구분없음' },
        { isActive: false, 시설: '학원', 운영시간: {close: '22'}, 이용가능대상: '접종 여부 구분없음' },
        { isActive: true, 시설: '독서실·스터디카페', 운영시간: {close: '제한 없음'}, 이용가능대상: '접종 여부 구분없음' },
        { isActive: true, 시설: '오락실', 운영시간: {close: '22'}, 이용가능대상: '접종 여부 구분없이 4㎡당 1명' },
        { isActive: true, 시설: '도서관', 운영시간: {close: '제한 없음'}, 이용가능대상: '접종 여부 구분없음' },
        { isActive: true, 시설: '박물관·미술관·과학관', 운영시간: {close: '제한 없음'}, 이용가능대상: '접종 여부 구분없음' },
        { isActive: true, 시설: '놀이공원‧워터파크', 운영시간: {close: '제한 없음'}, 이용가능대상: '접종 여부 수용인원의 50%' },
        { isActive: true, 시설: '실외체육시설', 운영시간: {close: '제한 없음'}, 이용가능대상: '접종 여부 구분없이, 밀집도 제한 없음' },
        { isActive: true, 시설: '백화점·상점·마트(300㎡이상)', 운영시간: {close: '제한 없음'}, 이용가능대상: '접종 여부 구분없이, 밀집도 제한 없음' },
        { isActive: true, 시설: '전시회‧박람회', 운영시간: {close: '제한 없음'}, 이용가능대상: '접종 구분 없이 50명 미만(4㎡당 1명)' },
      ],
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
