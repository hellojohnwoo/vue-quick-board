<template>
  <div>
    <input v-model="writer" placeholder="writer"/>
    <input v-model="title" placeholder="title"/>
    <textarea v-model="content" placeholder="content"/>
    <button @click="index !== undefined ? update() : write()">{{index !== undefined ? 'update' : 'write'}}</button>
  </div>
</template>
<script>
import data from '@/data'
export default {
  name : 'Create',
  data() {
    const index = this.$route.params.contentId;
    return {
      data : data,
      index : index,
      writer : index !== undefined ? data[index].writer : "",
      title : index !== undefined ? data[index].title : "",
      content : index !== undefined ? data[index].content : ""
    }
  },
  methods : {
    write() {
      this.data.push({
        writer : this.writer,
        title : this.title,
        content : this.content,
      })
      this.$router.push({
        path : '/'
      })
    },
    update() {
      data[this.index].writer = this.writer
      data[this.index].title = this.title
      data[this.index].content = this.content
      this.$router.push({
        path: '/'
      })
    }
  }
}
</script>