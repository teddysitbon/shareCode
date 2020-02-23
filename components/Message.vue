<template>
  <div class="message">
    <div class="message-image">
      <img
        class="image-avatar"
        :src="require(`@/assets/` + src + `.png` )"
      >
    </div>
    <div class="message-description">
      <div class="message-name">
        {{ name }}
      </div>
      <div
        class="message-text"
        v-html="text"
      />
    </div>
  </div>
</template>
<script>
export default {
    props : {
        src : {
            type    : String,
            default : 'emma-photo'
        },
        name : {
            type    : String,
            default : 'Emma'
        },
        text : {
            type    : String,
            default : ''
        }
    }
};

</script>
<style lang="scss">
.message{
    display: flex;
    margin-bottom: 20px;
    &-image{
        width: 48px;
        height: 48px;
        margin-right: 16px;
    }
    &-name{
        font-weight: 900;
        margin-bottom: 6px;
    }
}
.image-avatar{
    display: block;
    width: 100%;
}
</style>
