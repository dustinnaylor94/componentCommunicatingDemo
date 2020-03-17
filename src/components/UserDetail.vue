<template>
  <div class="component">
    <h3>You may view the User Details here</h3>
    <p>Many Details</p>
    <p>{{switchName()}}</p>
    <p>User Age: {{userAge}}</p>
    <button @click="resetName">Reset Name </button>
    <button @click="resetNewName">Reset Name Parent </button>
  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  props: {
    newName: {
      type: String,
      required: true,
      default: 'Emma'
    },
    resetNewName: Function,
    userAge: Number
  },
  methods: {
    switchName () {
      return this.newName.split("").reverse().join("")
    },
    resetName() {
      this.newName = 'Cody'
      this.$emit('nameWasReset', this.newName)
    }
  },
  created () {
    eventBus.$on('ageWasEdited', (age) => {
      this.userAge = age
    })
  }
}
</script>

<style scoped>
div {
  background-color: lightcoral;
}
</style>
