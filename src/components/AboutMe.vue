<template>
    <div class="about_me">
        <h2>关于我</h2>
        <ul>
            <i><img src="images/4.jpg"></i>
            <p><b>杨青</b>{{ user.SelfSlogo }}</p>
        </ul>
    </div>
</template>

<script>
import axios from "axios";
export default{
    data:function(){
        return {
            user:{
                
            }
        }
    },
    created:function(){
        this.getUserInfo();
    },
    methods:{
        getUserInfo:function(){
            var _this = this;
            axios.get("http://localhost:64786/api/UserInfo")
            .then(function(res){
                _this.user = res.data;
                console.log(_this.user)
            })
        }
    }
}
</script>
