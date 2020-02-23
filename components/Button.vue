<template>
  <button
    class="button"
    :class="classObject"
    :disabled="disabled"
    @click="handleClick"
  >
    <img
      v-if="icon !== ''"
      class="button-icon"
      :src="require(`@/assets/` + icon )"
    >
    {{ text }}
  </button>
</template>
<script>
export default {
    props : {
        className : {
            type    : String,
            default : ''
        },
        disabled : {
            type    : Boolean,
            default : false
        },
        icon : {
            type    : String,
            default : ''
        },
        text : {
            type     : String,
            required : true
        },
        textIndent : {
            type    : Boolean,
            default : false
        },
        type : {
            type    : String,
            default : 'blue'
        }
    },
    computed : {
        classObject() {
            const buttonColor = `button-${this.type}`;
            const specificClassName = this.className !== '' ? this.className : '';
            return [
                {
                    'button-left' : this.textIndent === true
                },
                buttonColor,
                specificClassName
            ];
        }
    },
    methods : {
        handleClick() {
            this.$emit('handleClick');
        }
    }
};

</script>
<style lang="scss">
@import "~/scss/variables.scss";
.button{
    display: inline-flex;
    border:0px;
    font-weight: 500;
    height: 48px;
    align-items: center;
    padding: 0 26px;
    vertical-align: top;
    border-radius: 4px;
    font-size: 16px;
    cursor: pointer;
    transition: 0.3s all;
    outline: none;
    &[disabled]{
        cursor: default;
    }
    &:hover,
    &:focus,
    &:active{
        opacity: 0.8;
    }

    &-left{
        margin-left: 8px;
    }
    &-blue{
        background: $blue;
        color: $white;
    }
    &-blueLight{
        background: $blueLight;
        color: $blue;
    }
    &-white{
        background: $white;
        color: $blue;
    }
    &-grey{
        background: $grey;
        color: $white;
    }
    &-icon{
        padding-right: 16px;
    }
}
@media (max-width: 792px){
    .button {
        font-size: 14px;
    }
}
</style>
