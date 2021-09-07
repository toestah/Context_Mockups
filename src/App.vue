<template>
  <div>
    <!-- <Navbar /> -->
    <div class="topbar">
      <img
        class="logo"
        src="https://context-2my7afm7yq-ue.a.run.app/src/assets/logo/logo_white.png"
      />
    </div>
    <div class="container is-fluid">
      <!-- 
      <div class="tabs">
        <ul>
          <li class="is-active"><a>My Projects</a></li>
          <li><a>Shared Projects</a></li>
        </ul>
      </div> -->

      <Search />
      <h1 class="title is-4 has-text-left">My Projects</h1>
      <div class="columns is-multiline is-gapless">
        <div
          :key="project.index"
          v-for="project in myProjects"
          class="column is-3"
        >
          <Card3
            :name="project.name"
            :template="project.template"
            :description="project.description"
            :fileTypes="project.filetypes"
            :numUsers="project.users.length"
            :numFiles="project.numfiles"
            :numInsights="project.numinsights"
            :tags="project.tags"
          />
        </div>
      </div>
      <h1 class="title is-4 has-text-left">Shared With Me</h1>
      <div class="columns is-multiline is-gapless">
        <!-- <div :key="project.id" v-for="project in projects" class="column is-3">
              <Card :project="project" />
            </div> -->
        <!-- <div :key="project.id" v-for="project in projects" class="column is-6">
            <Card2 :project="project" />
          </div> -->

        <div
          :key="project.index"
          v-for="project in sharedProjects"
          class="column is-3"
        >
          <Card3
            :name="project.name"
            :template="project.template"
            :description="project.description"
            :fileTypes="project.filetypes"
            :numUsers="project.users.length"
            :numFiles="project.numfiles"
            :numInsights="project.numinsights"
            :tags="project.tags"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import Navbar from "./components/Navbar";
import Card3 from "./components/Card3";
import Search from "./components/Search";

// import Media from "./components/Media"

export default {
  name: "App",
  components: {
    // Navbar,
    Card3,
    Search,
    // Media
  },
  data() {
    return {
      icons: [],
      activeModal: false,
      animation: "animate__animated animate__pulse",
      icons_picklist: [],
      active_icon_text: "fas fa-address-card",
      myProjects: [],
      sharedProjects: [],
    };
  },
  methods: {
    alert(message) {
      window.alert(message);
    },
    async deleteIcon(id) {
      if (confirm("Are you sure?")) {
        const res = await fetch(`api/icons/${id}`, {
          method: "DELETE",
        });

        res.status === 200
          ? (this.icons = this.icons.filter((icon) => icon.id !== id))
          : alert("Error deleting icon");
      }
    },
    animate(el) {
      // window.alert(el.toString())
      console.log(el);
    },
    async addIcon(icon) {
      const res = await fetch("api/icons", {
        method: "POST",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(icon),
      });

      const data = await res.json();

      this.icons = [...this.icons, data];
    },
    async fetchIcons() {
      const res = await fetch("api/icons");
      const data = await res.json();
      return data;
    },
    async fetchMyProjects() {
      const res = await fetch("api/myProjects");
      const data = await res.json();
      return data;
    },
    async fetchSharedProjects() {
      const res = await fetch("api/sharedProjects");
      const data = await res.json();
      return data;
    },
    async fetchIconsPicklist() {
      const res = await fetch("api/icons_picklist");
      const data = await res.json();

      return data;
    },
    cancelModal() {
      this.activeModal = false;
    },
    activateIcon(icon) {
      this.active_icon_text = icon;
    },
    openModal() {
      this.activeModal = true;
    },
  },
  async created() {
    this.myProjects = await this.fetchMyProjects();
    this.sharedProjects = await this.fetchSharedProjects();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0px;
}

i {
  font-size: 2em;
}

.default_cursor {
  cursor: default !important;
}

.spacer {
  height: 30px;
}

.topbar {
  background-color: #0080f7;
  margin-bottom: 20px;
  text-align: left;
}

.logo {
  margin: 6px;
  height: 30px;
  cursor: pointer;
}
</style>
