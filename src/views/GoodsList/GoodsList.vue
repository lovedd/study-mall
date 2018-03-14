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
            <a href="javascript:void(0)" class="filterby stopPop" @click="showFilterBy">Filter by</a>
          </div>
          <div class="accessory-result">
            <!-- filter -->
            <div class="filter stopPop" id="filter" :class="{'filterby-show': isShowFilterBy}">
              <dl class="filter-price">
                <dt>Price:</dt>
                <dd><a href="javascript:void(0)" :class="{'cur': priceChecked === 'all'}" @click="checkPriceFilter('all')">All</a></dd>
                <dd v-for="(item, index) in priceFilterList" :key="index">
                  <a href="javascript:void(0)" :class="{'cur': priceChecked === index}" @click="checkPriceFilter(index)">{{item.startPrice}} - {{item.endPrice}}</a>
                </dd>
              </dl>
            </div>

            <!-- search result accessories list -->
            <div class="accessory-list-wrap">
              <div class="accessory-list col-4">
                <ul>
                  <li v-for="item in showGoodsList" :key="item.productId">
                    <div class="pic">
                      <a href="#"><img v-lazy ="'/static/'+ item.prodcutImg" alt=""></a>
                    </div>
                    <div class="main">
                      <div class="name">XX</div>
                      <div class="price">{{item.prodcutPrice}}</div>
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
      <div class="md-overlay" v-show="isShowOverLay" @click="closeFilterBy"></div>
      <PageFooter></PageFooter>
    </div>
</template>

<script>
import PageHeader from '../../components/PageHeader'
import PageBread from '../../components/PageBread'
import PageFooter from '../../components/PageFooter'

export default {
  data () {
    return {
      goodsList: [],
      priceFilterList: [
        {
          startPrice: 100,
          endPrice: 500
        },
        {
          startPrice: 500,
          endPrice: 1000
        },
        {
          startPrice: 1000,
          endPrice: 3000
        }
      ],
      priceChecked: 'all',
      isShowFilterBy: false,
      isShowOverLay: false,
      filterPrice: {startPrice: 0, endPrice: Infinity}
    }
  },
  computed: {
    showGoodsList () {
      return this.goodsList.filter(item => {
        return this.filterPrice.startPrice < item.prodcutPrice && this.filterPrice.endPrice > item.prodcutPrice
      })
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
      this.$api.get('/api/goods', null, res => {
        let data = res.data
        console.log(res)
        this.goodsList = data.result
      })
    },
    checkPriceFilter (index) {
      this.priceChecked = index
      this.filterPrice = index === 'all' ? {startPrice: 0, endPrice: Infinity} : this.priceFilterList[index]
      this.closeFilterBy()
    },
    showFilterBy () {
      this.isShowFilterBy = true
      this.isShowOverLay = true
    },
    closeFilterBy () {
      this.isShowFilterBy = false
      this.isShowOverLay = false
    }
  }
}
</script>
