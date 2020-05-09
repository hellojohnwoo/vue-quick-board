<template>
  <div>
    <table>
      <tr>
        <td>writer</td>
        <td>title</td>
        <td>content</td>
      </tr>
      <tr :key="index" v-for="(value, index) in data">
        <td>{{value.writer}}</td>
        <td>{{value.title}}</td>
        <td>{{value.content}}</td>
      </tr> 
    </table>
    <button @click="write">write</button>
  </div>
</template>
<script>
import data from '@/data'

export default {
  name : 'Read',
  data() {
    return {
      data : data
    }
  },
  methods : {
    write() {
      this.$router.push({
        path : 'create'
      })
    }
  }
}
</script>