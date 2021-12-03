<template>
<div v-show="flag" class="flag">
  Name changed
</div>
</template>

<script>
import {computed} from "vue";

export default {
  name: "Alert",
  props:['user'],
  setup(props){

    const flag = computed(()=>{
      return props.user.lastName === 'is not';
    })

    return{flag};
  }
}
</script>

<style scoped>

.flag{
  color: red;
}

</style>