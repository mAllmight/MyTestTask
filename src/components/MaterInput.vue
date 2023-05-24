<script>
export default {
    name: "MaterInput",

    emits: ["setInputValue"],

    props: {
        inputValue: {
            type: String,
            required: true,
        },

        errorMessage: {
            type: String,
            default: "",
        },

        isDisabled: {
            type: Boolean,
            default: false,
        },

        label: {
            type: String,
            default: "",
        },

        placeholder: {
            type: String,
            default: "",
        },

        type: {
            type: String,
            default: "text",
        },
    },

    methods: {
        setInputValue(event) {
            this.$emit("setInputValue", event.target.value);
        },
    },
};
</script>

<template>
    <div class="mater-input">
        <label class="mater-input__label" html="master-input-id">{{
                label
            }}</label>
        <input
            class="mater-input__input input"
            :class="{ input_error: errorMessage !== '' }"
            :value="inputValue"
            :type="type"
            :placeholder="placeholder"
            :disabled="isDisabled"
            @input="setInputValue"
            id="master-input-id"
        />
        <span class="mater-input__error-messages" v-if="errorMessage">{{
                errorMessage
            }}</span>
    </div>
</template>

<style lang="scss" scoped>
.mater-input {
    width: 270px;
    border-radius: 8px;
    cursor: pointer;
    position: relative;

    &__label {
        font-size: 14px;
        color: #969696;
        margin-bottom: 8px;
        display: block;
    }

    .input {
        height: 48px;
        font-size: 16px;
        width: 100%;
        border-radius: 8px;
        padding: 0 16px;
        background: #f8f8f8;
        border: 1px solid #f3f3f3;

        &[type="text"] {
            font-size: 16px;
            color: #212121;
        }

        &::placeholder {
            font-size: 16px;
            color: #969696;
        }

        &:disabled {
            cursor: not-allowed;
        }

        &:hover {
            border: 1px solid #f3f3f3;
            background: #f8f8f8;
        }

        &:focus {
            border: 1px solid #ffda7a;
            background: #f8f8f8;
        }

        &_error {
            border: 1px solid #eb5757 !important;
        }
    }

    &__error-messages {
        display: block;
        margin-top: 8px;
        color: #eb5757;
    }
}
</style>
