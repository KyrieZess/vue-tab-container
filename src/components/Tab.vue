<template>
  <b-tab
    :title="title"
    title-item-class="eh-tabs-item"
    title-link-class="eh-tabs-link"
    @click="$emit('click')"
    :disabled="disabled"
  >
    <template #title>
      <slot name="title">{{ title }}</slot>
    </template>
    <slot></slot>
  </b-tab>
</template>
<script>
export default {
  name: "FpTab",
  props: {
    title: String,
    disabled: Boolean,
  },
};
</script>
