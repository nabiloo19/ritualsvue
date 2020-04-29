<template>
  <div>
    <h1>Redigere matrett</h1>
    <label>Id</label>
    <input v-model="editId" type="text" />
    <input @click="getWord" type="button" value="Hent matrett" />
    <hr />
    <input v-model="editMatrett.english" type="text" />
    <input @click="putMatrett" type="button" value="Lagre matrett" />
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "EditMatrett",
  data() {
    return {
      editId: "",
      editMatrett: {}
    };
  },
  methods: {
    getMatrett() {
      let webAPIUrl = `https://localhost:5001/ritualsadmin/${this.editId}`;
      axios.get(webAPIUrl).then(result => {
        this.editMatrett = result.data;
      });
    },
    putMatrett() {
      let webAPIUrl = "https://localhost:5001/ritualsadmin";
      axios.put(webAPIUrl, this.editMatrett);
    }
  }
};
</script>

