<template>
  <div class="search">
      <header>
          <div class="search-header-wrap">
              <div class="wrap-left" @click="back">
                  <i class="iconfont">&#xe637;</i>
              </div>
              <div class="wrap-mid">
                  <div class="search-view">
                      <i class="iconfont">&#xe626;</i>
                      <input type="text" @focus="searchFocus" @blur="searchBlur" v-model="keyword">
                  </div>
              </div>
              <div class="wrap-right">
                    <span>搜索</span>
              </div>
          </div>
      </header>
      <section>
          <div class="search-indicator">
               <category-box :title="computedIndicatorText">
                   <div class="indicator-hot" v-if="!isFocus">
                       <div class="hot-item">
                            <span>小米</span>
                       </div>
                        <div class="hot-item">
                            <span>棉袄</span>
                       </div>
                        <div class="hot-item">
                            <span>笔记本</span>
                       </div>
                        <div class="hot-item">
                            <span>自行车</span>
                       </div>
                        <div class="hot-item">
                            <span>背包</span>
                       </div>
                        <div class="hot-item">
                            <span>零食</span>
                       </div>
                   </div>
                   <div class="indicator-history" v-if="isFocus"></div>
               </category-box>
          </div>
      </section>
  </div>
</template>

<script>
export default {
  data(){
      return{
          isFocus:false,
          isTyping:false,
          keyword:''
      }
  },
  computed:{
      computedIndicatorText(){
          if(this.isFocus){
              if(this.isTyping){
                  return '相关商品';
              }else{
                  return '搜索记录';
              }
          }else{
              return '热搜';
          }
      }
  },
  methods:{
      searchFocus(e){
          this.isFocus = true;
      },
      searchBlur(e){
          this.isFocus = false;
          this.isTyping = false;
      }
  },
  watch:{
      keyword(val){
          this.isTyping = true;
      }
  }
}
</script>


<style lang="less" scoped>
@import '../assets/css/var.less';
.search{
    header{
        position: absolute;
        top:0px;
        left:0px;
        width:100%;
        .search-header-wrap{
            position: relative;
            display: flex;
            height: 52px;
            padding:0px 10px;
            background: white;
            .wrap-left{
                flex-basis: 35px;
                flex-shrink: 0;
                i{
                    line-height: 52px;
                    font-size: 20px;
                }
            }
            .wrap-mid{
                display: flex;
                flex:1;
                align-items: center;
                .search-view{
                    display: flex;
                    flex:1;
                    height: 35px;
                    background: @background-color;
                    border-radius: 35px;
                    i{
                        flex-grow: 0;
                        padding:0px 10px;
                        line-height: 35px;
                        font-size: 20px;
                    }
                    input{
                        flex:1;
                        font-size: 16px;
                        line-height: 35px;
                        border:none;
                        background: RGBA(255,255,255,0);
                        outline: none;
                    }
                }
            }
            .wrap-right{
                display: flex;
                flex-basis: 35px;
                flex-shrink: 0;
                align-items: center;
                justify-content: flex-end;
                span{
                    font-size: 16px;
                }
            }
            &::after{
                position: absolute;
                content: '';
                bottom:0px;
                left:0px;
                width:100%;
                border-bottom: 1px solid @divider-color;
                transform: scaleY(0.5);
            }
        }
    }
    section{
        position: absolute;
        top:52px;
        left:0px;
        right:0px;
        bottom:0px;
        .search-indicator{
            min-height: 100%;
            background: white;
            .indicator-hot{
                display: flex;
                flex-wrap: wrap;
                .hot-item{
                    display: flex;
                    flex-grow: 0;
                    align-items: center;
                    height: 35px;
                    span{
                        padding:0px 7px;
                        font-size: 14px;
                        background: @divider-color;
                        color:@content-color;
                        border-radius: 20px;
                    }
                    &:not(:last-child){
                        margin-right:20px;
                    }
                }
            }
        }
    }
}
</style>

