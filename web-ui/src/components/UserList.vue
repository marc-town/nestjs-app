<template>
  <div>
    <h1>ユーザー管理画面</h1>
    {{ name }}
  </div>
</template>

<script>
import { mapState, mapActions } from "vuex";
export default {
  components: {},
  data () {
    return {}
  },
  mixins: [],
  computed: {
    ...mapState('user', [
      'name'
    ])
  },
  watch: {},
  methods: {
    ...mapActions('user', [
      'setUser'
    ]),
    initialize: function() {
      this.fetchData();
    },
    fetchData: async function() {
      try {
        const users = await this.$axios.get('/users')
        this.setUser(users.data[0])
      } catch (error) {
        // サンプルで書いてるだけなので特に何もしない
      }
    }
  },
  // 以下、ライフサイクル系処理
  beforeCreate: function() {
  },
  created: function() {
    this.initialize()
  },
  beforeMount: function() {
  },
  mounted: function() {
  },
  beforeUpdate: function() {
  },
  updated: function() {
  },
  beforeDestroy: function() {
  },
  destroyed: function() {
  }
}
</script>

<style scoped>
</style>