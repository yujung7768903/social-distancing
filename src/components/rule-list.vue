<template>
  <div id="rule-list">
    <b-card>
        <b-table bordered sticky-header :items="items" :fields="fields" :tbody-tr-class="rowClass">
            <template #table-colgroup="scope">
            <col
                v-for="field in scope.fields"
                :key="field.key"
                :style="{ width: field.key === '운영시간' ? '105px' : 'auto' }"
            >
            </template>
        </b-table>
    </b-card>
  </div>
</template>

<script>
export default {
  name: 'rule-list',
  props: {
    
  },
  data() {
      return {
        fields: [
        {key: '시설'}, 
        {key: '운영시간', formatter: 'openingHour'}, 
        {key: '상세'}],
        items: [
            { isActive: false, 시설: '유흥시설', 운영시간: {close: '24'}, 상세: '취식: 콜라텍·무도장은 불가능, 그 외 유흥시설 가능' },
            { isActive: false, 시설: '식당‧카페', 운영시간: {close: '24'}, 상세: '시설 내 춤추기 금지, 테이블 간 이동 금지, 24시 이후 포장 가능' },
            { isActive: false, 시설: '노래(코인) 연습장', 운영시간: {close: '24'}, 상세: '취식: 불가' },
            { isActive: false, 시설: '영화관‧공연장', 운영시간: {open: '24'}, 상세: '종료시각은 익일 1시 초과 금지, 취식 불가, 지정된 좌석에서만 관람하도록 안내' },
            { isActive: false, 시설: '학원', 운영시간: {close: '24'}, 상세: '취식: 불가, 환기‧소독 : 1일 3회 이상 환기 및 1회 이상 소독' },
            { isActive: true, 시설: '독서실·스터디카페', 운영시간: {close: '제한 없음'}, 상세: '취식: 불가, 환기‧소독 : 1일 3회 이상 환기 및 1회 이상 소독' },
            { isActive: true, 시설: 'PC방, 오락실', 운영시간: {close: '24'}, 상세: '취식: 불가' },
            { isActive: true, 시설: '도서관', 운영시간: {close: '제한 없음'}, 상세: '취식: 불가, 사전예약제 운영' },
            { isActive: true, 시설: '박물관·미술관·과학관', 운영시간: {close: '제한 없음'}, 상세: '취식: 불가, 사전예약제 운영' },
            { isActive: true, 시설: '놀이공원‧워터파크', 운영시간: {close: '제한 없음'}, 상세: '취식: 가능' },
            { isActive: true, 시설: '실외체육시설', 운영시간: {close: '제한 없음'}, 상세: '취식: 가능, 경기에 참여하는 인원은 종목별 인원의 1.5배까지 경기(시합) 가능' },
            { isActive: true, 시설: '백화점·상점·마트(300㎡이상)', 운영시간: {close: '제한 없음'}, 상세: '취식: 불가, 시식‧시음‧견본품(마스크벗는 경우) 서비스 금지, 호객행위(함성 등 판촉) 금지' },
            { isActive: true, 시설: '전시회‧박람회', 운영시간: {close: '제한 없음'}, 상세: '취식: 불가' },
            { isActive: true, 시설: '종교시설', 운영시간: {close: '제한 없음'}, 상세: '취식: 불가, 정규종교활동의 경우, 수용인원의 70% 내에서 허용' },
        ],
    }
  },
  methods: {
    openingHour(value) {
      if (value.close === "제한 없음") {
        return `제한 없음`
      }
      else if(value.open) {
        return `시작: ~${value.open}시`
      }
      else {
        return `종료: ~${value.close}시`
      }
    },
    rowClass(item) {
      if (item.운영시간.close === "제한 없음") {
        return "no-limit"
      }
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
#rule-list {
  width: 100%;
}
.no-limit {
  background-color: var(--color-sky-blue);
}
.card > .card-body > .b-table-sticky-header {
  margin-bottom: 0px;
}

.b-table-sticky-header > .table.b-table > thead, 
.b-table-sticky-header > .table.b-table > tbody,
.b-table-sticky-header > .table.b-table > thead > tr {
  border-top: none;
}

.b-table-sticky-header > .table.b-table > thead > tr > th {
  background-color: var(--color-light-gray);
}

th:after,
th:before {
  content: '';
  position: absolute;
  left: 0;
  width: 100%;
}

th:before {
  top: 0px;
  border-top: 1px solid var(--color-gray);
}

th:after {
  bottom: -1px;
  border-bottom: 2px solid var(--color-gray);
}

</style>