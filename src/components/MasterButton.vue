<script>
export default {
    name: "MasterButton",
    emits: ["clickBtn"],
props: {
    buttonDisabled: {
        type: Boolean,
        default: false,
    },
    buttonTitle:{
        type: String,
        required: true,
    }
    },

    methods: {


        clickBtn() {
            this.$emit("clickBtn")
            }
    },
};
</script>

<template>
    <div class="master-button">
        <button class="master-button__btn btn"
                :disabled="buttonDisabled"
            :class="{ 'master-button_disabled': buttonDisabled }"
            @click='clickBtn'>
            {{buttonTitle}}
        </button>
    </div>
</template>

<style lang="scss" scoped>
.master-button__btn {
    width: 141px;
    height: 48px;
    background: #FFDA7A;
    color: #212121;
    border-radius: 8px;
font-size: 16px;
    &:hover {
        box-shadow: 0px 0px 20px 0px #FFDA7A;

    }
    &:active {
        box-shadow: 0px 0px 20px 0px #FFDA7A;
        transform: translateY(1px)
    }
    &:disabled {
        cursor: not-allowed;
        opacity: 50%;
    }
    }

</style>