<template>
  <div class="share">
    <div
      class="share-description"
      v-html="description"
    />
    <div class="share-code">
      <CopyClipboard
        :code="code"
      />
      <div class="share-social">
        <Button
          icon="twitter-icon.svg"
          text="Tweet"
          text-indent
          type="blue"
          @handleClick="shareTweet"
        />
        <Button
          icon="facebook-icon.png"
          text="Share"
          text-indent
          type="blue"
          @handleClick="shareOnFacebook"
        />
      </div>
    </div>
  </div>
</template>
<script>
import Button from '~/components/Button.vue';
import CopyClipboard from '~/components/CopyClipboard.vue';
import { LOCALE } from '~/constants/locale.js';
import { TWITTER_SHARE_LINK } from '~/constants/';
export default {
    components : {
        Button,
        CopyClipboard
    },
    props : {
        code : {
            type     : String,
            required : true
        },
        description : {
            type    : String,
            default : ''
        }
    },
    methods : {
        shareTweet() {
            const PARAMS = encodeURIComponent(LOCALE.TWITTER.SHARE + this.code);
            const LINK = TWITTER_SHARE_LINK + PARAMS;
            window.open(LINK, '_blank');
        },
        shareOnFacebook() {
            console.log('Share on Facebook ', this.code);
        }
    }
};
</script>
<style lang="scss">
.share{
    margin-left: 62px;
    margin-bottom: 32px;
    &-description{
        margin-bottom: 16px;
    }
    &-code{
        flex-direction: row;
        display: flex;
        -webkit-box-align: center;
        align-items: center;
        -webkit-box-pack: start;
        justify-content: flex-start;
    }
    &-social{
        flex-direction: row;
        display: inline-flex;
        -webkit-box-align: center;
        align-items: center;
        -webkit-box-pack: end;
        justify-content: flex-end;
        flex: 1 1 0%;
    }
}
@media (max-width: 768px){
    .share {
        margin-left: 0;
        &-code {
            display: block;
        }
    }
}
</style>
