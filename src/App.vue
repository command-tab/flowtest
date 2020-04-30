<template>
  <div id="app">
    <div ref="dropzone" id="dropzone">Click or drop to select a file</div>
  </div>
</template>

<script>
import Flow from '@flowjs/flow.js'

export default {
  name: 'App',
  data () {
    return {
      flow: {
        files: []
      }
    }
  },
  mounted () {
    this.flow = new Flow({
      target: '/someapi/upload'
    })

    this.flow.assignDrop(this.$refs.dropzone)
    this.flow.assignBrowse(this.$refs.dropzone)

    this.flow.on('fileAdded', (flowFile, event) => {
      console.log('fileAdded', flowFile, event)
    })
  }
}
</script>

<style scoped>
#dropzone {
  border: 2px dashed gray;
  text-align: center;
  margin: 20px;
  padding: 50px;
}
</style>
