<template>
  <div class="card">
    <div class="card-image">
    </div>
    <div class="card-content">
      <div class="media">
        <!-- <div class="media-left">
          <figure class="image is-48x48">
            <img
              src="https://picsum.photos/300"
              alt="Placeholder image"
            />
          </figure>
        </div> -->
        <div class="media-content">
          <p class="title is-4">{{project.name}}</p>
          <p class="subtitle is-6">Template: {{project.template}}</p>
          <p class="subtitle is-12">
              <span class=>{{project.filetypes}} </span>
            </p>
        </div>
      </div>

      <div class="content">
        {{project.description}} 
        <br />
        
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
      project: Object
  }
};
</script>