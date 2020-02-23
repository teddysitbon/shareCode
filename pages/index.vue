<template>
  <div class="container">
    <Message
      src="emma-photo"
      name="Emma"
      text="Don’t forget that for each new subscriber you refer, both you and them get <b>one free month</b> of coverage! 💙"
    />
    <ShareCode
      code="SHARETHELOVE+5WMXM"
      description="Share your <b>one free month</b> referral code"
    />
    <SendCode
      description="You can also send <b>one free month</b> via email, separate emails with semicolon « ; »"
    />
  </div>
</template>
<script>
import Message from '~/components/Message.vue';
import SendCode from '~/components/SendCode.vue';
import ShareCode from '~/components/ShareCode.vue';
export default {
    layout     : 'header',
    components : {
        Message,
        SendCode,
        ShareCode
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
@media (max-width: 768px){
    .container {
        padding: 30px 16px 0;
    }
}
</style>
