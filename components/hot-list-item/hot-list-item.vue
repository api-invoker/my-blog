<template>
  <view class="item-container">
    <view class="item-box">
      <view class="item-box-left">
        <hot-ranking :ranking="ranking"></hot-ranking>
      </view>
      <view class="item-box-right">
        <view class="item-title line-clamp-2">{{hotListItem.title}}</view>
        <view class="item-desc line-clamp-2">{{hotListItem.desc}}</view>
        <view class="item-bottom-box">
          <text class="item-author">{{hotListItem.nickname}}</text>
          <view class="hot-box">
            <image class="hot-icon" src="/static/images/hot-icon.png"></image>
            <text class="hot-text">{{ showItemViews }}&nbsp;热度</text>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
  export default {
    name: "hot-list-item",
    props: {
      hotListItem: {
        type: Object,
        required: true,
      },
      ranking: {
        type: Number,
        required: true
      }
    },
    computed: {
      showItemViews() {
        let views = parseInt(this.hotListItem.views)
        if(views < 1000) return views
        views = String(views)
        return views.substring(0, views.length - 3) + 'k'
      }
    },

    data() {
      return {

      };
    },

    methods: {
      
    }
  }
</script>

<style lang="scss" scoped>
  .item-container {
    padding-bottom: $uni-spacing-col-lg;

    .item-box {
      display: flex;
      margin: 0 $uni-spacing-row-base;
      padding: $uni-spacing-row-lg $uni-spacing-row-base;
      background-color: $uni-bg-color;
      border-radius: $uni-border-radius-lg;
      box-shadow: 2px 2px 5px 1px rgba(143, 143, 143, .1);

      .item-box-left {
        margin-right: $uni-spacing-row-sm;
      }

      .item-box-right {
        flex: 1;

        .item-title {
          font-size: $uni-font-size-lg;
          font-weight: 700;
          color: $uni-text-title-color;
        }

        .item-desc {
          padding-top: $uni-spacing-col-sm;
          word-break: break-word;
          font-size: $uni-font-size-base;
          color: $uni-text-color;
        }

        .item-bottom-box {
          display: flex;
          justify-content: space-between;
          align-items: center;
          margin-top: $uni-spacing-col-sm;

          .item-author {
            font-size: $uni-font-size-sm;
            color: $uni-text-color-grey;
          }

          .hot-box {
            .hot-icon {
              width: $uni-img-size-sm;
              height: $uni-img-size-sm;
              vertical-align: top;
            }

            .hot-text {
              margin-left: $uni-spacing-row-sm;
              font-size: $uni-font-size-sm;
              color: $uni-text-color-hot;
            }

          }

        }

      }

    }
  }
</style>
