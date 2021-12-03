<template>
  <div>
    <p>{{ num }}</p>
    <p>{{ double }}</p>
    <button @click.prevent="increment">add one</button>
    <p>{{ name + ' ' + lastName }}</p>
    <input type="text" v-model="phrase">
    <p>{{ inversePhrase }}</p>
    <Alert :user="user"/>

  </div>
</template>

<script>
import {ref, reactive, toRefs, watch, computed, onBeforeMount, onMounted,} from 'vue';
import Alert from '@/components/Alert';
export default {
  name: 'App',
  components:{Alert},
  setup() {
    onBeforeMount(() => {
      console.log('on before mount');
    });
    onMounted(() => {
      console.log('on mounted')
    })
    let num = ref(0);

    function increment() {
      num.value++
    }

    const user = reactive({
      name: 'shahrokh',
      lastName: 'is'
    });

    const double = computed(() => {
      return num.value ** 2;
    });

    setTimeout(() => {
      user.lastName = 'is not'
    }, 1000);

    const phrase = ref("");
    const inversePhrase = ref("");

    watch(() => {
      inversePhrase.value = phrase.value.split("").reverse().join("");
    })


    return {num, increment, ...toRefs(user), phrase, inversePhrase, double, user};
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
