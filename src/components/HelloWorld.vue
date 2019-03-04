<template>
  <div class="hello">
    <div>
      <button @click="bone">天降骨头</button>
      <button @click="cat">小猫来了</button>
      <button>找路</button>
    </div>
    <div
      v-for="item in list"
      :key="item"
      :ref="item"
      class="square"
      @click="getPoint(item)"
    >{{item}}</div>
  </div>
</template>
<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      list: []
    };
  },
  methods: {
    river() {
      for (let i = 0; i < 300; i++) {
        this.$refs[
          Math.floor(Math.random() * this.list.length)
        ][0].style.backgroundColor = "brown";
      }
    },
    bone() {
      let p = Math.floor(Math.random() * this.list.length);
      this.$refs[p][0].textContent = "肉";
      this.$refs[p][0].style.borderRadius = "50%";
      this.$refs[p][0].style.backgroundColor = "yellow";
       this.$refs[p][0].style.textAlign= "center";
    },
    cat() {
      let p = Math.floor(Math.random() * this.list.length);
      this.$refs[p][0].textContent = "猫";
      this.$refs[p][0].style.borderRadius = "50%";
      this.$refs[p][0].style.backgroundColor = "red";
      this.$refs[p][0].style.textAlign= "center";
    },
    getPoint(item) {
      // todo 解决边界问题
    
      // 获取隔壁方块的值
      console.log('left',(item-1));
      console.log('right',(item+1));
      console.log('top',(item-30));
      console.log('bottom',(item+30));
    }
  },
  created() {
    for (let i = 0; i < 900; i++) {
      this.list.push(i);
    }
  },
  mounted() {
    this.river();
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello{
  width:600px;
  height:600px;

}
.square {
  background-color: #f7f7fe;
  height: 20px;
  width: 20px;
  float: left;
  font-size: 0.1px;
}
</style>
