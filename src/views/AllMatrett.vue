<template>
  <div>
    <h1>All Matretter</h1>
    <MatrettList />
  </div>
</template>

<script>
import MatrettList from "@/components/MatrettList";
export default {
  name: "AllMatrett",
  components: {
    MatrettList
  }
};
</script>