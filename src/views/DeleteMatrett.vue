<template>
  <div>
    <h1>Slett matretter</h1>
    <label>Id</label>
    <input v-model="deleteId" type="text" />
    <input @click="deleteMatrett" type="button" value="Slett matrett" />
    <p>{{ deleteStatus }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "DeleteMatrett",
  data() {
    return {
      deleteId: null,
      deleteStatus: "Ingenting er slettet enda"
    };
  },
  methods: {
    deleteMatrett() {
      let webAPIUrl = `https://localhost:5001/ritualsadmin/${this.deleteId}`;

      axios.delete(webAPIUrl).then(result => {
        this.deleteStatus = JSON.stringify(result.data);
      });
    }
  }
};
</script>