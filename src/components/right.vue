<template>
    <div>
         <div class="right-body" v-show="may">
            <img src="../assets/emoji.png" alt="">
        </div>
        <div class="right-body-a" v-show="mays">
            <div class="right-body-b">
                <div class="body-b-a">
                    <img :src="imgUrl"/>
                </div>
                <div class="body-b-b">{{user}}</div>
            </div>
            <div class="body-c" id="box">
                <div class="body-d" v-for="(item,index) in arrList" :key="index">                  
                    <div class="body-d-b">
                        <img :src="item.imageUrl">
                    </div>
                    
                    <div class="body-d-d">{{item.message}}</div>                       
                    
                </div>
            </div>
            <div class="body-c-a">
                <input type="file" ref="filElem" class="body-c-b" id="body-c-b" multiple/>
                <div class="body-c-c" @click="filed"></div>
            </div>
            <textarea  class="body-c-d" placeholder="请输入信息" v-model="inputCont"></textarea>
            <div class="body-c-e" @click="sent()">发送</div> 
        </div>
    </div>
</template>
<script>
import bus from '@/event/eventBus.js'
    export default {
        data(){
            return{
                arrList:[
                {imageUrl:require("../assets/bn1.jpg"),message:"123"}
            ],
            user:"",
            mays:false,
            may:true,
            inputCont:"",
            imgUrl:""
            }
        },
        mounted(){
            bus.$on('halo',(m,n,imgUrl) => {this.mays=m;this.may=!m;this.user=n;this.imgUrl=imgUrl;this.arrList=[];});
        },
        methods:{
            sent:function(){
                this.arrList.push({imageUrl:require("../assets/bn1.jpg"),message:this.inputCont});
                this.inputCont="";
            },
        
        filed:function(){
            this.$refs.filElem.dispatchEvent(new MouseEvent('click'));
        },
        }
    }
</script>
<style scoped>
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
        /* background: url("../assets/user1.png");
        background-size:45px; */
        border-radius:4px;
        margin-top:2px;
    }
    .body-b-a > img{
     width:45px;   
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
