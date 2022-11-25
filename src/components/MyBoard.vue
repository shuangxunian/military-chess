<template>
  <div class="board-main">
    <div class="board-body">
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
      <div class="board"></div>
      <div class="log"></div>
    </div>

    <!-- 111 -->
  </div>
</template>

<script>
export default {

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
      background-color: green;
    }
    .log {
      width: 150px;
      background-color: blue;
    }
  }
}
</style>
