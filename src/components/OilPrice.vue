<template>
  <h1>Oil Price</h1>
  <div id="app">
    <form v-on:submit.prevent="addItem">
      <label class="date">日期
        <input type="date" v-model="newItem.date" name="date">
      </label>
      <label class="oil_98">98價格
        <input type="text" v-model="newItem.oil_98" name="oil_98">
      </label>
      <label class="oil_95">95價格
        <input type="text" v-model="newItem.oil_95" name="oil_95">
      </label>
      <label class="oil_92">92價格
        <input type="text" v-model="newItem.oil_92" name="oil_92">
      </label>
      <label class="oil_high">柴油價格
        <input type="text" v-model="newItem.oil_high" name="oil_high">
      </label>

      <button type="submit">Submit</button>
    </form>
    <button class="bt2" @click="handleClick">顯示資料</button>
  </div>

  <div>
    <table>
      <thead>
      <tr>
        <th>date</th>
        <th>oil_98</th>
        <th>oil_95</th>
        <th>oil_92</th>
        <th>oil_high</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="item in data" :key="item.id">
        <td>{{ item.date}}</td>
        <td>{{ item.oil_98}}</td>
        <td>{{ item.oil_95}}</td>
        <td>{{ item.oil_92}}</td>
        <td>{{ item.oil_high}}</td>
      </tr>
      </tbody>
    </table>
  </div>


</template>

<script>
  export default {

    data() {
      return {
        data: [],
        newItem: {
          date: '',
          oil_98: '',
          oil_95: '',
          oil_92: '',
          oil_high: ''
        },
      };
    },
    methods: {
      async addItem() {
        let item =  {
          date: this.newItem.date,
          oil_98: this.newItem.oil_98,
          oil_95: this.newItem.oil_95,
          oil_92: this.newItem.oil_92,
          oil_high: this.newItem.oil_high
        }
        this.data.push(item);
        this.newItem.date = null;
        this.newItem.oil_98 = null;
        this.newItem.oil_95 = null;
        this.newItem.oil_92 = null;
        this.newItem.oil_high = null;
      },

    }
  };

</script>

<style scoped>


body {
  padding: 50px;
  font: 14px "Lucida Grande", Helvetica, Arial, sans-serif;
  background-color: aliceblue;
  display: flex;
  flex-direction: column;
  align-items: center;
}

form {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 20px;
}

label {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 10px;
  font-size: 20px;
}

h1 {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 10px;
  font-size: 20px;
}

input {
  height: 25px;
}

button[type="submit"] {
  color: black;
  padding: 20px 20px;
  text-align: center;
  text-decoration: none;
  font-size: 22px;
  transition-duration: 0.4s;
  cursor: pointer;
  justify-content: center;
  margin-top: 10px;
  background-color: darkgray;
  border: 2px solid black;
}

button:hover {
  background-color: #ffd700;
  color: white;
}

.bt2 {
  margin-bottom: 50px;
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20px;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  padding: 8px;
  text-align: left;
  border-bottom: 3px solid #ddd;
}

th {
  background-color: gray;
}

tbody tr:last-child td {
  border-bottom: none;
}

#log {
  margin-top: 20px;
}


</style>
