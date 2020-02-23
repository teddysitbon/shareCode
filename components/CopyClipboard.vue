<template>
  <div class="code">
    <input
      class="code-input"
      disabled
      type="text"
      :value="code"
    >
    <button class="code-button">
      <img
        class="button-img"
        src="~assets/copy-icon.svg"
      >
      {{ text }}
    </button>
  </div>
</template>
<script>
export default {
    props : {
        code : {
            type     : String,
            required : true
        },
        text : {
            type    : String,
            default : ''
        }
    }
};

</script>
<style lang="scss">
.code{
    display: inline-flex;
    &-input{
        margin:0;
        border:0;
        white-space:normal;
        background:none;
        line-height:1;
        font-weight: 500;
        flex-direction: row;
        display: flex;
        -webkit-box-align: center;
        align-items: center;
        background-color: #edf5fe;
        color: #0042da;
        padding-left: 24px;
        width: 300px;
        height: 48px;
        font-size: 16px;
        cursor: text;
    }
    &-button{
        background: #0042da;
        border: 0px;
        color: white;
        font-size: 16px;
        padding: 0 24px;
        display: flex;
        -webkit-box-align: center;
        align-items: center;
        width: 164px;
        cursor: pointer;
        border-top-right-radius: 4px;
        border-bottom-right-radius: 4px;
        outline: none;
        &:hover,
        &:focus,
        &:active{
            opacity: 0.8;
        }
    }
}
.button-img{
    padding-right: 16px;
}
@media (max-width: 768px){
    .code {
        display: flex;
        margin-bottom: 5px;
        .code-input{
            flex: 1;
        }
    }
    /*
    .code .code-input{
        flex: 1;
    }
    .code .code-input{
        padding-left: 14px;
        width: 200px;
        height: 40px;
        font-size: 14px;
    }
    .code .code-button{
        font-size: 14px;
        padding: 0 16px;
        width: 143px;
    }
    */
}
</style>
