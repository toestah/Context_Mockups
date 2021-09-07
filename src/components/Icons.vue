<template>
  <div class="columns is-multiline">
    <div class="column is-3" :key="icon.id" v-for="icon in icons">
      <Icon
        @delete-icon="$emit('delete-icon',icon.id)"
        :icon="icon.fa_label"
        :text="icon.text"
        :href="icon.url"
        :animation="animation"
        :animatable="true"
        :color="icon.color"
      />
    </div>
  </div>
</template>

<script>
import Icon from "./Icon";

export default {
  name: "Icons",
  components: {
    Icon,
  },
  props: {
    icons: Array,
  },
};
</script>