<template>
  <div class="ui container segment">
    <h1>CountUp</h1>
    <p v-html="desc">
    </p>
    <table class="ui celled table">
      <thead>
        <tr><th>参数</th><th>说明</th></tr>
      </thead>
      <tbody>
        <tr v-for="parm in parms"> <td class="single line"> {{parm.parm}} </td> <td> {{parm.desc}} </td></tr>
      </tbody>
    </table>
    <code v-text="code">
    </code>
    <div class="ui divider"></div>
    <button @click='run' class='ui basic button'>
      <i class='icon play'></i>
      运行
    </button>
    <count-up :end="count" :duration="2.5" :options="{useEasing : true,
      useGrouping : true,
      separator : ',',
      decimal : '.',
      prefix : '',
      suffix : ''}">
    </count-up>
  </div>
</template>

<script>
  import CountUp from './Bz'
  export default {
    components: {
      CountUp
    },
    data: function () {
      return {
        count: 0,
        title: 'CountUp',
        desc: `
        缓速变化数字的效果，用到了<a href="https://inorganik.github.io/countUp.js/">countUp.js</a>，把<a href="https://github.com/samcrosoft/vue-countup">vue-countup</a>改为了数据绑定的
        `,
        parms: [
          {parm: 'end', desc: '结束的数字'},
          {parm: 'duration', desc: '速度?'},
          {parm: 'options', desc: '配置项'}
        ],
        code: `
        <count-up
        :end="count"
        :duration="2.5"
        :options="{useEasing : true,
          useGrouping : true,
          separator : ',',
          decimal : '.',
          prefix : '',
          suffix : ''} ">
        </count-up>`
      }
    },
    methods: {
      run: function () {
        if (this.count === 0) {
          this.count = 5000
        } else {
          this.count = 0
        }
      }
    }
  }
</script>
