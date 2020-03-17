<template>
  <div class="component">
    <h1>The User Component</h1>
    <p>I'm an awesome User!</p>
    <p>{{newName}}</p>
    <p>Age: {{age}}</p>
    <button @click="changeName">Change My Name</button>
    <hr>
    <div class="row">
      <div class="col-xs-12 col-sm-6">
        <app-user-detail 
        :newName="newName" 
        @nameWasReset="newName = $event"
        :resetNewName="resetName"
        :userAge="age"></app-user-detail>
      </div>
      <div class="col-xs-12 col-sm-6">
        <app-user-edit 
        :userAge="age" 
        @ageWasEdited="age=$event">
        </app-user-edit>
      </div>
    </div>
  </div>
</template>

<script>
import UserDetail from './UserDetail.vue';
import UserEdit from './UserEdit.vue';

export default {
  data () {
    return {
      newName: 'Cody',
      age: 100
    }
  },
  methods: {
    changeName () {
      this.newName = 'Emily'
    },
    resetName () {
      this.newName = 'Cody'
    }
  },
  components: {
    appUserDetail: UserDetail,
    appUserEdit: UserEdit
  }
}
</script>

<style>
div {
  background-color: lightblue;
}
</style>
