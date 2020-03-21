<template>
  <div>
    <table>
      <tr>
        <th>name</th>
        <th>surname</th>
        <th>phone</th>
        <th>email</th>
        <th></th>
      </tr>
      <TableString
        v-for="string of strings"
        :key="string.id"
        v-bind:parrent="parrent"
        v-bind:string="string"
        @remove-string="removeString"
      />
    </table>
  </div>
</template>

<script>
import TableString from "@/components/TableString";
export default {
  props: ["strings", "parrent"],
  components: {
    TableString
  },
  data() {
    return {
      rows: this.strings
    };
  },
  methods: {
    removeString(id) {
      this.$emit("remove-string", id);
    }
  },
  created: function() {
    this.rows = JSON.parse(localStorage.getItem("users")) || [];
  }
};
</script>
<style scoped>
table {
  margin: auto;
  width: 90%;
  background: white;
  color: white;
  border-spacing: 1px;
}

th {
  background: maroon;
  padding: 5px;
  text-transform: uppercase;
}
</style>