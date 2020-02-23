<template>
  <div class="container">
    <Message
      name="Emma"
      src="emma-photo"
      :text="message"
    />
    <ShareCode
      :description="shareMessage"
    />
    <SendCode
      :description="sendMessage"
    />
  </div>
</template>
<script>
import Message from '~/components/Message.vue';
import SendCode from '~/components/SendCode.vue';
import ShareCode from '~/components/ShareCode.vue';
import { LOCALE } from '~/constants/locale.js';
export default {
    // layout     : 'header',
    components : {
        Message,
        SendCode,
        ShareCode
    },
    created() {
        this.message = LOCALE.MESSAGE.NEW_SUBSCRIBER;
        this.sendMessage = LOCALE.MESSAGE.SEND;
        this.shareMessage = LOCALE.MESSAGE.SHARE;
    }
};
</script>
<style>
.container {
    margin: 0 auto;
    position: relative;
    max-width: 792px;
    padding-top: 48px;
}
@media (max-width: 792px) {
    .container{
        width: 768px;
    }
}
@media (max-width: 768px){
    .container {
        padding: 30px 16px 0;
        width: 100%
    }
}
</style>
