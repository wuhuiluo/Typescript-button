<template>
  <div>
    <button
      :class="{'ui-btn-large' : large,
    'ui-btn-small' : small,
    'ui-btn-xlarge': xlarge,
    'ui-btn-xsmall': xsmall,
    'ui-btn-tile': tile,
    'ui-btn-rounded': rounded,
    'ui-btn-circle': circle,
    'ui-btn-disabled': disabled
    }"
      :style="`
       --color-tint: ${TintColor}
    `"
      @click="onClickBtn"
      class="ui-btn"
    >
      <slot>button</slot>
    </button>
  </div>
</template>


<script lang="ts">
import { Component, Vue, Emit, Prop } from "vue-property-decorator";
@Component
export default class UIbutton extends Vue {
  @Prop(Boolean) private xsmall: boolean | undefined;
  @Prop(Boolean) private small: boolean | undefined;
  @Prop(Boolean) private large: boolean | undefined;
  @Prop(Boolean) private xlarge: boolean | undefined;
  @Prop(Boolean) private tile: boolean | undefined;
  @Prop(Boolean) private rounded: boolean | undefined;
  @Prop(Boolean) private circle: boolean | undefined;
  @Prop(Boolean) private disabled: boolean | undefined;
  @Prop(String) private color: string | undefined;
  @Emit("click")
  private emitClickEvent(event: MouseEvent) {}
   // computed
  private get TintColor() {
    if (this.color) {
      return this.color;
    } else {
      return "#2DBCF0";
    }
  }
  private mounted() {
    // console.log(this.large);
  }
  private onClickBtn(event: MouseEvent) {
    if (!this.disabled) {
      this.emitClickEvent(event);
    }
  }
}
</script>


<style lang="stylus" scope>
resize(minWidth, height, paddingLR, fontSize) {
  min-width: minWidth;
  height: height;
  padding: 0 paddingLR;
  font-size: fontSize;

  &.ui-btn-rounded, &.ui-btn-circle {
    border-radius: (@height / 2);
  }

  &.ui-btn-circle {
    min-width: 0;
    padding: 0;
  }
}

.ui-btn {
  resize(64px, 36px, 36px, 0.875rem);
  border-radius: 4px;
  font-weight: 500;
  letter-spacing: 0.09em;
  outline: none;
  border: 0 solid black;
  background-color: var(--color-tint);
  user-select: none;
  cursor: pointer;
  &:hover {
    filter brightness(120%)
  }
  &:active {
    filter brightness(80%)
  }
  &.ui-btn-large {
    resize(80px, 44px, 19px, 0.875rem);
  }

  &.ui-btn-small {
    resize(50px, 28px, 12px, 0.75rem);
  }

  &.ui-btn-xsmall {
    resize(30px, 20px, 9px, 0.625rem);
  }

  &.ui-btn-xlarge {
    resize(120px, 52px, 23px, 1rem);
  }

  &.ui-btn-tile {
    border-radius: 0;
  }

  &.ui-btn-rounded {
    border-radius: (@height / 2);
  }

  &.ui-btn-disabled {
    background-color: #F5F5F5;
    color: #C5C8CE;
    cursor: not-allowed;
  }
}
</style>