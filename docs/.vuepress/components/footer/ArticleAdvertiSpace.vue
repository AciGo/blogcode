<template>
  <div>
    <div class="carousel">
      <el-carousel trigger="click" height="150px">
        <el-carousel-item v-for="item in carouses" :key="item.id">
          <a :href="item.href" @click="linkFun" :target="target">
            <img :src="item.imgUrl" :width="width" :height="height" alt />
          </a>
        </el-carousel-item>
      </el-carousel>
    </div>
    <el-dialog
      title="提示"
      :visible.sync="centerDialogVisible"
      closeonclickmodal="false"
      width="30%"
      center
      v-if="isDiaLog"
    >
      <span>如需合作:请您联系站长,添加微信:suibichuanji,期待我们合作愉快</span>
      <span slot="footer" class="dialog-footer">
        <el-button @click="centerDialogVisible = false">取 消</el-button>
        <el-button type="primary" @click="centerDialogVisible = false">确 定</el-button>
      </span>
    </el-dialog>
  </div>
</template>

<script>
export default {
  name: "ArticleAdvertiSpace",
  props: ["width", "height"],
  data() {
    return {
      carouses: [
        {
          imgUrl: "/images/adslo.png",
          text: "广告位招租",
          id: "1",
          href: "javascript:;",
          target: "_blank"
        },

        {
          imgUrl: "/images/adslocation.png",
          text: "广告位招租",
          id: "2",
          href: "/about/adverent",
          target: "_blank"
        }
      ],
      centerDialogVisible: false,
      isDiaLog: true
    };
  },

  methods: {
    linkFun() {
      const isMobile = /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(
        navigator.userAgent
      )
        ? true
        : false;
      if (isMobile) {
        this.isDiaLog = false;
        this.$message({
          message: "如需合作,请您联系站长,期待我们合作愉快",
          type: "error",
          center: true,
          duration: 5000
        });
        return console.log("移动端下不显示dialog");
      } else {
        this.carouses.forEach(item => {
          if (item.href != "javascript:;") {
            item.target = "_blank";
            item.href = item.href;
          } else {
            item.target = "_self";
            this.centerDialogVisible = true;
          }
        });
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.carousel {
  text-align: center;
  margin: 30px;
}
</style>