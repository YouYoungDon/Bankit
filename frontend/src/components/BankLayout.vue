<template>
  <v-card
    class="mx-auto overflow-hidden"
    height="1200"
  >
    <v-app id="inspire">
      <v-app-bar
        app
        clipped-right
        dark
        shrink-on-scroll
        src="https://i.picsum.photos/id/283/1920/1080.jpg?hmac=VZ2X9gUoyGt_QHQvSkxka5LvnUxGA-apDHwcfIiLHAM"
      >
        <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <v-toolbar-title><v-text class="text-h4 font-weight-black">Bank </v-text><v-text class="text-h3 pink--text font-weight-black">i</v-text><v-text class="text-h4 font-weight-black">t</v-text></v-toolbar-title>
        <v-spacer></v-spacer>
          <v-btn icon color="red">
            <v-icon>mdi-heart</v-icon>
          </v-btn>
          <v-menu
            bottom
            left
          >
          </v-menu>
        <template v-slot:extension>
          <v-tabs
            v-model="tab"
          >
            <v-tab
              v-for="item in BoardItems"
              :key="item.tab"
            >
            <p class="white--text font-weight-black">{{ item.tab1 }}</p>
            </v-tab>
            <v-tab
              v-for="item in CardItems"
              :key="item.tab"
            >
            <p class="white--text font-weight-black">{{ item.tab1 }}</p>
            </v-tab>
            <v-tab
              v-for="item in FundItems"
              :key="item.tab"
            >
            <p class="white--text font-weight-black">{{ item.tab1 }}</p>
            </v-tab>
            <v-tab
              v-for="item in SaveItems"
              :key="item.tab"
            >
            <p class="white--text font-weight-black">{{ item.tab1 }}</p>
            </v-tab>
          </v-tabs>
        </template>
        <slot name="menubar"></slot>
      </v-app-bar>
      <v-navigation-drawer
        v-model="drawer"
        app
      >
        <v-list dense>
          <v-list-item @click.stop="left = !left">
            <v-list-item-action>
              <v-icon>mdi-home</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title @click="home">홈으로 이동</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
        <v-list dense>
          <v-list-item @click.stop="left = !left">
            <v-list-item-action>
              <v-icon>mdi-cart</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title @click="cart">찜</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
        <v-tabs-items v-model="tab">
          <v-tab-item
            v-for="item in BoardItems"
            :key="item.tab"
          >
            <v-card flat>
              <board-list-page-form :list-array="pageArray"/>
            </v-card>
          </v-tab-item>
          <v-tab-item align="center"
            v-for="item in CardItems"
            :key="item.tab"
          >
          <br>
          <p>
          <v-btn color="red" v-if=checkedCards v-on:click="calcBuy()">찜하기</v-btn>
          </p>
          <v-layout>
            <v-col
              cols="12"
              md="4"
            >
              <v-card flat>
                <v-card color="brown lighten-3" class="white--text font-weight-bold">{{ item.content1 }}</v-card>
              </v-card>
              <v-img
                :src="require('/home/bitai/Downloads/card.jpeg')"
                class="my-3"
                max-width="200"
                max-height="300"
              />
              <a class="product_lick" href="https://www.shinhancard.com/pconts/html/card/apply/credit/1196945_2207.html">▲▲카드보러가기▲▲</a>
              <p>
              <input type="checkbox" v-model="checkedCards" id="네이버카드" value="네이버 카카오 카드">네이버 카카오 카드
              </p>
              <v-img
                :src="require('/home/bitai/Downloads/card1.jpeg')"
                class="my-3"
                max-width="200"
                max-height="300"
              />
              <a class="product_lick" href="https://www.shinhancard.com/pconts/html/card/apply/credit/1196674_2207.html">▲▲카드보러가기▲▲</a>
              <p>
              <input type="checkbox" v-model="checkedCards" id="신한카드" value="신한카드-1">신한카드-1
              </p>
              <v-img
                :src="require('/home/bitai/Downloads/card2.jpeg')"
                class="my-3"
                max-width="200"
                max-height="300"
              />
              <a class="product_lick" href="https://www.shinhancard.com/pconts/html/card/apply/credit/1197027_2207.html">▲▲카드보러가기▲▲</a>
              <p>
              <input type="checkbox" v-model="checkedCards" id="신한카드" value="신한카드-2">신한카드-2
              </p>
              <v-img
                :src="require('/home/bitai/Downloads/card3.jpeg')"
                class="my-3"
                max-width="200"
                max-height="300"
              />
              <a class="product_lick" href="https://www.shinhancard.com/pconts/html/card/apply/credit/1196302_2207.html">▲▲카드보러가기▲▲</a>
              <p>
              <input type="checkbox" v-model="checkedCards" id="신한카드" value="신한카드-3">신한카드-3
              </p>
              <v-img
                :src="require('/home/bitai/Downloads/card4.jpeg')"
                class="my-3"
                max-width="200"
                max-height="300"
              />
              <a class="product_lick" href="https://www.shinhancard.com/pconts/html/card/apply/credit/1197177_2207.html">▲▲카드보러가기▲▲</a>
              <p>
              <input type="checkbox" v-model="checkedCards" id="신한카드" value="신한카드-4">신한카드-4
              </p>
            </v-col>
            <v-col
              cols="12"
              md="4"
            >
              <v-card flat>
                <v-card color="brown lighten-3" class="white--text font-weight-bold">{{ item.content2 }}</v-card>
              </v-card>
              <v-img
                :src="require('/home/bitai/Downloads/bc.jpeg')"
                class="my-3"
                max-width="200"
                max-height="300"
              />
              <a class="product_lick" href="https://m.bccard.com/app/mobileweb/CardDetail.do?exec=cardDetail&cardGdsNo=1000026845">▲▲카드보러가기▲▲</a>
              <p>
              <input type="checkbox" v-model="checkedCards" id="비씨카드" value="비씨카드-1">비씨카드-1
              </p>
              <v-img
                :src="require('/home/bitai/Downloads/bc1.jpeg')"
                class="my-3"
                max-width="200"
                max-height="300"
              />
              <a class="product_lick" href="https://m.bccard.com/app/mobileweb/CardDetail.do?exec=cardDetail&cardGdsNo=1001030000">▲▲카드보러가기▲▲</a>
              <p>
              <input type="checkbox" v-model="checkedCards" id="비씨카드" value="비씨카드-2">비씨카드-2
              </p>
              <v-img
                :src="require('/home/bitai/Downloads/bc2.jpeg')"
                class="my-3"
                max-width="200"
                max-height="300"
              />
              <a class="product_lick" href="https://m.bccard.com/app/mobileweb/CardDetail.do?exec=cardDetail&cardGdsNo=1000024919">▲▲카드보러가기▲▲</a>
              <p>
              <input type="checkbox" v-model="checkedCards" id="비씨카드" value="비씨카드-3">비씨카드-3
              </p>
              <v-img
                :src="require('/home/bitai/Downloads/bc3.jpeg')"
                class="my-3"
                max-width="200"
                max-height="300"
              />
              <a class="product_lick" href="https://m.bccard.com/app/mobileweb/CardDetail.do?exec=cardDetail&cardGdsNo=1000026779">▲▲카드보러가기▲▲</a>
              <p>
              <input type="checkbox" v-model="checkedCards" id="비씨카드" value="비씨카드-4">비씨카드-4
              </p>
              <v-img
                :src="require('/home/bitai/Downloads/bc4.jpeg')"
                class="my-3"
                max-width="200"
                max-height="300"
              />
              <a class="product_lick" href="https://m.bccard.com/app/mobileweb/CardDetail.do?exec=cardDetail&cardGdsNo=1000025332">▲▲카드보러가기▲▲</a>
              <p>
                <input type="checkbox" v-model="checkedCards" id="비씨카드" value="비씨카드-5">비씨카드-5
              </p>
            </v-col>
            <v-col
              cols="12"
              md="4"
            >
              <v-card flat>
                <v-card color="brown lighten-3" class="white--text font-weight-bold">{{ item.content3 }}</v-card>
              </v-card>
              <v-img
                :src="require('/home/bitai/Downloads/gong.jpeg')"
                class="my-3"
                max-width="200"
                max-height="300"
              />
              <a class="product_lick" href="https://m.bccard.com/service/card_issue_cardhappy.html">▲▲카드보러가기▲▲</a>
              <p>
                <input type="checkbox" v-model="checkedCards" id="공공카드" value="공공카드-1">공공카드-1
              </p>
              <v-img
                :src="require('/home/bitai/Downloads/gong1.jpeg')"
                class="my-3"
                max-width="200"
                max-height="300"
              />
              <a class="product_lick" href="https://m.bccard.com/card/card_6.html">▲▲카드보러가기▲▲</a>
              <p>
                <input type="checkbox" v-model="checkedCards" id="공공카드" value="공공카드-2">공공카드-2
              </p>
              <v-img
                :src="require('/home/bitai/Downloads/gong2.jpeg')"
                class="my-3"
                max-width="200"
                max-height="300"
              />
              <a class="product_lick" href="https://m.bccard.com/card/card_3.html">▲▲카드보러가기▲▲</a>
              <p>
                <input type="checkbox" v-model="checkedCards" id="공공카드" value="공공카드-3">공공카드-3
              </p>
              <v-img
                :src="require('/home/bitai/Downloads/gong3.jpeg')"
                class="my-3"
                max-width="200"
                max-height="300"
              />
              <a class="product_lick" href="https://m.bccard.com/card/card_8.html">▲▲카드보러가기▲▲</a>
              <p>
                <input type="checkbox" v-model="checkedCards" id="공공카드" value="공공카드-4">공공카드-4
              </p>
              <v-img
                :src="require('/home/bitai/Downloads/gong4.jpeg')"
                class="my-3"
                max-width="200"
                max-height="300"
              />
              <a class="product_lick" href="https://m.bccard.com/card/card_4.html">▲▲카드보러가기▲▲</a>
              <p>
                <input type="checkbox" v-model="checkedCards" id="공공카드" value="공공카드-5">공공카드-5
              </p>
            </v-col>
          </v-layout>
          </v-tab-item>
          <v-tab-item
            v-for="item in FundItems"
            :key="item.tab"
          >
          </v-tab-item>
          <v-tab-item
            v-for="item in SaveItems"
            :key="item.tab"
          >
          </v-tab-item>
        </v-tabs-items>
      <v-footer
        app
        color="brown lighten-3"
        class="white--text"
        shrink-on-scroll
      >
        <v-spacer></v-spacer>
        <span>&copy; Bank it</span>
      </v-footer>
    </v-app>
  </v-card>
</template>

<script>
import router from '../router'
import axios from 'axios'
import BoardListPageForm from '@/components/BoardListPageForm.vue'
import { mapState, mapGetters } from 'vuex'

export default {
  name: 'VuetifyBoardListPage',
  computed: {
    ...mapState(['myinfo'], ['checkedCards']),
    ...mapGetters(['isAuthorized'], ['checkedCards'])
  },
  components: {
    BoardListPageForm
  },
  created () {
    axios.get('http://localhost:7777/boards')
      .then(res => {
        console.log(res)
        this.pageArray = res.data
      })
      .catch(err => {
        console.log(err)
      })
  },
  data: () => ({
    pageArray: [],
    tab: null,
    CardItems: [
      { tab1: '카드', content1: '신한카드', content2: '비씨카드', content3: '공공카드' }
    ],
    FundItems: [
      { tab1: '펀드', content1: '펀드 카테고리' }
    ],
    SaveItems: [
      { tab1: '적금', content1: '적금 카테고리' }
    ],
    BoardItems: [
      { tab1: '게시판', content1: '게시판' }
    ],
    components: { BoardListPageForm },
    drawer: false,
    left: false,
    checkedCards: []
  }),
  methods: {
    home () {
      (window.location.pathname === '/') ? router.push('/') : router.go(0)
    },
    cart () {
      (window.location.pathname !== '/') ? router.push('/BankCart') : router.go(0)
    },
    calcBuy () {
      if (this.checkedCards.length !== 0) {
        this.$store.commit('setCheckCards', this.checkedCards)
        this.checkbox = false
        alert('찜완료')
      } else {
        alert('체크된 카드가 없습니다')
      }
    }
  }
}
</script>
