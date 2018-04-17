<template>
  <div>
    <v-title title="Vue组件化"></v-title>
    <v-button @click="handleClick">点击按钮</v-button>
    <input type="text" v-model="name" placeholder="你的名字">
    <h1>你好，{{ name }}</h1>
    <div>
      {{ date | formatDate }}
    </div>
    <div>
      {{ reversedText }}
    </div>
    <div>
      {{ classes }}
    </div>
    <ul>
      <li v-for="(value, key, index) in user">
        {{ index }} - {{ key }} : {{ value }}
      </li>
    </ul>
    <ul>
      <template v-for="book in filterBooks">
        <li>书名: {{ book.name }}</li>
        <li>作者: {{ book.author }}</li>
      </template>
    </ul>
  </div>
</template>
<script>
  import vTitle from './components/title.vue';
  import vButton from './components/button.vue';

  export default {
    components: {
      vTitle,
      vButton
    },
    created () {
      this.name = 'created';
      console.log(this.name);
    },
    mounted () {
      this.name = 'mounted';
      console.log(this.name);
      var _this = this;
      this.timer = setInterval(function() {
        _this.date = new Date();
      }, 1000);
    },
    beforeDestory () {
      if(this.timer) {
        clearInterval(this.timer);
      }
    },
    methods: {
      handleClick (e) {
        console.log(e);
        console.log(this.name);
        this.name= 'click';
        this.books.push({
          name: '《JavaScript揭秘》',
          author: '[希]Lea Verou'
        });
        console.log(this.books.length);
        this.books[2] = {
          name: '《CSS揭秘》',
          author: '[希]Lea Verou'
        }
        console.log(this.books[2]);
      }
    },
    data () {
      return {
        color: '#f60',
        name: '',
        date: new Date(),
        text: '123,456',
        isActive: true,
        error: null,
        user: {
          name: 'Aresn',
          gender: '男',
          age: 26
        },
        books: [
          {
            name: '《Vue.js实战》',
            author: '梁灏'
          },
          {
            name: '《JavaScript语言精粹》',
            author: 'Douglas Crockford'
          },
          {
            name: '《JavaScript高级程序设计》',
            author: 'Nicholas C.Zakas'
          }
        ]
      }
    },
    computed: {
      reversedText () {
        return this.text.split(',').reverse().join(',');
      },
      classes () {
        return {
          active: this.isActive && !this.error,
          'text-fail': this.error && this.error.type === 'fail'
        }
      },
      filterBooks () {
        return this.books.filter((book) => book.name.match(/JavaScript/));
      }
    },
    filters: {
      formatDate (value) {
        var padDate = function(value) {
          return value < 10 ? '0' + value : value;
        }
        var date = new Date(value);
        var year = date.getFullYear();
        var month = padDate(date.getMonth() + 1);
        var day = padDate(date.getDate());
        var hours = padDate(date.getHours());
        var minutes = padDate(date.getMinutes());
        var seconds = padDate(date.getSeconds());

        return year + '-' + month + '-' + day + ' ' + hours + ':' + minutes + ':' + seconds;
      }
    }
  }
</script>
<style scoped>
  div{
    color: #f60;
    font-size: 24px;
  }
</style>
