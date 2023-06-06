<script>
import { defineComponent } from 'vue'
import MasterInput from '@/components/MasterInput.vue'
import MasterSelector from '@/components/MasterSelector.vue'
import MasterButton from "@/components/MasterButton.vue";
import FilterSelector from "@/components/FilterSelector.vue";

export default defineComponent({
    components: {
        MasterButton,
        MasterSelector,
        MasterInput,
        FilterSelector
    },

    data() {
        return {
            inputValue: '',
            inputErrorMessage: '',
            inputLabel: 'Мой инпут',
            inputPlaceholder: 'Мой Placeholder',
            inputDisabled: false,

            selectorLabel: 'Label',
            selectorPlaceholder: 'Мой селектор',
            selectorDisabled: false,
            selectorOptions: [
                {
                    name: 'Значение 1',
                    id: 1
                },
                {
                    name: 'Значение 2',
                    id: 2
                },
                {
                    name: 'Значение 3',
                    id: 3
                },
                {
                    name: 'Значение 4',
                    id: 4
                },
                {
                    name: 'Значение 5',
                    id: 5
                },
                {
                    name: 'Значение 6',
                    id: 6
                },
                {
                    name: 'Значение 7',
                    id: 7
                },
                {
                    name: 'Значение 8',
                    id: 8
                },
                {
                    name: 'Значение 9',
                    id: 9
                },
                {
                    name: 'Значение 10',
                    id: 10
                }
            ],
            selectorValue: {
                name: '',
                id: ''
            },
            buttonDisabled:false,
            buttonTitle:'PRESS',

            filterLabel: 'Label',
            filterPlaceholder: 'Поиск',
            filterDisabled: false,
            filterOptions: [
            {
                name: 'Item 1',
                id: 1
            },
            {
                name: 'Item 2',
                id: 2
            },
            {
                name: 'Item 3',
                id: 3
            },
            {
                name: 'Item 4',
                id: 4
            },
            {
                name: 'Item 5',
                id: 5
            },
            {
                name: 'Item 6',
                id: 6
            },
            {
                name: 'Item 7',
                id: 7
            }],

            filterValue: [{
            name: '',
            id: ''
            }],
        }},

    methods: {
        setInputValueHandler(value) {
            this.inputValue = value
        },

        choiceItemHandler(id) {
            this.selectorValue = this.selectorOptions.find((item) => item.id === id)
        },

        choiceFilterHandler() {
            this.filterValue = this.filterOptions.find((item) => item.id === id)
        },
        choiceCheckHandler() {
            this.filterValue = this.filterOptions.find((item) => item.id === id)
        },
        setClickBtn(){
            console.log('123')
        }
    },

})
</script>

<template>
    <div class="container">
        <MasterInput
                :input-value="inputValue"
                :is-disabled="inputDisabled"
                :placeholder="inputPlaceholder"
                :label="inputLabel"
                :error-message="inputErrorMessage"
                @setInputValue="setInputValueHandler"
        />
        <MasterSelector
                :label="selectorLabel"
                :placeholder="selectorPlaceholder"
                :disabled="selectorDisabled"
                :options="selectorOptions"
                :selector-value="selectorValue"
                @choiceItem="choiceItemHandler"
        />
        <FilterSelector
            :filter-label="filterLabel"
            :filter-placeholder="filterPlaceholder"
            :filter-disabled="filterDisabled"
            :filter-options="filterOptions"
            :filter-value="filterValue"
            @choiceFilterItem="choiceFilterHandler"
            @choiceCheckItem="choiceCheckHandler"
        />
        <MasterButton
            :button-disabled="buttonDisabled"
            :button-title="buttonTitle"
            @clickBtn="setClickBtn"
        />
    </div>
</template>

<style scoped lang="scss">

.container {
  margin: 0 auto;
  padding: 60px;
  display: flex;
  flex-direction: column;
  gap: 30px;
}
</style>
