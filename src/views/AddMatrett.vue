<template>
  <div>
    <h1>Legg til nytt matrett!</h1>
    <MatrettForm />
  </div>
</template>

<script>
import MatrettForm from "@/components/MatrettForm";
export default {
  name: "AddMatrett",
  components: {
    MatrettForm
  }
};
</script>

