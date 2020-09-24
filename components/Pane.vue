<template>
  <div :class="{ pane: true, [panestyle]: true }">
    <div class="pane-inner">
      <slot />
    </div>
  </div>
</template>
<script lang="ts">
import Vue from 'vue'
import Component from 'vue-class-component'

@Component({})
export default class Pane extends Vue {
  panestyle = 'default'
}
</script>
<style lang="scss">
.pane {
  .pane-inner {
    padding: 2px;
  }

  &.muddy-slate,
  &.footer {
    background: #8e8e8e;
    background-image: url('~assets/muddyslate.jpg');
    background-blend-mode: multiply;

    border: #51473d 1px solid;
  }

  &.footer {
    min-height: 200px;
  }
}
</style>
