<template>
  <div>
    <v-row>
      <v-col cols="12" sm="6" lg="4" v-for="matrett in matretter" :key="matrett.id">
        <MatrettItem :id="matrett.id" :name="matrett.name" :imageSrc="matrett.imageSrc" />
      </v-col>
    </v-row>
  </div>
</template>
<script>
import axios from "axios";
import MatrettItem from "@/components/MatrettItem";
export default {
  name: "MatrettList",
  data() {
    return {
      matretter: [
        {
          id: 999,
          name: "TESTFIDO",
          imageSrc: "fido.jpg"
        }
      ]
    };
  },
  created() {
    axios.get("https://localhost:5001/rituals").then(result => {
      this.Matrett = result.data;
    });
  },
  components: {
    MatrettItem
  }
};
</script>
