<template>
  <div class="header">
    <div class="content-wrapper">
      <div class="avatar">
        <img :src="seller.avatar" width="64" height="64" />
      </div>
      <div class="content">
        <div class="title">
          <span class="brand"></span>
          <span class="name">{{ seller.name }}</span>
        </div>
        <div class="description">
          {{ seller.description + " / " + seller.deliveryTime + "分钟送达" }}
        </div>
        <div class="surrports" v-if="seller.supports">
          <div class="supports_desc">
            <span
              class="icon"
              :class="iconClassMap[seller.supports[0].type]"
            ></span>
            <span class="text">{{ seller.supports[0].description }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    seller: {
      type: Object,
    },
  },
  created() {
    this.iconClassMap = [
      "decrease",
      "discount",
      "special",
      "invoice",
      "guarantee",
    ];
  },
};
</script>

<style lang="stylus" scoped>
.header {
  position: relative;
  blur: 10px;
  overflow: hidden;

  .content-wrapper {
    position: relative;
    display: flex;
    padding: 24px 12px 18px 24px;
    font-size: 12px;

    .avatar {
      img {
        border-radius: 10px;
      }
    }

    .content {
      margin-left: 16px;

      .title {
        margin: 2px 0px 8px 0px;
        font-size: 16px;

        .brand {
          display: inline-block;
          vertical-align: top;
          width: 30px;
          height: 18px;
          background-image: url('img/brand@2x.png');
          background-size: 30px 18px;
          background-repeat: no-repeat;
        }

        .name {
          margin-left: 10px;
          font-size: 16px;
          line-height: 18px;
          font-weight: bold;
        }
      }

      .description {
        font-size: 12px;
        margin-bottom: 10px;
      }

      .supports {
        .icon {
          width: 12px;
          height: 12px;

          &.decrease {
            background-image: url('img/decrease_1@2x.png');
          }

          color: blue;
        }
      }
    }
  }
}
</style>