<template>
  <div align="center">
  <div>Bank it</div>
    <table border="2">
      <tr>
        <th align="center" width="80">No</th>
        <th align="center" width="320">Title</th>
        <th align="center" width="100">Writer</th>
        <th align="center" width="180">Registration Date</th>
      </tr>
      <tr v-if="!paginatedData || (Array.isArray(paginatedData) && paginatedData.length === 0)">
        <td colspan="4">
          List is empty
        </td>
      </tr>
      <tr v-for="page in paginatedData" :key="page.boardNo">
        <td>{{ page.boardNo }}</td>
        <td align="left">
          <router-link :to="{ name: 'BoardReadPage',
                  params: { boardNo: page.boardNo.toString() } }">
            {{ page.title }}
          </router-link>
        </td>
        <td>{{ page.writer }}</td>
        <td>{{ page.regDate }}</td>
      </tr>
    </table>
    <div class="text-center">
      <v-btn :disabled="pageNum === 0"
        @click="prevPage" class="page-btn">
        이전
      </v-btn>
      <span class="page-count">{{ pageNum + 1 }} / {{ pageCount }} 페이지</span>
      <v-btn :disabled="pageNum >= pageCount - 1"
        @click="nextPage" class="page-btn">
        다음
      </v-btn>
      <div></div>
      <router-link :to="{ name: 'BoardRegisterPage' }">
        새로운 글 쓰기
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'VuetifyListPageForm',
  data () {
    return {
      pageNum: 0,
      page: 1
    }
  },
  props: {
    listArray: {
      type: Array,
      required: true
    },
    pageSize: {
      type: Number,
      required: true,
      default: 5
    }
  },
  methods: {
    nextPage () {
      this.pageNum += 1
    },
    prevPage () {
      this.pageNum -= 1
    }
  },
  computed: {
    pageCount () {
      const listLen = this.listArray.length
      const listSize = this.pageSize

      let page = Math.floor(listLen / listSize)
      if (listLen % listSize > 0) {
        page += 1
      }

      return page
    },
    paginatedData () {
      const start = this.pageNum * this.pageSize
      const end = start + this.pageSize
      return this.listArray.slice(start, end)
    }
  }
}
</script>
