<template>
  <div class="container form">
    <div :model="formData" class="form-input">
      <label for="" class="type">Type</label>
      <select v-model="formData.type" class="form-select">
        <option disabled value="">Type</option>
        <option :value="item" v-for="item in items">{{item}}</option>
      </select>
      <label for="Comments" class="comments">Comments </label>
      <input v-model="formData.comment" type="text" placeholder="Text" />
      <label for="Number" class="number">Number </label>
      <input
        v-model.number="formData.value"
        type="number"
        placeholder="Number"
      />
      <button class="mr-4" @click="onSubmit()" color="primary">Submit</button>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    items: ["Income", "Outcome"],
    formData: {
      type: "Income",
      comment: "",
      value: 0,
    },
  }),

  computed: {},

  methods: {
    onSubmit() {
      this.$emit("submitForm", { ...this.formData });
      this.$refs.addItemForm.resetFields();
    },
  },
};
</script>

<style scoped>
.form {
  border-radius: 5px;
}

.type {
  font-weight: 600;
  font-size: 16px;
  margin-bottom: 2px;
}

.form-input {
  display: flex;
  flex-direction: column;
  width: 400px;
  margin: 5px;
  padding: 15px 10px;
  font-family: Helvetica;
  background-color: rgb(242, 242, 242);
  border-radius: 10px;
}

.form-select {
  border: 1px solid black;
}

.comments {
  margin-top: 10px;
  font-size: 16px;
  font-weight: 600;
}

.number {
  margin-top: 10px;
  font-size: 16px;
  font-weight: 600;
}

select {
  width: 100px;
  border-radius: 5px;
  padding: 10xp 15px;
  height: 20px;
}

button {
  margin: auto;
  background: rgb(49, 49, 250);
  padding: 10px 15px;
  border-radius: 5px;
  color: white;
  font-weight: 600;
  margin-top: 10px;
}
</style>