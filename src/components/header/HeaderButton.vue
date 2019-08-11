<template>
  <input type="button" v-bind:value="text" @click="$emit('switch-to', text)" />
</template>

<script>
export default {
    name: 'HeaderButton',
    props: { 
      text : Number
    }
}
</script>