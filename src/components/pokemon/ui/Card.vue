<template>
  <div>
    <h2>
      {{ name }}
    </h2>
    <div>
      {{details}}
    </div>
  </div>
</template>

<script setup >
  import { ref, onMounted } from 'vue';

  const props = defineProps(['pokemon']);
  const {name, url } = props.pokemon
  const details = ref({})

  onMounted( async () => {
    const response = await fetch(url);
    details.value = await response.json();
  })


</script>

<style>

</style>