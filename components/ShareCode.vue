<template>
  <div class="share">
    <div
      class="share-description"
      v-html="description"
    />
    <div class="share-code">
      <CopyClipboard
        :code="this.$store.state.code"
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
        description : {
            type    : String,
            default : ''
        }
    },
    methods : {
        shareOnFacebook() {
            console.log('Share on Facebook');
        },
        shareTweet() {
            const CODE = this.$store.state.code;
            const PARAMS = encodeURIComponent(LOCALE.TWITTER.SHARE + CODE);
            const LINK = TWITTER_SHARE_LINK + PARAMS;
            window.open(LINK, '_blank');
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
/*
@media (max-width: 1075px) {
  .header-container{
    padding: 0;
    width: 792px;
  }
}
@media (max-width: 792px) {
  .header-container{
    padding: 0;
    width: 768px;
  }
}
@media (max-width: 768px) {
  .header-description{
    display: none;
  }
  .header-container{
    padding: 0 16px;
    width: 100%;
  }
  .logout{
    margin-right: 12px;
  }
}
*/
@media (max-width: 792px){
    .share {
        margin-left: 0;
        margin-bottom : 25px;
        &-description{
            margin-bottom: 5px;
        }
        &-code {
            display: block;
        }
        &-social {
          display: flex;
          justify-content: flex-start;
          .button{
            width: 49%;
            margin-left: 0px;
            height: 40px;
            font-size: 12px;
          }
          .button:first-child{
              margin-right: 2%;
          }
        }
    }
}
</style>
