<template>
    <div id="feedback">
        <div class="black-bg"></div>
        <b-form ref="form" id="feedback-area" @submit.prevent="submitFeedback" @reset="resetFeedback">
            <img class="btn-close" @click="closeFeedback" src="../assets/btn_close.png" alt="">
            <span>이메일</span>
            <b-form-input name="email" type="email" placeholder="이메일을 남겨주시면, 오류 수정이 완료되었을 때 알려드립니다."></b-form-input>
            <span>오류제보</span>
            <b-form-textarea name="feedback" vmodel="feedback" rows="5" placeholder="피드백은 언제나 환영합니다. 감사합니다:)">
            </b-form-textarea>
            <div class="horizontal container center">
                <b-button class="point box" type="submit">제출</b-button>
                <b-button type="reset">초기화</b-button>
            </div>
        </b-form>
    </div>
</template>

<script>
import emailjs from '@emailjs/browser';

export default {
    name: 'feedback',
    data() {
        return {
            feedback: ''
        }
    },
    methods: {
        submitFeedback() {
            console.log("submitFeedback");
            emailjs.sendForm('social-distancing', 'template_c0hvs17', this.$refs.form, 'gZx2q2lwJSMSqEG8f')
            .then((result) => {
                console.log(result);
            }, (error) => {
                console.log(error);
            });
            this.closeFeedback();
        },
        resetFeedback() {
            this.feedback = '';
        },
        closeFeedback() {
            this.$emit('_closeFeedbackArea');
        }
    }
}
</script>

<style>
#feedback {
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    z-index: 3;
}

.black-bg {
  position: fixed;
  width: 100%; 
  height: 100%;
  top: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.7);
  z-index: 4;
}

#feedback-area {
  position: relative;
  width: 630px;
  /* height: 200px; */
  display: flex; 
  flex-direction: column;
  justify-content: center;
  align-items: left;
  gap: 20px;
  border-radius: 0.25rem;
  padding: 25px 20px;
  background: white;
  margin: auto;
  z-index: 5;
}

#feedback-area > span {
    text-align: left;
}

#feedback-area > .btn-close {
    position: absolute;
    top: 15px;
    width: 20px;
    height: 20px;
    align-self: flex-end;
}

#feedback-area > .btn-close:hover {
    opacity: 1;
}
</style>