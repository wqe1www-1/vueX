<style scoped>
* {
  margin: 0;
  padding: 0;
}
.box {
  display: flex;
  width: 100%;
  flex-wrap: wrap;
  /* flex-direction: column; */

  overflow-y: scroll;

  max-height: 55vh;

  z-index: 100;
}
.box1 {
  display: flex;
  width: 100%;
  flex-wrap: wrap;
  /* flex-direction: column; */
  max-height: 75vh;
  overflow-y: scroll;

  z-index: 100;
}
.content {
  height: 50px;
  width: 80%;

  border: 1px solid rgb(233, 228, 228);
  border-radius: 5px;
  margin: auto;
  margin-top: 10px;
  padding: 10px;
}
.content:hover {
  box-shadow: 0px 2px 10px rgba(0, 0, 30, 0.5);
}

.h4 {
  width: 30px;
  height: 30px;
  line-height: 20px;

  text-align: center;
  margin: 20px;
  margin-left: auto;
  background: #e20d0d;
}
.left {
  float: left;
}
.right {
  float: right;
  margin-right: 10px;
}

.button {
  width: 60%;
  height: 7%;
  background: red;
  border-radius: 5px;
  margin: auto;
  margin-top: 10px;

  position: absolute;
  left: 30%;
  bottom: 5%;
}
#int {
  width: 100%;
  height: 100%;
  box-shadow: 0px 2px 10px rgba(180, 180, 184, 0.5);
  padding-left: 30px;
  border: none;
  outline: none;
}
</style>
<template>
  <div :class="tmp ? 'box' : 'box1'">
    <div class="content" v-for="item in arrList" :key="item.id">
      <div class="left">
        <el-checkbox v-model="checked"
          ><span>{{ item.name }}</span></el-checkbox
        >

        <br />
        <div class="block">
          <el-date-picker v-model="item.value" type="date" placeholder="-"> </el-date-picker>
        </div>
      </div>
      <div class="right">
        <h3 style="display: inline-block">...</h3>
        <span style="margin: 10px">
          <el-button @click="del(index)" size="mini" type="danger" icon="el-icon-delete" circle></el-button>
        </span>
      </div>
    </div>

    <div class="button">
      <input type="text" id="int" placeholder="+ 添加任务" v-model="text" @keyup.enter="addText" />
    </div>
  </div>
</template>
<script>
export default {
  name: 'ListS',
  data() {
    return {
      text: '',
      value1: '',
      value2: '',
      arrList: [],
      tmp: true
    }
  },
  mounted() {
    this.$bus.$on('Data', this.dataBtn)
  },
  methods: {
    dataBtn(value) {
      this.tmp = value
    },
    del(index) {
      if (confirm(`确定要删除的吗 `)) {
        this.arrList.splice(index, 1)
      }
    },
    //方法
    addText() {
      let addList = {
        id: this.arrList.length,
        name: this.text,
        status: false,
        value: ''
      }
      this.arrList.push(addList)
    }
  },
  watch: {
    //监听
    op() {}
  },
  computed: {},
  props: {
    msg: String
  }
}
</script>
