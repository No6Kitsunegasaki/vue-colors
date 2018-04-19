<template>
  <div class="board" :style=style>
    <panel v-for="(panel, key) in panels" :panel="panel" :key="key"/>
  </div>
</template>

<script>
import Panel from "./Panel";
export default {
  components: {
    Panel
  },
  name: "Board",
  props: ["rows", "columns"],
  data() {
    return {
      panels: [],
      style: { width: 0, height: 0 },
      panelStyle: { width: 100, height: 100 }
    };
  },
  created: function() {
    const panelCount = this.rows * this.columns;
    this.style.width = this.columns * this.panelStyle.width + "px";
    this.style.height = this.rows * this.panelStyle.height + "px";
    for (let i = 0; i < panelCount; i++) {
      this.panels.push({ color: 0, style: this.panelStyle });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.board {
  border: 1px solid #000000;
  display: flex;
  flex-wrap: wrap;
  margin: auto;
  padding: auto;
}
</style>
