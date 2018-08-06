<template>
  <div class="col-md-4">
    <form class="form-horizontal">
      <div class="form-group">
        <label>用户名</label>
        <input type="text" class="form-control" placeholder="用户名" v-model="name">
      </div>
      <div class="form-group">
        <label>评论内容</label>
        <textarea class="form-control" rows="6" placeholder="评论内容" v-model="content"></textarea>
      </div>
      <div class="form-group">
        <div class="col-sm-offset-2 col-sm-10">
          <button @click="add" type="button" class="btn btn-default pull-right">提交</button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
    export default {
      name: "Add",
      props:{
        addComment:{ //指定属性名，属性值的类型，必要性
          type: Function,
          require:true
        }
      },
      data(){
          return {
            name:'',
            content:''
          }
      },
      methods:{
        add(){
          //1.合法
          const name = this.name.trim();
          const content = this.content.trim();
          if(!name||!content){
            alert("不能为空1")
          }
          //2.输入的数据分装成对象
          const  comment={
            name,content
          }
          //3.添加到comments中
          this.addComment(comment);
          //4.清除输入
          this.name = this.content = '';

        }
      }
    }
</script>

<style scoped>

</style>
