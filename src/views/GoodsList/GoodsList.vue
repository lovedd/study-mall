<template>
    <div>
      <PageHeader></PageHeader>
      <PageBread>
        <span>Goods</span>
      </PageBread>
      <div class="accessory-result-page accessory-page">
        <div class="container">
          <div class="filter-nav">
            <span class="sortby">Sort by:</span>
            <a href="javascript:void(0)" class="default cur">Default</a>
            <a href="javascript:void(0)" class="price">Price <svg class="icon icon-arrow-short"><use xlink:href="#icon-arrow-short"></use></svg></a>
            <a href="javascript:void(0)" class="filterby stopPop">Filter by</a>
          </div>
          <div class="accessory-result">
            <!-- filter -->
            <div class="filter stopPop" id="filter">
              <dl class="filter-price">
                <dt>Price:</dt>
                <dd><a href="javascript:void(0)">All</a></dd>
                <dd>
                  <a href="javascript:void(0)">0 - 100</a>
                </dd>
                <dd>
                  <a href="javascript:void(0)">100 - 500</a>
                </dd>
                <dd>
                  <a href="javascript:void(0)">500 - 1000</a>
                </dd>
                <dd>
                  <a href="javascript:void(0)">1000 - 2000</a>
                </dd>
              </dl>
            </div>

            <!-- search result accessories list -->
            <div class="accessory-list-wrap">
              <div class="accessory-list col-4">
                <ul>
                  <li v-for="item in goodsList" :key="item.productId">
                    <div class="pic">
                      <a href="#"><img :src="'/static/'+ item.prodcutImg" alt=""></a>
                    </div>
                    <div class="main">
                      <div class="name">XX</div>
                      <div class="price">999</div>
                      <div class="btn-area">
                        <a href="javascript:;" class="btn btn--m">加入购物车</a>
                      </div>
                    </div>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
      <PageFooter></PageFooter>
    </div>
</template>

<script>
import axios from 'axios'
import PageHeader from '../../components/PageHeader'
import PageBread from '../../components/PageBread'
import PageFooter from '../../components/PageFooter'

export default {
  data () {
    return {
      goodsList: []
    }
  },
  mounted () {
    this.getGoodsList()
  },
  components: {
    PageHeader,
    PageBread,
    PageFooter
  },
  methods: {
    getGoodsList () {
      axios.get('/api/goods.do').then((res) => {
        let data = res.data.data
        console.log(res)
        this.goodsList = data.result
      })
    }
  }
}
</script>
