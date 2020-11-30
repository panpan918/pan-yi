<template>
    <div>
        <div class="left-head">
            <div class=left-port></div>
            <div class="left-body">
                <div class="left-body-a" @click="chat">
                    <img src="../assets/bn2.png" alt="">
                </div>
                <div class="left-body-b" @click="state">
                    <img src="../assets/bn3.png" alt="">
                </div>
                <div class="left-body-c" @click="introduce">
                    <img src="../assets/bn4.png" alt="">
                </div>
            </div>
        </div>
        <div class="left-body-base" :style="{display:stated}">
            <div class="lbody-a">设置</div>   
            <div class="lbody-b">
                <div class="b-left">
                    <img src="../assets/bn1.jpg" alt="">
                </div>
                <div class="b-right">
                    <div class="b-right-a">账号</div>
                    <div class="b-right-b">IP地址</div>
                    <div class="b-right-c">{{times}}</div>
                </div>    
            </div>
            <div class="foot">
                <div class="foot-a">
                    <input type="checkbox">
                    <span>消息声音</span>
                </div>
                <div class="foot-b">
                    <input type="checkbox">
                    <span>显示昵称</span>
                </div>
                <div class="foot-c">
                    <input type="checkbox">
                    <span>消息时间</span>    
                </div> 
            </div>
        </div>
        <div class="sets" :style="{display:states}">
            <div class="sets-a">关于</div>
            <div class="sets-b">
                <div>版本: v1.0</div>
                <div>协议:MIT</div>
                <div>作者:Mr.pan</div>
                <div>邮箱:88171800@qq.com</div>
                <div>仓库:</div>
                <div>^.^</div>
            </div>
        </div>

    </div>
</template>
<script>
export default {
    data(){
        return{
            stated:"none",
            states:"none",
            times:""
        }
    },
    methods:{
        state(){
            this.stated="block";
            this.states="none";
        },
        introduce(){
            this.stated="none";
            this.states="block";
        },
        chat(){
            this.stated="none";
            this.states="none";
        }
    },
    mounted:function(){
        this.times=new Date().toLocaleString();
    }
}
</script>
<style scoped>
    .left-head{
        width:60px;
        height:600px;
        background:#26292e;
    }
    .left-port{
        width:60px;
        height:60px;
        background:url('../assets/bn1.jpg');
        background-size: 40px 40px;
        background-repeat: no-repeat;
        background-position:center center;
        cursor:pointer;
    }
    .left-body>div{
        width:60px;
        height:40px;
        display:flex;
        justify-content:center;
        align-items:center;
        margin-top:10px;
    }
    .left-body>div>img{
        width:28px;
        cursor:pointer;
    }
    .left-body>div>img:hover{
        background:#b2e281;
    } 
    .left-body-base{
        width:680px;
        height:600px;
        background: #CCFFFF;
        position:absolute;
        top:58px;
        left:118px;
        /* display:none; */
        z-index:999;
    }
    .lbody-a{
        width:640px;
        height:30px;
        font-size:20px;
        font-family: "微软雅黑";
        font-weight:bolder;
        margin:10px auto;
    }
    .lbody-b{
        width:640px;
        height:70px;
        margin:0 auto;
        display:flex;
    }
    .b-left{
        width:70px;
        height:70px;
    }
    .b-right{
        height:70px;
        flex:1;
    }
    .b-left>img{
        width:70px;
    }
    .b-right>div{
        margin-left:10px;
        font-size:15px;
    }
    .b-right-a{
        height:20px;
        line-height:30px;
    }
    .b-right-b{
        height:20px;
        line-height:35px;
    }
    .b-right-c{
        height:30px;
        line-height:40px;
    }
    .foot{
        width:640px;
        margin-left:15px;
        margin-top:10px;
    }
    .foot>div{
        height:30px;
        margin-top:5px;
        line-height:30px;
        border-bottom:1px solid white;
    }
    .sets{
        width:680px;
        height:600px;
        background: #CCFFFF;
        position:absolute;
        top:58px;
        left:118px;
        /* display:none; */
        z-index:999;
    }
    .sets-a{
        width:640px;
        height:30px;
        font-size:20px;
        font-family: "微软雅黑";
        font-weight:bolder;
        margin:10px auto;
    }
    .sets-b{
        width:580px;
        height:300px;
        margin-top:30px;
        margin-left:40px;
    }
    .sets-b>div{
        height:49px;
        border-bottom:1px solid white;
        font-size:15px;
        line-height:75px;
    }

</style>