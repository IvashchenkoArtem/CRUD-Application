<template>
  <div>
    <router-link to="/edit">
      <a>Add user</a>
    </router-link>

    <Table parrent="home" v-bind:strings="strings" @remove-string="removeString" />
  </div>
</template>

<script>
import Table from "@/components/Table";
import AddString from "@/components/AddString";
export default {
  name: "App",
  data() {
    return {
      strings: []
    };
  },

  methods: {
    removeString(id) {
      this.strings = this.strings.filter(t => t.id !== id);
      localStorage.setItem("users", JSON.stringify(this.strings));
    },
    addString(string) {
      this.strings.push(string);
    }
  },
  components: {
    Table,
    AddString
  },
  created: function() {
    this.strings = JSON.parse(localStorage.getItem("users")) || [];
  }
};
</script>

<style  scoped>
a {
  display: block;
  width: 80px;
  height: 30px;
  line-height: 30px;
  background: green;
  border-radius: 2px;
  text-decoration: none;
  color: black;
  margin: 5px auto;
}
</style>

