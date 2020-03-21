<template>
  <form @submit.prevent="onSubmit">
    <input type="text" placeholder="Your Name..." v-model="name" />
    <input type="text" placeholder="Your Surname..." v-model="username" />
    <input type="tel" name="tel" placeholder="Your Phone Number..." v-model="phone" />
    <input type="email" placeholder="Your Email..." v-model="email" />
    <button type="submit">Add user</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      username: "",
      phone: "",
      email: ""
    };
  },
  methods: {
    onSubmit() {
      console.log("Submit");
      if (
        (this.name.trim(),
        this.username.trim(),
        this.phone.trim(),
        this.email.trim())
      ) {
        const NewString = {
          id: Date.now(),
          name: this.name,
          username: this.username,
          phone: this.phone,
          email: this.email
        };

        this.$emit("add-string", NewString);
        (this.name = ""),
          (this.username = ""),
          (this.phone = ""),
          (this.email = "");
      }
    }
  }
};
</script>

<style scoped>
form {
  margin: 10px auto;
}

input {
  margin-right: 10px;
}

button {
  border: none;
  background: green;
  border-radius: 2px;
  padding: 5px 10px;
  font-weight: bold;
  cursor: pointer;
}
</style>