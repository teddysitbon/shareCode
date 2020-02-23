<template>
  <div class="send">
    <div
      class="send-description"
      v-html="description"
    />
    <textarea
      v-model="contentMails"
      class="send-field"
      placeholder="amelie.dupont@gmail.com ; jeanmichel@gmail.com"
    />
    <div class="send-email">
      <Button
        class-name="button-send"
        :disabled="nbMails === 0 ? true : false"
        icon="send-icon.svg"
        :text="getTextBtn()"
        :type="nbMails === 0 ? 'grey' : 'blue'"
        @handleClick="sendEmail"
      />
      <div class="send-done">
        <Button
          class-name="button-done"
          text="Done"
          type="blueLight"
          @handleClick="doneEmail"
        />
      </div>
    </div>
  </div>
</template>
<script>
import Button from '~/components/Button.vue';
import { validateEmail } from '~/helpers/email.js';

export default {
    components : {
        Button
    },
    props : {
        description : {
            type    : String,
            default : ''
        }
    },
    data() {
        return {
            contentMails : '',
            nbMails      : 0
        };
    },
    watch : {
        contentMails(value) {
            this.nbMails = 0;
            const CONTENT = value.split(';');
            CONTENT.map((email) => {
                const EMAIL_TRIM = email.trim();
                if (validateEmail(EMAIL_TRIM)) {
                    this.nbMails++;
                }
            });
        }
    },
    methods : {
        doneEmail() {
            console.log('Done');
        },
        getTextBtn() {
            switch (this.nbMails) {
            case 0 :
                return 'Send 0 email';
            case 1 :
                return 'Send 1 email';
            default:
                return `Send ${this.nbMails} emails`;
            }
        },
        sendEmail() {
            const EMAILS_TO_SEND = [];
            const CONTENT = this.contentMails.split(';');
            CONTENT.map((email) => {
                const EMAIL_TRIM = email.trim();
                if (validateEmail(EMAIL_TRIM)) {
                    EMAILS_TO_SEND.push(EMAIL_TRIM);
                }
            });
            console.log('Send email');
            console.log(EMAILS_TO_SEND);
        }
    }
};

</script>
<style lang="scss">
@import "~/scss/variables.scss";
.send{
    margin-left: 62px;
    margin-bottom: 20px;
    &-description{
        margin-bottom: 12px;
    }
    &-field{
        width : 100%;
        border: 1px solid $greyLight;
        border-radius: 4px;
        min-height: 128px;
        padding: 12px 24px;
        font-size: 16px;
        margin-bottom: 16px;
    }
    &-email{
        display: flex;
         .send-done{
            flex-direction: row;
            display: inline-flex;
            align-items: center;
            justify-content: flex-end;
            flex: 1 1 0%;
        }
    }
}
.button-send{
    min-width: 185px;
}
@media (max-width: 792px){
    .send {
        margin-left: 0px;
    }
}
</style>
