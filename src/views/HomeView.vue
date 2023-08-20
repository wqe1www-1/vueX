<style scoped>
li {
  list-style: none;
}
a {
  text-decoration: none;
}
.left {
  position: relative;
  width: 70%;

  box-shadow: 0px 2px 10px rgba(0, 0, 0, 0.5);
  margin: auto;
  border-radius: 10px;
}
p {
  font-size: 14px;
  font-weight: bold;
  color: #2e81d3;
  margin-bottom: 10px;
}
.box {
  width: 80px;
  height: 50px;
  background: #2e81d3;
  border-radius: 10px;
  text-align: center;
  margin: 20% auto;
}
</style>
<template>
  <div class="home">
    <div>
      <div class="box" @click="addBtn">
        <div>
          <img src="https://files.codelife.cc/icons/todo.svg" alt="" id="loge" />
        </div>
        <p>待办事务项</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeView',
  components: {},
  methods: {
    addBtn() {
      this.$router.push({ name: 'HelloWorld' })
    }
  }
}
</script>
