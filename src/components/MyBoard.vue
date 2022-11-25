<template>
  <div class="board-main">
    <div class="board-body">
      <!-- 左侧用户信息与开始 -->
      <div class="user">
        <div class="user-avatar">
          <img class="circle-img" src="../assets/img/saucg.png"  />
          <el-button>选择</el-button>
        </div>
        <el-button>开始</el-button>
        <div class="user-avatar">
          <img class="circle-img" src="../assets/img/saucg.png"  />
          <el-button>选择</el-button>
        </div>
      </div>
      <!-- 中间棋盘 -->
      <div class="board">
        <canvas
          id="chess"
          :width="450"
          :height="700"
          :style="{ background: primary }">
        </canvas>
      </div>
      <!-- 右侧行棋log -->
      <div class="log"></div>
    </div>

    <!-- 111 -->
  </div>
</template>

<script>
export default {
  data () {
    return {
      canvas: null, // 画布
      ctx: null,
      primary: '#E4B97F', // 主题色
      height: 500,
      width: 450,
      locationScale: 50, // 一格的物理尺寸
      padding: 25 // 左右边距
    }
  },
  mounted () {
    this.initData()
  },
  methods: {
    // 初始化数据
    initData () {
      const canvas = (this.canvas = document.getElementById('chess'))
      this.ctx = canvas.getContext('2d')
      // const ctx = (this.ctx = canvas.getContext('2d'))
      this.drawChessContainer()
    },
    // 绘制棋盘
    drawChessContainer () {
      const { ctx } = this
      // 每次绘制棋盘前,先清空画布
      ctx.rect(0, 0, this.width, this.height)
      // 设置颜色
      ctx.fillStyle = this.primary
      ctx.strokeStyle = '#000'

      // 循环画出来会少一条横线,我们手动加上
      ctx.beginPath()
      ctx.moveTo(this.padding, 475)
      ctx.lineTo(425, 475)
      // 绘制线条
      ctx.stroke()
      for (let index = 1; index <= 9; index++) {
        // 横线
        ctx.beginPath()
        ctx.moveTo(this.padding, index * this.locationScale - this.padding)
        ctx.lineTo(425, index * this.locationScale - this.padding)
        // 绘制线条
        ctx.stroke()

        // 竖线
        ctx.beginPath()
        ctx.moveTo(this.locationScale * index - this.padding, this.padding)
        ctx.lineTo(this.locationScale * index - this.padding, 475)
        // 绘制线条
        ctx.stroke()
      }
    }
  }
}
</script>

<style lang="less" scoped>
.board-main {
  height: 100%;
  // background-color: #999;
  position: relative;
  .board-body {
    width: 800px;
    height: 700px;
    background-color: #ccc;
    position: absolute;
    top:0;
    right: 0;
    bottom: 0;
    left: 0;
    margin: auto;
    display: flex;
    .user {
      width: 200px;
      .user-avatar {
        height: 330px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        .el-button {
          margin: 0 auto;
          width: 50%;
        }
      }
      .el-button {
        width: 100%;
      }
      .circle-img {
        border-radius: 90px;
        width: 180px;
        height: 180px;
        margin: 10px auto;
      }
    }
    .board {
      width: 450px;
    }
    .log {
      width: 150px;
      background-color: blue;
    }
  }
}
</style>
