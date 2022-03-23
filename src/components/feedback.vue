<template>
    <div id="feedback">
        <div class="black-bg"></div>
        <b-form ref="form" id="feedback-area" @submit.prevent="submitFeedback" @reset="resetFeedback">
            <b-form-textarea name="feedback" vmodel="feedback" rows="5" placeholder="오류를 제보해주세요. 피드백은 언제나 환영합니다. 감사합니다:)">
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
            })
        },
        resetFeedback() {
            this.feedback = ''
        },
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
  background: rgba(0, 0, 0, 0.5);
  z-index: 4;
}

#feedback-area {
  position: relative;
  width: 630px;
  height: 200px;
  display: flex; 
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 10px;
  border-radius: 0.25rem;
  padding: 10px;
  background: white;
  margin: auto;
  z-index: 5;
}
</style>