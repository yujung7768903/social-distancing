<template>
  <div id="app">
    <div id="app-content">
      <div class="meeting-container">
        <b-card class="small" header="사적 모임">
          <b-card-text>전국 6인</b-card-text>
        </b-card>
        <b-card class="small" header="행사·집회">
          <b-card-text>50명 미만: 접종자·미접종자 구분없이 가능</b-card-text>
          <b-card-text>50명 이상: 접종완료자 등으로만 구성하여 299명까지 가능</b-card-text>
        </b-card>
      </div>
      <b-card class="left" header="최신 뉴스">
        <b-card-text>
          사적모임 인원 전국 6인 유지, 영업시간 22시로 완화, 내일부터 즉시 시행(2.19~3.13)
        </b-card-text>
        <b-button href="http://ncov.mohw.go.kr/tcmBoardView.do?brdId=&brdGubun=&dataGubun=&ncvContSeq=370247&contSeq=370247&board_id=&gubun=ALL" variant="primary">보러가기</b-button>
      </b-card>
      <b-table :items="items" :fields="fields"></b-table>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
    
  },
  data() {
    return {
      fields: ['시설', '운영시간', '이용가능대상'],
        items: [
          { isActive: false, "시설": "영화관‧공연장", "운영시간": '시작: ~22시 | 종료: ~24시', "이용가능대상": '접종 여부 구분없음' },
          { isActive: false, "시설": "학원", "운영시간": '종료: ~22시', "이용가능대상": '접종 여부 구분없음' },
          { isActive: true, "시설": "독서실·스터디카페", "운영시간": '제한 없음', "이용가능대상": '접종 여부 구분없음' }
        ]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 30px;
}
#app-content {
  width: 630px;
  display: flex;
  flex-direction: column;
  gap: 30px;
  justify-content: center;
  align-items: center;
}
.card {
  width: 100%;
}
.card.left {
  text-align: left;
}
.small.card {
  width: 300px;
}
.card-body {
  vertical-align: center;
}
.meeting-container {
  display: flex; 
  flex-direction: row; 
  gap: 30px;
  justify-content: center;
}
</style>
