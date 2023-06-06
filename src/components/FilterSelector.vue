<script>
export default {
    name: "FilterSelector",
    emits: ["choiceFilterItem","choiceCheckItem"],

    props: {
        filterPlaceholder: {
            type: String,
            default: "",
        },
        filterDisabled: {
            type: Boolean,
            default: false,
        },

        filterOptions: {
            type: Array,
            required: true,
        },

        filterValue: {
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
    openOptions() {
    if (!this.filterDisabled) {
        this.isSelectorOpen = !this.isSelectorOpen;
    }},
     choiceFilter(id) {
     this.$emit("choiceFilterItem", id);
            },
        choiceCheck(id) {
            this.$emit("choiceCheckItem", id);
        },
},};
</script>

<template>
    <div class="filter-selector"
    :class="{ 'filter-selector_disabled': filterDisabled }"
    @click="openOptions">
    <div class="filter-selector__placeholder placeholder">
        <p v-if="filterValue.id !==''" class="placeholder__label">{{ filterPlaceholder }}</p>
    </div>
<div class="filter-selector__options options" >

    <template v-for="option in filterOptions" :key="option.id">
       <div class="option__item">
           <div class="options__item" v-on:change="choiceFilter(option.id)">
        {{ option.name }}</div>
        <input type="checkbox" :checked="isChecked" @change="choiceCheck($event.target.checked)"/>
    </div>
</template>
</div>
    </div>
</template>

<style lang="scss" scoped>
.filter-selector {
    margin-top: 350px;
    width: 270px;
    height: 48px;
    border: 1px solid #f3f3f3;
    background: #f3f3f3;
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
.option__item{
    display: flex;
    flex-direction: row-reverse;
}
</style>