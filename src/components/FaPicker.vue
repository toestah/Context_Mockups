<template>
<div :class="[active ? 'is-active' : '', 'modal']">
  <div class="modal-background"></div>
  <div class="modal-card">
    <header class="modal-card-head">
      <p class="modal-card-title">Pick an Icon</p>
      <button @click="cancel()" class="delete" aria-label="close"></button>
    </header>
    <section class="modal-card-body">
      <!-- Content ... -->
      <div class="columns is-centered is-multiline">
          <div @click="makeActive(icon)" :class="['grow','column', 'is-2', 'highlighted']" :key="icon.key" v-for="icon in icons">
              <i :class="icon"> </i>
          </div>
      </div>
    </section>
    <footer class="modal-card-foot">
      <!-- <button class="button is-success">Save changes</button> -->
      <!-- <button class="button" @click="cancel()">Return</button> -->
    </footer>
  </div>
</div>
</template>

<script>
export default {
    name: "FaPicker",
    props: {
        active: Boolean,
        icons: Array
    },
    data(){
    },
    methods: {
        cancel(){
            this.$emit("cancel-modal")
        },
        makeActive(icon){
            this.$emit('active-icon',icon)
            this.$emit("cancel-modal")
        }
    }
};
</script>

<style scoped>
    .grow { min-height:75%; transition: all .08s ease-in-out; color: black}
    /* .grow:hover {  cursor: pointer; filter:brightness(90%); filter: drop-shadow(2px 2px 2px rgb(0 0 0 / 0.4)); color: darkgreen; border: ridge green 2px; box-sizing: border-box; -moz-box-sizing: border-box; -webkit-box-sizing: border-box;}  */
    .grow:hover {        
        padding: 1px 0px 0px 0px;
        transform: scale(1.05);
        cursor: pointer;
        filter:drop-shadow(2px 1px 1px rgb(0 0 0 / 0.4));
    }
</style>
