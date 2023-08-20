<style scoped>
.hello {
  position: relative;
  width: 70%;
  height: 670px;
  margin: 100px auto;
  box-shadow: 0px 2px 10px rgba(0, 0, 0, 0.5);

  border-radius: 10px;
}
.data {
  width: 98%;
  height: 90vh;
  margin: 0;
}
</style>
<template>
  <div :class="tmp ? 'hello' : 'data'">
    <LeftList />
    <AboutView />
    <buttonS />
    <div style="width: 104%; float: left">
      <el-progress :percentage="100" :format="format"></el-progress>
    </div>
  </div>
</template>

<script>
import buttonS from '../components/five.vue'
import AboutView from '../views/AboutView.vue'
import LeftList from './three.vue'
export default {
  name: 'HelloWorld',
  data() {
    return {
      tmp: 2
    }
  },
  components: {
    LeftList,
    AboutView,
    buttonS
  },
  props: {
    msg: String
  },
  methods: {
    data(data) {
      this.tmp = data
    }
  },
  mounted() {
    this.$bus.$on('Data', this.data)
  }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
