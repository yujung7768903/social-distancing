<template>
<b-card>
    <b-table bordered sticky-header :items="items" :fields="fields" :tbody-tr-class="rowClass">
        <template #table-colgroup="scope">
        <col
            v-for="field in scope.fields"
            :key="field.key"
            :style="{ width: field.key === '운영시간' ? '100px' : 'auto' }"
        >
        </template>
    </b-table>
</b-card>
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
    }
  },
  methods: {
    openingHour(value) {
      if (value.close === "제한 없음") {
        return `제한 없음`
      }
      else if(value.open && value.close) {
        return `시작: ~${value.open}시 종료: ~${value.close}시`
      }
      else {
        return `종료: ~${value.close}시`
      }
    },
    rowClass(item) {
      console.log(item.운영시간.close);
      if (item.운영시간.close === "제한 없음") {
        return "no-limit"
      }
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.b-table-sticky-header > .table.b-table > thead > tr > th {
  background-color: var(--color-light-gray);
}
.no-limit {
  background-color: var(--color-sky-blue);
}
</style>