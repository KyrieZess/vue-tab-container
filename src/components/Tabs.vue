<template>
  <div>
    <b-tabs
      class="eh-tabs"
      active-nav-item-class="eh-active-tab"
      fill
      :lazy="lazy"
      @activate-tab="activateTab"
    >
      <b-tab
        v-for="(tab, tabIndex) in tabs"
        :key="'tab-' + tabIndex"
        title-item-class="eh-tabs-item"
        title-link-class="eh-tabs-link"
        class="eh-tab-content"
        :disabled="disabledTabs && !tab[noneDisabledKey]"
      >
        <template #title>
          <slot name="title" v-bind="tab"></slot>
        </template>
        <slot name="content" v-bind="tab">
          {{ tab }}
        </slot>
      </b-tab>
      <slot></slot>
    </b-tabs>
  </div>
</template>
<script>
export default {
  name: "Tabs",
  props: {
    tabs: Array,
    lazy: {
      type: Boolean,
      default: true,
    },
    disabledTabs: Boolean,
    noneDisabledKey: String,
  },
  methods: {
    activateTab(newTab, prevTab, bvEvent) {
      this.$emit("activateTab", {
        NewTabIndex: newTab,
        PrevTabIndex: prevTab,
        BvEvent: bvEvent,
      });
    },
  },
};
</script>
<style>
.eh-tabs .eh-tabs-link {
  color: #000;
  font-weight: 900;
  border-radius: 0 !important;
  background: #dfdfdf !important;
  outline: none;
  border-width: 1px !important;
  border-color: white !important;
}

.eh-tabs .eh-tabs-link:hover {
  background-color: #a4a4a4 !important;
}

.eh-tabs .eh-tabs-link.eh-active-tab {
  color: white !important;
  background-color: #000 !important;
}

.eh-tabs .eh-tabs-link.eh-active-tab:hover {
  background-color: #555555 !important;
}

.eh-tabs .eh-tabs-link.disabled {
  opacity: 0.7;
}

.eh-tabs .tab-content {
  background: white;
  border-radius: 0 0 10px 10px;
  border-color: #a3a3a3 !important;
  border: 1px solid;
  padding: 0px 10px 10px 10px;
}
</style>
