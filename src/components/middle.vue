<template>
    <div>
        <div class="middles">
            <div class="middles-a">
                <div class="a-left"></div>
                <input type="text" placeholder="搜索" v-model="inputext">
            </div>
            <div class="middles-b">
                <div class="b-list" v-show="halo">
                    <div class="list-user" v-for="(item,index) in userList" :key="index" @click="onchat(item.username,item.imgUrl)">
                        <div class="user-left">
                            <img :src="item.imgUrl" />
                        </div>
                        <div class="user-right">
                            <div class="user-right-a">
                                <div class="right-a-a">{{item.username}}</div>
                                <div class="right-a-b">{{timer}}</div>
                            </div>    
                            <div class="user-right-b">{{messages}}</div>
                        </div>
                        

                    </div>
                </div>
                 <div class="b-list" v-show="halos">
                      <div class="list-user" v-for="(item,index) in hadio" :key="index" @click="onchat(item.username,item.imgUrl)">
                        <div class="user-left">
                            <img :src="item.imgUrl" />
                        </div>
                        <div class="user-right">
                            <div class="user-right-a">
                                <div class="right-a-a">{{item.username}}</div>
                                <div class="right-a-b">{{timer}}</div>
                            </div>    
                            <div class="user-right-b">{{messages}}</div>
                        </div>
                        

                    </div>
                 </div>
            </div>
        </div>
    </div>
</template>
<script>
import bus from '@/event/eventBus.js'
export default {
    data(){
        return{
            arrList:[
                // {imageUrl:require("../assets/bn1.jpg"),message:"123"}
            ],
            inputext:"",
            messages:"", 
            userList:[
                {imgUrl:require("../assets/user1.png"),username:"甲",id:1},
                {imgUrl:require("../assets/user2.png"),username:"乙",id:2},
                {imgUrl:require("../assets/user3.png"),username:"丙",id:3},
                {imgUrl:require("../assets/user4.png"),username:"丁",id:4}
                ],
            timer:"",
            hadio:[],
            halo:true,
            halos:false
            
        }
    },
    methods:{
        onchat(username,imgUrl){
            
            bus.$emit('halo',true,username,imgUrl);
        },
    },
    watch:{
        inputext(newText,oldText){
          var current = this.userList.findIndex(v => v.username == newText);
            if(newText === ""){
                this.halo = true;
                this.halos = false;
                this.hadio = [];
                this.userList = this.userList.sort(function(a,b){
                    if(a.id<b.id){
                        return -1;
                    }else if(a.id>b.id){
                        return 1;
                    }else{
                        return 0;
                    }
                });
            }else{
                if(current === -1){
                this.halo = false;
                this.halos = true;
                this.hadio = [];
            }else{
                this.hadio.push(this.userList[current]);
                this.halo = false;
                this.halos = true; 
                this.userList.splice(current,1);
                this.userList = this.hadio.concat(this.userList);
                
            }
            }


            // if(current === -1){
            //     this.halo = true;
            //     this.halos = false;
            //     this.hadio = [];
            //     this.userList = this.userList.sort(function(a,b){
            //         if(a.id<b.id){
            //             return -1;
            //         }else if(a.id>b.id){
            //             return 1;
            //         }else{
            //             return 0;
            //         }
            //     });
            // }else{
            //     this.hadio.push(this.userList[current]);
            //     this.halo = false;
            //     this.halos = true; 
            //     this.userList.splice(current,1);
            //     this.userList = this.hadio.concat(this.userList);
                
            // }
        }
    }
}
</script>
<style scoped>
    .middles{
        width:220px;
        height:600px;
        background: #FFFFCC;
        position:absolute;
        top:58px;
        left:118px;
    }
    .middles-a{
        width:200px;
        height:35px;
        background:#CCCC99;
        margin:10px auto;
        border-radius:4px;
        display:flex;
    }
    .a-left{
        width:25px;
        height:25px;
        background:url("../assets/bn5.png");
        background-size:25px 25px;
        margin-left:5px;
        margin-top:5px;
    }
    .middles-a>input{
        display:block;
        flex:1;
        height:25px;
        margin-top:5px;
        border-radius:4px;
        border-style:none;
        background-color: transparent;       
    }
    .b-list{
        width:200px;
        height:535px;
        margin:15px auto;
        /* background:orange; */
    }
    .list-user{
        width:200px;
        height:49px;
        /* background: green; */
        border-bottom:1px solid aqua;
        display:flex;
        cursor:pointer;
    }
    .list-user>div{
        margin-top:3px;
    }
    .user-left{
        width:45px;
        height:45px;
        border-radius:4px;
        background: #CCCC99;
    }
    .user-left>img{
        width:45px;
    }
    .user-right{
        height:45px;
        flex:1;
        /* background: tomato; */
    }
    .user-right-a{
        display:flex;
    }
    .right-a-a{
        width:98px;
        height:20px;
        font-size:18px;
        margin-left:3px;
    }
    .right-a-b{
        flex:1;
        height:20px;
        line-height:25px;
        font-size:13px;
    }
    .user-right-b{
        width:50px;
        height:15px;
        /* border:1px solid black; */
        margin-top:5px;
        font-size:12px;
        overflow:hidden;
        margin-left:3px;
        overflow:hidden;
    }
    .right-body{
        width:460px;
        height:600px;
        background:#CCCC99;
        position:absolute;
        top:58px;
        left:338px;
        display:flex;
        justify-content:center;
        align-items: center;
    }
    .right-body-a{
        width:460px;
        height:600px;
        background:#CCCC99;
        position:absolute;
        top:58px;
        left:338px;
    }
    .right-body-b{
        width:450px;
        height:49px;
        margin:15px auto;
        display:flex;
        border-bottom:1px solid aqua;
    }
    .body-b-a{
        width:45px;
        height:45px;
        background: url("../assets/user1.png");
        background-size:45px;
        border-radius:4px;
        margin-top:2px;
    }
    .body-b-b{
        height:49px;
        flex:1;
        font-size:20px;
        line-height:50px;
        padding-left:3px;
    }
    .body-c{
        width:440px;
        height:299px;
        border-bottom:1px solid aqua;
        margin:0 auto;
        overflow-y:scroll;
        overflow-x:hidden;
    }
    .body-c-a{
        width:440px;
        height:30px;
        margin:0 auto;
    }
    .body-c-b{
        display:block;
        width:30px;
        height:30px;
        background: blue;
        visibility: hidden;
    }
    .body-c-c{
        width:30px;
        height:30px;
        background:url("../assets/edit.png");
        background-size:30px 30px;
        position:absolute;
        top:380px;
        cursor:pointer;
    }
    .body-c-d{
        display:block;
        margin:5px auto;
        border-style:none;
        font-size:20px;
        width:440px;
        height:130px;
        background-color:transparent;
        resize:none;
    }
    .body-c-e{
        width:100px;
        height:30px;
        background: orange;
        font-size:20px;
        text-align:center;
        border-radius:5px;
        margin:10px 352px;
        cursor:pointer;
        overflow:hidden;
    }
    .body-d{
        width:440px;
        /* height:50px; */
        margin:0 auto;
        margin-bottom:5px;
        display:flex;
    }
    .body-d-b{
        min-width:50px;
        height:50px;
        /* background:url("../assets/bn1.jpg"); */
        /* background-size:50px; */
        border-radius:5px;
    }
    .body-d-b>img{
        width:50px;
    }
    /* .body-d-c{
        flex:1;
        background: #FFFFCC;
        border-radius:5px;
    } */
    .body-d-d{
        /* flex:1; */
        padding:10px;
        background: #FFFFCC;
        display:inline-block;
        font-size:20px;
        border-radius:4px; 
        /* overflow:hidden;  */
    }

    
</style>