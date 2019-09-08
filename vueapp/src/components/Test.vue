<template>
    <div class="test">
        <!--获取数据 -->  
        <h1>{{title}}</h1>
        <p>{{user.firstName}}</p>
        <p v-text="user.lastName"></p>
 
        <!--v-if -->  
        <p v-if="showName">{{user.firstName}}</p>
        <!--v-else --> 
        <p v-else> Nobody</p>

        <!--v-for -->
        <ul>
            <li v-for="item in items">{{item.title}}
            </li>
        </ul>

       <!--v-on -->
       <button v-on:click="greet('hello everybody')">say greeting
       </button> 

       <!--键盘事件 -->
       <input type="text" v-on:keyup="pressKey" v-on:keyup.alt.enter="enterHit"/>

    <hr>
       <!--computed 计算属性 -->
       <label>FirstName:</label>
       <input type="text" v-model="user.firstName">
       <br>
       <label>LastName:</label>
       <input type="text" v-model="user.lastName">
       <br>

       <h3>{{fullName}}</h3>

       <!--props 属性 -->
        <h2>{{msg}}</h2>
    </div>
</template>

<script>
    export default {
        name:"test",
        props:{
            msg:{
                type:String,
                default:"默认就是当前文字"
            }
        },
        data() {
            return {
                title:"hello Vue.js!",
                user:{
                    firstName:"qin",
                    lastName:"peng"
                },
                showName:false,
                items:[
                    { title:"item 1"},
                    { title:"item 2"},
                    { title:"item 3"}
                ]
            }
      
        },
        methods: {
            greet:function(greeting){
                alert(greeting);
            },
            pressKey:function(){
                console.log("pressed......");
            },
            enterHit:function(){
                console.log("you pressed enter key!!!")
            }
        },
        computed: {
            fullName:function(){
                return this.user.firstName + " " + this.user.lastName;
            }
        },
    }
</script>

<style scoped>

</style>