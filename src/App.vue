<template>
  <div id="app">
    <div>
      <header class="site-header jumbotron">
        <div class="container">
          <div class="row">
            <div class="col-xs-12">
              <h1>请发表对Vue的评论</h1>
            </div>
          </div>
        </div>
      </header>
      <div class="container">
        <Add :addComment="addComment"/>
        <List :comments="comments" :deleteComment="deleteComment"/>
      </div>
    </div>
  </div>
</template>

<script>
  import Add from "./components/Add";
  import List from "./components/List";
    export default {
        name: "App",
      components: {List, Add},
      comments: {
        Add,
        List
      },
      data() {
          return {
            comments:[//数据在哪个组件，操作数据的方法或者行为就应该在哪个组件
              {
                name:'lisi',
                content:"vue NICE"
              },
              {
                name:'张三丰',
                content:"vue 还可以"
              },
              {
                name:'李白',
                content:"vue 还行"
              }
            ]
          }
      },
      methods:{
        //添加评论
        addComment(comment){
          this.comments.unshift(comment)
        },
        //删除指定下标评论
        deleteComment(index){
          this.comments.slice(index,1);
        }

      }
    }
</script>

<style scoped>

</style>
