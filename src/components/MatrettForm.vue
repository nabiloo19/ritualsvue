<template>
  <div>
    <v-row>
      <v-col cols="12" sm="6" lg="4" class="mx-auto">
        <v-text-field v-model="newMatrett.name" label="Navn"></v-text-field>
        <v-file-input v-model="file" show-size></v-file-input>
        <v-btn @click="postMatrett">Lagre nytt matrett</v-btn>
      </v-col>
    </v-row>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "MatrettForm",
  data() {
    return {
      newMatrett: { name: "", imageSrc: "" },
      file: null
    };
  },
  methods: {
    postMatrett() {
      this.newMatrett.imageSrc = this.file.name;

      let data = new FormData();
      data.append("file", this.file);

      axios
        .post("https://localhost:5001/ritualsadmin", this.newMatrett)
        .then(result => {
          console.log(result.data);

          axios({
            method: "POST",
            url: "https://localhost:5001/ritualsadmin/UploadImage",
            data: data,
            config: { headers: { "Content-Type": "multipart/form-data" } }
          });
        });
    }
  }
};
</script>