<script>
import { defineComponent } from 'vue'
import MasterInput from '@/components/MasterInput.vue'
import MasterSelector from '@/components/MasterSelector.vue'

export default defineComponent({
    components: {
        MasterSelector,
        MasterInput
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
            }
        }
    },

    methods: {
        setInputValueHandler(value) {
            this.inputValue = value
        },

        choiceItemHandler(id) {
            this.selectorValue = this.selectorOptions.find((item) => item.id === id)
        }
    }
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
