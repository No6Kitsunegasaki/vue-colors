<template>
  <div class="panel" :class="classObject" :style="style" v-on:click="change" >
    <div>
      bgcolor: {{bgcolor}}
      color index: {{panel.color}}
    </div>
  </div>
</template>

<script>
export default {
  name: "Panel",
  data() {
    return {
      list: [
        "color-red",
        "color-orange",
        "color-yellow",
        "color-green",
        "color-blue",
        "color-navy",
        "color-purple"
      ]
    };
  },
  props: ["panel"],
  methods: {
    change: function(event) {
      this.panel.color++;
      if (this.panel.color >= this.list.length) {
        this.panel.color = 0;
      }
    }
  },
  computed: {
    classObject: function() {
      let obj = {};
      obj[this.list[this.panel.color]] = true;
      return obj;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.panel {
  height: 100px;
  width: 100px;
  flex-basis: 100px;
}
.color-red {
  background-color: #c93a40;
}
.color-orange {
  background-color: orange;
}
.color-yellow {
  background-color: yellow;
}
.color-green {
  background-color: green;
}
.color-blue {
  background-color: blue;
}
.color-navy {
  background-color: navy;
}
.color-purple {
  background-color: purple;
}
</style>
