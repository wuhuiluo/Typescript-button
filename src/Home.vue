<template>
  <div class="root-home">
    <div class="btn-container">
      <UIbutton
        color="red"
        :tile="tile"
        :rounded="rounded"
        :circle="circle"
        :xsmall="xsmall"
        :small="small"
        :large="large"
        :xlarge="xlarge"
        @click="onClick"
        :disabled="disabled"
      >123</UIbutton>
    </div>
    <div class="btn-group">
      <UIbutton class="btn" @click="resize('xsmall')">超小</UIbutton>
      <UIbutton class="btn" @click="resize('small')">小</UIbutton>
      <UIbutton class="btn" @click="resize('normal')">正常</UIbutton>
      <UIbutton class="btn" @click="resize('large')">大</UIbutton>
      <UIbutton class="btn" @click="resize('xlarge')">超大</UIbutton>
    </div>
    <div class="btn-group">
      <UIbutton class="btn" @click="reRadius('tile')">矩形</UIbutton>
      <UIbutton class="btn" @click="reRadius('normal')">正常</UIbutton>
      <UIbutton class="btn" @click="reRadius('rounded')">半圆</UIbutton>
      <UIbutton class="btn" @click="reRadius('circle')">圆</UIbutton>
    </div>
    <div class="btn-group">
      <UIbutton class="btn" @click="changeDisabled">禁用</UIbutton>
    </div>
  </div>
</template>


<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import UIbutton from "./components/UIbutton.vue";
@Component({
  components: {
    UIbutton
  }
})
export default class Home extends Vue {
  private xlarge: boolean = false;
  private large: boolean = false;
  private small: boolean = false;
  private xsmall: boolean = false;
  private tile: boolean = false;
  private rounded: boolean = false;
  private circle: boolean = false;
  private disabled: boolean = false;
  private changeDisabled() {
     this.disabled = !this.disabled
  }
  private reRadius(name: string) {
    switch (name) {
      case "tile":
        this.tile = true;
        this.rounded = false;
        this.circle = false;
        break;
      case "rounded":
        this.rounded = true;
        this.tile = false;
        this.circle = false;
        break;
      case "circle":
        this.circle = true;
        this.tile = false;
        this.rounded = false;
        break;
      case "normal":
        this.tile = false;
        this.rounded = false;
        this.circle = false;
        break;
    }
  }
  private resize(name: string) {
    switch (name) {
      case "xsmall":
        this.xsmall = true;
        this.xlarge = false;
        this.large = false;
        this.small = false;
        break;
      case "small":
        this.small = true;
        this.xlarge = false;
        this.xsmall = false;
        this.large = false;
        break;
      case "small":
        this.small = false;
        this.xsmall = false;
        this.xlarge = false;
        this.large = false;
        break;
      case "large":
        this.small = false;
        this.xlarge = false;
        this.xsmall = false;
        this.large = true;
        break;
      case "xlarge":
        this.small = false;
        this.xlarge = true;
        this.xsmall = false;
        this.large = false;
        break;
    }
  }
  private onClick(event: MouseEvent) {
    console.log(event);
  }
}
</script>


<style lang="stylus" scope>
.btn-container {
  width: 480px;
  height: 160px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.btn-group {
  display: flex;
}

.btn {
  margin: 10px;
}
</style>