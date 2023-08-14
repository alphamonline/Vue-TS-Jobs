<template>
  <div class="app">
    hello vue-ts jobs {{ name }} - {{ age }}
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs, ref } from 'vue';

export default defineComponent({
  name: 'App',
  components: {},
  setup() {

    //Using reactivity
    // const state = reactive({
    //   name: 'Alpha',
    //   age: 27 as number | number //:use type assertion
    // })

    // return { ...toRefs(state) }

    //Using ref 
    const name = ref('Alpha')
    const age = ref<number | string>(27) //: use generic arguments

    name.value = 'Alpha'
    age.value = 27

    return {
      name,
      age
    }
  },
});
</script>

<style>

</style>
