<template>
  <div>
    <form @submit="addIcon">
      <p>
        <i @click="openModal()" :class="[icon_text,'grow']" :style="{color : activeColor}">  </i>
          &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
        <input placeholder="Color" name="color" type="color" v-model="activeColor" />
      </p>
      <br />
      <p>
        <input placeholder="Text" name="text" type="text" v-model="text" />
      </p>
      <br />
      <p>
        <input placeholder="URL" name="url" type="text" v-model="url" />
      </p>
      <br />
      <p>

      </p>
      <br />
      <p>
        <input
          type="Submit"
          value="Add New Tile"
          class="button is-primary"
          @click="addIcon()"
        />
      </p>
    </form>
  </div>
</template>

<script>
export default {
  name: "AddIcon",
  props: {
    icon_text: String
  },
  data(){
    return {
      activeColor: "black"
    }
  },
  methods: {
    addIcon(e) {
      e.preventDefault();
      if (!this.text) {
        alert("Please add an icon");
        return;
      }
      const newIcon = {
        // id: Math.floor(Math.random() * 100000),
        text: this.text,
        color: this.activeColor,
        url: this.url,
        fa_label: this.icon_text,
      };

      this.$emit("add-icon", newIcon);

      this.activeColor = "black";
      this.text = "";
      this.url = "";

    },
    openModal(){
      this.$emit('open-modal')
    }
  },
};
</script>

<style scoped>
    .grow { min-height:75%; transition: all .08s ease-in-out; color: }
    .grow:hover { transform: scale(1.20); cursor: pointer; filter:brightness(90%)}
</style>