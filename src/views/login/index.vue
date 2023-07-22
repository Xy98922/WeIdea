<script setup lang="ts">
import {
  NButton, NButtonGroup, NCard, NCarousel, NCarouselItem, NForm,
  NFormItemRow, NInput, NModal, NTabPane, NTabs,
} from 'naive-ui'
import { reactive, ref } from 'vue'
import { useRoute } from 'vue-router'
import { loginInfo } from '@/api'
const route = useRoute()
const showSignModal = ref(false)
const items = reactive([
  { title: '特斯拉公司(Tesla)', content: 'Model 3/Y交付量', src: 'public/微信图片_20230720201647.png' },
  { title: 'X5零售集团股份有限公司', content: '股票表现', src: 'public/微信图片_20230720204248.png' },
  { title: 'CPI地产集团(O5G)', content: '留存收益', src: 'public/微信图片_20230720204257.png' },
  { title: 'CPI地产集团(O5G)', content: '汽车总交付量', src: 'public/微信图片_20230720204303.png' },
])
const detail = ref(false)
async function handleLogin() {
  try {
    console.log(await loginInfo('sss'))
  }
  catch (error: any) {

  }
  finally {

  }
}
</script>

<template>
  <div class="navbar">
    <div class="logo" />
    <NTabs type="line" animated tab-style="color:white">
      <NTabPane name="oasis" tab="首页" style="color: aliceblue;" />
      <NTabPane name="jay chou" tab="产品">
        <NCarousel show-arrow>
          <NCarouselItem v-for="item in items" :key="item.title">
            <NCard :title="item.title">
              <template #cover>
                <img :src="item.src">
              </template>
              {{ item.content }}
              <NButtonGroup>
                <NButton @click="detail = true">
                  查看智能分析
                </NButton>
                <NButton>
                  <router-link to="/chat/:uuid?">
                    咨询
                  </router-link>
                </NButton>
                <NButton>
                  购买
                </NButton>
              </NButtonGroup>
              <NModal
                v-model:show="detail"
                class="custom-card"
                preset="card"
                style="width: 600px"
                title="大成互联网+大数据A"
                size="huge"
                :bordered="false"
                :segmented="{
                  content: 'soft',
                  footer: 'soft',
                } "
              >
                002236|偏股型基金
                近一年涨幅：29.46%
                日涨跌幅：0.05%
                <template #footer>
                  大成互联网+大数据A基金的资产配置为：股票占比88.89%，现金7.35%，其他3.76%。重仓股票为：云南白药 (000538)占比40%，古井贡酒(000596)占比30%，汇川技术(300124)占比。该基金的资金和股票配置相对稳健，重仓的股票整体趋势良好，以下是对各股票的分析。

                  云南白药（占比40%）

                  云南白药 (000538)的财务情况为：ROE为7.87%，净利润现金比率为107.00%，资产负债率为27.75%，毛利率为26.32%，营业利润率为9.24%，营业收入增长率为0.31%，固定资产比率为4.91%，分红率为39.81%。综合来看，云南白药公司的财务情况相对稳定。ROE和净利润现金比率表明公司在利润创造和现金管理方面表现良好。资产负债率较低，说明公司的债务相对较少。毛利率和营业利润率表明公司在销售和经营方面有一定的盈利能力。然而，营业收入增长率相对较低，固定资产比率也较低，这可能意味着公司在扩张和投资方面的表现有限。此外，分红率较高，这可能对公司的现金流和再投资能力产生一定影响。

                  古井贡酒（占比30%）

                  古井贡酒(000596)的财务情况为：ROE为17.93%，净利润现金比率为98.80%，资产负债率为35.10%，毛利率为77.17%，营业利润率为26.64%，营业收入增长率为25.95%，固定资产比率为8.25%，分红率为29.93%。综合来看，古井贡酒的财务情况相对良好。ROE较高，说明公司能够有效地利用股东权益创造利润。净利润现金比率接近1，表明公司的净利润主要以现金形式存在。资产负债率适中，说明公司的债务相对较低。毛利率和营业利润率较高，显示公司在销售产品时能够保持较高的利润水平。营业收入增长率较高，表明公司的营业收入在一定时期内有较快的增长。固定资产比率较低，说明公司的固定资产投资相对较少。分红率较高，显示公司愿意将一部分利润分配给股东。总体而言，古井贡酒的财务情况良好，但仍需注意监控各项指标的变化，以确保持续的财务稳定和增长。
                </template>
              </NModal>
            </NCard>
          </NCarouselItem>
        </NCarousel>
      </NTabPane>
    </NTabs>
    <NButton class="loginIn" type="primary" @click="showSignModal = true">
      登录
    </NButton>
  </div>
  <div id="Nav" class="video-lvWKNq710v">
    <video src="https://moka-public-tc-1258232444.cos.ap-beijing.myqcloud.com/webankhr/1066810ba6b4468f8aa6ecfccc5328e8.mp4?sign=q-sign-algorithm%3Dsha1%26q-ak%3DAKIDKTLxLSIr9BwQdaHhqjLgkdFaeQwA9qHR%26q-sign-time%3D1660286691%3B3807770338%26q-key-time%3D1660286691%3B3807770338%26q-header-list%3Dhost%26q-url-param-list%3D%26q-signature%3Daba6c5d750c37a32ea9f99d730a9fe51d3efe5d0" height="793px" autoplay loop muted style="object-fit: cover;" />
  </div>
  <NModal v-model:show="showSignModal">
    <NCard class="signcard">
      <NTabs
        class="card-tabs"
        default-value="signin"
        size="large"
        animated
        pane-wrapper-style="margin: 0 -4px"
        pane-style="padding-left: 4px; padding-right: 4px; box-sizing: border-box;"
      >
        <NTabPane name="signin" tab="登录">
          <NForm>
            <NFormItemRow label="用户名">
              <NInput />
            </NFormItemRow>
            <NFormItemRow label="密码">
              <NInput
                type="password"
                show-password-on="mousedown"
              />
            </NFormItemRow>
          </NForm>
          <NButton type="primary" block secondary strong @click="handleLogin">
            登录
          </NButton>
        </NTabPane>
        <NTabPane name="signup" tab="注册">
          <NForm>
            <NFormItemRow label="用户名">
              <NInput />
            </NFormItemRow>
            <NFormItemRow label="密码">
              <NInput
                type="password"
                show-password-on="mousedown"
              />
            </NFormItemRow>
            <NFormItemRow label="重复密码">
              <NInput
                type="password"
                show-password-on="mousedown"
              />
            </NFormItemRow>
          </NForm>
          <NButton type="primary" block secondary strong>
            注册
          </NButton>
        </NTabPane>
      </NTabs>
    </NCard>
  </NModal>
</template>

  <style scoped>
 .video-lvWKNq710v {
    position: relative;
    display: -webkit-box;
    display: -webkit-flex;
    display: -moz-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-pack: center;
    -webkit-justify-content: center;
    -moz-box-pack: center;
    -ms-flex-pack: center;
    justify-content: center;
    -webkit-box-align: center;
    -webkit-align-items: center;
    -moz-box-align: center;
    -ms-flex-align: center;
    align-items: center;
    background-color: #000;
    border-bottom:1px solid #3a474b ;
    overflow: visible;
}
video{
    border-bottom:1px solid #3a474b ;
 }
.navbar{
    position: fixed;
    z-index: 3;
    top: 0;
    right: 0;
    left: 0;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    min-width: 960px;
    padding: 0 140px;
    -webkit-transition: background-color 0.3s;
    -o-transition: background-color 0.3s;
    -moz-transition: background-color 0.3s;
    transition: background-color 0.3s;
    color: aliceblue!important;
}
.card-tabs .NTabs-nav--bar-type {
  padding-left: 4px;
  color: aliceblue;
}
.navbar .logo{
    width: 54px;
    height: 36px;
    background-size: 54px 36px;
    background-image: url('https://public-cdn-tc.mokahr.com/webankhr/46a98f0f-66b1-40d0-9c47-8271becdeb94.png');
    position: absolute;
    top: 8px;
    left: 50px;
}
.loginIn{
    position: absolute;
    top: 5px;
    right: 150px;
    color: white;
}
.signcard{
    width: 30%;
}
.n-card {
  max-width: 850px;
  margin-left: 15%;
}
.carousel-img {
  width: 100%;
  height: 240px;
  object-fit: cover;
}
.n-button-group {
    float: right;
}
  </style>
