<template>
    <div>
        <table>
            <tr>
                <td v-for="tab in  Object.keys(tabs)" :key="tab">
                    <HeaderButton v-bind:text="tab" v-on:switch-to="buttonClicked" :key="newtab"/>
                </td>
            </tr>
        </table>
    </div>
</template>

<script>
import HeaderButton from './HeaderButton.vue'

export default {

  name: 'Header',
  components: {
    HeaderButton
  },
  props : {
    tabs : Object
  },
  methods : {
    buttonClicked(newtab) {
      this.$emit('switch-to', this.tabs[newtab]);
    }
  }
}

</script>