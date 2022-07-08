<template>
  <div class="field">
    <input
      :type="type"
      :id="name"
      :name="name"
      :placeholder="label"
      v-model="value"
      class="field__input"
      :class="{ 'is-value': value }"
    />
    <label :for="name" class="field__label">{{ label }}</label>
    <span class="field__helper-text"></span>
  </div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits, withDefaults, computed } from "vue";

interface Props {
  type?: string;
  modelValue: string;
  name: string;
  label: string;
}

const props = withDefaults(defineProps<Props>(), {
  type: "text",
});

const emit = defineEmits<{
  (e: "update:modelValue", value: string): void;
}>();

const value = computed<string>({
  get() {
    return props.modelValue;
  },
  set(value) {
    emit("update:modelValue", value);
  },
});
</script>

<style scoped lang="scss">
.field {
  position: relative;

  &__input {
    width: 100%;
    padding: 12px 16px;
    border: 1px solid var(--color-gray);
    border-radius: 0.25rem;
    outline: none;

    &,
    &::placeholder {
      font-family: var(--font-family);
      font-size: 1rem;
      line-height: 1.5;
    }

    &.is-value,
    &:focus {
      padding: 20px 16px 4px;
      &::placeholder {
        opacity: 0;
      }
      & + label {
        display: inline-block;
      }
    }

    &:focus {
      border-color: var(--color-dark);
      box-shadow: inset 0px 0px 0px 1px var(--color-dark);
    }
  }

  &__label {
    position: absolute;
    display: none;
    top: 4px;
    left: 16px;
    font-size: 0.75rem;
    font-weight: 500;
  }
}
</style>
