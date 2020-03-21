<template>
  <tr>
    <td>
      {{ string.name }}
      <br />
      <input type="text" v-model.lazy="string.name" v-if="isVisible" />
    </td>
    <td>
      {{ string.username }}
      <br />
      <input type="text" v-model.lazy="string.username" v-if="isVisible" />
    </td>
    <td>
      {{ string.phone }}
      <br />
      <input type="text" v-model.lazy="string.phone" v-if="isVisible" />
    </td>
    <td>
      {{ string.email }}
      <br />
      <input type="text" v-model.lazy="string.email" v-if="isVisible" />
    </td>
    <td>
      <button @click="editBtn()">Edit</button>
      <button @click="$emit('remove-string', string.id)">Delete</button>
    </td>
  </tr>
</template>

<script>
import router from "../router";
export default {
  data: () => {
    return {
      isVisible: false
    };
  },
  props: {
    string: {
      type: Object,
      required: true
    },
    parrent: {
      type: String
    }
  },
  methods: {
    editBtn() {
      console.log(this.isVisible);
      console.log(this.parrent);

      if (this.parrent === "edit") {
        this.isVisible = !this.isVisible;
      } else {
        this.isVisible = false;
        router.push("edit");
      }
      console.log(this.isVisible);
    }
  }
};
</script>

<style scoped>
td {
  background: green;
  padding: 5px;
  color: black;
  height: 100%;
}
td:last-child {
  display: flex;
  justify-content: space-around;
}
button {
  border: none;
  padding: 5px 10px;
  cursor: pointer;
  font-weight: bold;
  border-radius: 2px;
  margin: 10px 0;
}
</style>