<template>
  <div id="result" class="result">
    <div class="resultTop">
      <p>Result</p>
    </div>
    <div class="resultCenter">
      <component ref="cmpContent" :is="content"></component>
    </div>
  </div>
</template>

<script>
  import ContentA from './components/ContentA.vue';
  import ContentB from './components/ContentB.vue';

  export default {
    props: [
      'fileList'
    ],
    components: {
      ContentA,
      ContentB
    },
    computed:{
      content(){
        let content = 'ContentA';
        let routePath = this.$route.path;
        let contentIdx = routePath.indexOf('guide/');

        if ( contentIdx > 0 ) {
          content = routePath.slice(contentIdx+6);
        }

        return content;
      }
    },
    data() {
      return {
        name: 'ContentA',
        cnt: 1,
        htmlTxt: '<p class="red">It\'s magic!</p>',
        jsTxt: 'console.log("hi");',
        cssTxt: 'p {font-family: Helvetica, Arial; }'
      };
    },
    methods: {
    },
    mounted() {
    }
  }
</script>


<style scoped>
  .result {
    position: absolute;
    left: 50%;
    top: 0px;
    bottom: 0px;
    right: 0px;
    border: 1px solid #e5e5e5;
  }
  .result .resultTop {
    position: absolute;
    height: 50px;
    width: 100%;
    border-bottom: 1px solid #e5e5e5;
  }
  .result .resultTop > p {
    font-size: 20px;
    font-weight: bold;
    padding: 0 0 0 20px;
  }
  .result .resultCenter {
    position: absolute;
    top: 51px;
    height: calc(100% - 50px);
    width: 100%;
    padding: 20px 20px 20px 20px;
  }
</style>
