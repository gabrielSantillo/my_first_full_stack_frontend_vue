<template>
  <div>
    <insert-candy></insert-candy>
    <display-candys></display-candys>
  </div>
</template>

<script>
import DisplayCandys from "./display-candys/DisplayCandys.vue";
import InsertCandy from "./insert-candy/InsertCandy.vue";
export default {
  components: { DisplayCandys, InsertCandy },
};
</script>

<style scoped></style>
