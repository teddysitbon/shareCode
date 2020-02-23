<template>
  <div class="send">
    <div
      class="send-description"
      v-html="description"
    />
    <textarea
      v-model="content"
      class="send-field"
      placeholder="amelie.dupont@gmail.com ; jeanmichel@gmail.com"
    />
    <div class="send-email">
      <Button
        class-name="button-send"
        icon="send-icon.svg"
        text="Send 0 email"
        type="grey"
      />
      <div class="send-done">
        <Button
          class-name="button-done"
          text="Done"
          type="blueLight"
        />
      </div>
    </div>
  </div>
</template>
<script>
import Button from '~/components/Button.vue';

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
            content : ''
        };
    }
};

</script>
<style lang="scss">
.send{
    margin-left: 62px;
    margin-bottom: 20px;
    &-description{
        margin-bottom: 12px;
    }
    &-field{
        width : 100%;
        border: 1px solid #dddddd;
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
@media (max-width: 768px){
    .send {
        margin-left: 0px;
    }
}
</style>
