<template>
  <div class="code">
    <input
      class="code-input"
      disabled
      type="text"
      :value="code"
    >
    <input
      id="codeCopy"
      class="code--hide"
      type="hidden"
      :value="code"
    >
    <button
      :class="classObject"
      @click.stop.prevent="copyCode"
    >
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
        }
    },
    data() {
        return {
            copiedAnimation : false,
            text            : 'Copy code'
        };
    },
    computed : {
        classObject() {
            return [
                {
                    'code-button--active' : this.copiedAnimation === true
                },
                'code-button'
            ];
        }
    },
    methods : {
        copyCode() {
            const codeToCopy = document.querySelector('#codeCopy');
            codeToCopy.setAttribute('type', 'text');
            codeToCopy.select();
            document.execCommand('copy');
            codeToCopy.setAttribute('type', 'hidden');
            this.text = 'Copied !';
            this.copiedAnimation = true;
        }
    }
};

</script>
<style lang="scss">
@import "~/scss/variables.scss";
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
        background-color: $blueLight;
        color: $blue;
        padding-left: 24px;
        width: 300px;
        height: 48px;
        font-size: 16px;
        cursor: text;
    }
    &-button{
        background: $blue;
        border: 0px;
        color: $white;
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
        cursor: copy;
        transition: 0.6s;
        &:hover,
        &:focus,
        &:active{
            opacity: 0.8;
        }
        &--active{
            background-color: $grey;
            cursor: default;
        }
    }
    &--hide{
        position: absolute;
        top: -999px;
        left: -999px;
        opacity: 0;
        z-index: -1;
    }
}
.button-img{
    margin-right: 16px;
}
/*
@keyframes test {
  50% {
    width: 18px;
    height: 18px;
    margin-right: 14px;
  }
  100% {
    width: 16px;
    height: 16px;
    margin-right: 16px;
  }
}
@keyframes toust {
  100% {
    background-color:
  }
}
*/
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
