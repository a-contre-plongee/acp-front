<template>
  <div>
    <v-btn @click="opened = !opened" fab flat>
      <v-icon class="flex" v-if="opened">close</v-icon>
      <v-icon class="flex" v-else>edit</v-icon>
    </v-btn>
    <v-speed-dial v-model="opened" direction="left">
      <v-btn fab color="green" small @click="add=true">
        <v-icon class="flex">add</v-icon>
      </v-btn>
      <v-btn fab color="blue" small @click="edit=true">
        <v-icon class="flex">edit</v-icon>
      </v-btn>
      <v-btn fab color="red" small @click="del=true">
        <v-icon class="flex">delete</v-icon>
      </v-btn>
    </v-speed-dial>
    <ptz-add-position :device="device" :open="add" @close="add=false"/>
    <ptz-edit-position :device="device" :open="edit" @close="edit=false"/>
    <ptz-delete-position :device="device" :open="del" @close="del=false"/>
  </div>
</template>

<script>
export default {
  props: {
    device: Object,
  },
  data() {
    return {
      add: false,
      edit: false,
      del: false,
      opened: false
    }
  }
}
</script>

<style scoped>
.flex {
  display: flex;
}

</style>
