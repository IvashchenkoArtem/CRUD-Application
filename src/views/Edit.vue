<template>
  <div>
    <router-link to="/">Home</router-link>
    <hr />
    <input v-model="input" type="text" placeholder="Enter 'import JSON' " />
    <button @click="getUsers">Get Users</button>
    <AddString @add-string="addString" />
    <Table parrent="edit" v-bind:strings="strings" @remove-string="removeString" />
  </div>
</template>

<script>
import Table from "@/components/Table";
import AddString from "@/components/AddString";
export default {
  name: "App",
  data() {
    return {
      strings: [],
      input: ""
    };
  },

  methods: {
    removeString(id) {
      this.strings = this.strings.filter(t => t.id !== id);
      localStorage.setItem("users", JSON.stringify(this.strings));
    },
    addString(string) {
      this.strings.unshift(string);
    },
    getUsers() {
      if (this.input === "import JSON") {
        fetch("https://jsonplaceholder.typicode.com/users")
          .then(response => response.json())
          .then(json => {
            json.map(user => this.strings.unshift(user));
            // this.strings = json;
          });
      }
    }
  },
  components: {
    Table,
    AddString
  },
  watch: {
    strings: {
      handler: function() {
        console.log(this.strings);
        localStorage.setItem("users", JSON.stringify(this.strings));
      },
      deep: true
    }
  },
  created: function() {
    this.strings = JSON.parse(localStorage.getItem("users")) || [];
  }
};
</script>