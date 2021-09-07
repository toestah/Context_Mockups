<template>
  <div class="card">
    <div class="card__details">
      <div class="name">{{name}}</div>
      <p class="desc2">Template: {{template}}</p>
      <p class="description">{{description}}</p>
      <hr>
      <p class="desc">File Types:  <span v-for="type in fileTypes" :key="type.id"> [{{type}}] </span> </p>
      <p class="desc">Top Insights: </p>

      <div class="columns">
        <div class="column piece">
          <i class="fas fa-user-circle icon"></i> <span class="widget"> {{numUsers}}</span>
          <br>
          <span class="define">Users</span>
        </div>
        <div class="column piece">

          <i class="far fa-file-alt icon"></i> <span class="widget"> {{numFiles}}</span>
          <br>
          <span class="define">Files</span>
        </div>
        <div class="column piece">
          <i class="fab fa-searchengin icon"></i> <span class="widget"> {{numInsights}}</span>
          <br>
          <span class="define">Insights</span>
        </div>
      </div>

      <!-- <button>Read more</button> -->
      <hr />
      <p class="desc2">
        Tags:
        <span v-for="tag in tags" :key="tag.index" class="tag is-info"> {{tag}} </span>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name:"Card",
  props: {
    name: String,
    template: String,
    description: String,
    fileTypes: Array,
    tags: Array,
    numUsers: Number,
    numFiles: Number,
    numInsights: Number
  }
};
</script>


<style scoped>
img {
  width: 100%;
  border-radius: 6px;
  height: 214px;

  object-fit: cover;
}

body {
  background-color: #eaeff1;
  font-family: "Raleway", sans-serif;
  margin: 0;
  padding: 0;
}

.widget {
  font-size: 22px;
}

.icon {
  font-size: 22px;
}

.define {
  font-size: 14px;
  color: #7f8c9b;
}

.container {
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.card {
  background-color: #ffffff;
  padding: 2px;
  border-radius: 8px;

  border: solid 1px #bacdd8;
  align-items: left;
  justify-content: left;
  margin: 8px;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 3px;
}

.card:hover {
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 3px;
  filter: brightness(98%);
  cursor: pointer;
  transform: scale(1.01);
}

.piece {
  /* background-color:red;
    border: solid black 1px; */
  margin-top: 25px;
}

.card__details {
  padding: 8px 8px 8px 8px;
}

.tag {
  padding: 8px 8px;
  margin-left: 2px;
  margin-top: 4px;
  border: solid 1px #e5eaed;
  border-radius: 6px;

  font-size: 10px;
  font-weight: 600;

  color: #788697;
  cursor: pointer;
}

.name {
  font-size: 20px;
  font-weight: 600;
  text-align: left;
}

hr {
  margin-top: 6px;
  margin-bottom: 6px;
}

.desc {
  font-size: 12px;
  text-align: left;
}

.description {
  font-size: 12px;
  text-align: left;
  height: 3em;
}

.desc2 {
  margin-top: 0px;
  text-align: left;
}

/* p {
  font-size: 10px;
  color: #7f8c9b;
  line-height: 150%;
  margin-top: 2px;
  margin-bottom: 8px;
  text-align: left;
} */

button {
  border: none;
  padding: 12px 24px;
  border-radius: 8px;
  font-weight: 600;
  color: #0077ff;
  background-color: #e0efff;
  display: block;
  margin: 0 auto;
  outline: none;

  transition: all 200ms ease-in-out;

  cursor: pointer;
}

button:hover,
button:hover {
  background-color: #0077ff;
  color: #e0efff;
}
</style>