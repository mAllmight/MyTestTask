<script>
import { defineComponent } from "vue";

export default defineComponent({
    name: "MasterSelector",

    emits: ["choiceItem"],

    props: {
        label: {
            type: String,
            default: "",
        },
        placeholder: {
            type: String,
            default: "",
        },
        disabled: {
            type: Boolean,
            default: false,
        },

        options: {
            type: Array,
            required: true,
        },

        selectorValue: {
            type: Object,
            required: true,
        },
    },

    data() {
        return {
            isSelectorOpen: false,
        };
    },

    methods: {
        choiceItem(id) {
            this.$emit("choiceItem", id);
        },

        openOptions() {
            if (!this.disabled) {
                this.isSelectorOpen = !this.isSelectorOpen;
            }
        },
    },
});
</script>

<template>
    <div class="wrapper">
        <p class="wrapper__label" v-if="label">
            {{ label }}
        </p>

        <div
                class="master-selector"
                :class="{ 'master-selector_disabled': disabled }"
                @click="openOptions"
        >
            <div class="master-selector__placeholder placeholder">
                <p v-if="selectorValue.id !== ''" class="placeholder__label">
                    {{ selectorValue.name }}
                </p>
                <p v-else class="placeholder__placeholder">{{ placeholder }}</p>
                <img
                        src="../assets/icons/selector-arrow.svg"
                        alt=""
                        :class="{ label__arrow_up: isSelectorOpen }"
                />
            </div>

            <div class="master-selector__options options" v-if="isSelectorOpen">
                <template v-for="option in options" :key="option.id">
                    <div class="options__item" @click="choiceItem(option.id)">
                        {{ option.name }}
                    </div>
                </template>
            </div>
        </div>
    </div>
</template>

<style scoped lang="scss">
.wrapper {
  &__label {
    line-height: 10px;
    margin-bottom: 8px;
    margin-left: 4px;
    font-size: 14px;
    color: #969696;
  }

  .master-selector {
    width: 270px;
    height: 48px;
    border: 1px solid #f3f3f3;
    background: #f8f8f8;
    border-radius: 8px;
    cursor: pointer;
    position: relative;
    padding: 0 16px;

    &_disabled {
      cursor: not-allowed;
      border: 1px solid #f3f3f3 !important;
    }

    &:hover {
      border: 1px solid #e9e9e9;
    }

    .placeholder {
      display: flex;
      align-items: center;
      justify-content: space-between;
      font-size: 16px;
      padding: 0;
      margin: 0;
      width: 100%;
      height: 100%;

      &__placeholder {
        color: #969696;
      }

      &__label {
        color: #212121;
      }

      &__arrow_up {
        transform: rotate(180deg);
      }
    }

    .options {
      width: 100%;
      background: #ffffff;
      box-shadow: 0 0 30px rgba(169, 169, 169, 0.15);
      border-radius: 8px;
      max-height: 270px;
      position: absolute;
      top: calc(100% + 8px);
      left: 0;
      overflow-y: auto;
      padding: 8px 0;

      &__item {
        width: 100%;
        padding: 8px 16px;
        color: #212121;
        font-size: 16px;

        &:hover {
          background: #f8f8f8;
        }
      }
    }
  }
}
</style>