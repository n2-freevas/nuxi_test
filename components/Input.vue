<script setup lang="ts">
    import { computed, InputHTMLAttributes } from 'vue'

    interface Emits {
        (e: 'update:modelValue', value: string): void
    }
    const emit = defineEmits<Emits>()
    
    interface Props extends /* @vue-ignore */ InputHTMLAttributes {
        modelValue: string
        width?: string
        limit?: number
        ph: string
    }
    const props = defineProps<Props>()

    const defs = computed(() => {
        const { modelValue, ...originals } = props
        return { modelValue, originals }
    })
    const styles = computed(() => {
        const width = props.width ?? "unset"
        return {
            '--vcInputWidth': width
        }
    })
    const value = computed({
        get: () => defs.value.modelValue,
        set: (value: string) => {
            emit('update:modelValue', value)
        }
    })
</script>

<template>
    <div class="vcInput" :style="styles">
        <input v-model="value" v-bind="defs.originals" :placeholder="ph"/>
    </div>
</template>

<style lang="scss" scoped>
    .vcInput{
        margin:0 auto;
        text-align: center;
        // width: var(--vcInputWidth);
    }
    input{
        width: var(--vcInputWidth);
        border-radius: 10px;
        border: solid 1px #929292;
        padding:5px 30px;
        font-size: 20px;
        font-weight: bold;
        text-align: center;
    }
</style>
