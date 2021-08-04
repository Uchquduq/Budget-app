<template>
  <div class="container budget-list">
    <div class="title">
      <h3>{{ header }}</h3>
    </div>
    <template v-if="!isEmpty">
      <thead>
        <tr>
          <th style="padding-left: 15px;text-align: start;">Comment</th>
          <th>Value</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, prop) in list"
        :key="prop">
        <td>{{item.comment}}</td>
        <td>{{item.value}}</td>
        <button @click="deleteItem(item.id)">Delete</button>
        </tr>
      </tbody>
    </template>

    <template v-else>
      <div>
        <div style="text-align: center;background: red; border-radius: 5px; padding: 10px; color: white;  font-weight: 600;">Elementlar yo'q</div>
      </div>
    </template>
  </div>
</template> 

<script>
export default {
  name: "BudgetList",
  props: {
    list: {
      type: Object,
      default: () => ({}),
    },
  },
  data: () => ({
    header: "Budget List",
  }),
  methods: {
    deleteItem(id) {
      this.$emit("deleteItem", id)
    }
  },
  computed: {
    isEmpty() {
      return !Object.keys(this.list).length;
    },
  },
};
</script>

<style scoped>
div {
  font-family: Helvetica;
}

h3 {
  text-align: center;
  font-weight: 600;
  margin-bottom: 20px;
}

button {
  margin: auto;
  background: rgb(250, 49, 49);
  padding: 5px 10px;
  border-radius: 5px;
  color: white;
  font-weight: 600;
  margin-top: 10px;
}

thead {
  margin: 10px;
}

td {
  padding: 15px;
  margin-left: 10px;
}

.budget-list {
  width: 400px;
  max-width: 400px;
  border-radius: 10px;
  margin: 5px;
  padding: 15px 10px;
  font-family: Helvetica;
  background-color: rgb(242, 242, 242);
}
</style>
