<template>
    <label class="checkbox">
        <input
            v-bind="$attrs"
            v-model="value"
            type="checkbox"
            class="checkbox__input"
        />
        <span class="checkbox__box"></span>
        <slot></slot>
    </label>
</template>

<script>
export default {
    name: 'UiCheckbox',

    inheritAttrs: false,

    emits: ['update:modelValue'],

    props: {
        modelValue: {
            type: [Boolean, Array],
        },
    },

    computed: {
        value: {
            get() {
                return this.modelValue;
            },

            set(value) {
                this.$emit('update:modelValue', value);
            },
        },
    },
};
</script>

<style scoped>
.checkbox {
    display: inline-block;
    position: relative;
    padding-left: 44px;
    margin-bottom: 10px;
    text-align: left;
    cursor: pointer;
    font-size: 20px;
    line-height: 28px;
    transition-duration: 0.3s;
    transition-timing-function: ease;
    transition-property: background-color, border-color;
}

.checkbox > input.checkbox__input {
    position: absolute;
    z-index: -1;
    opacity: 0;
    padding: 0;
}

.checkbox > .checkbox__box {
    border: 2px solid var(--blue-light);
}

.checkbox > .checkbox__box {
    border-radius: 8px;
    background: 0 0;
    position: absolute;
    top: 0;
    left: 0;
    height: 28px;
    width: 28px;
}

.checkbox > input.checkbox__input:checked ~ .checkbox__box:after {
    display: block;
}

.checkbox > .checkbox__box:after {
    content: '';
    position: absolute;
    display: none;
    top: 50%;
    left: 50%;
    width: 14px;
    height: 13px;
    background-image: url('~@/assets/icons/icon-check.svg');
    border: none;
    transform: translate(-50%, -50%);
}
</style>
