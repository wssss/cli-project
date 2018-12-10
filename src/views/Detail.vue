<template>
    <div class="about">
        <h1>This is an Detail page</h1>

        <h2>{{ title }}</h2>
    </div>
</template>

<script>

export default {
    data: function() {
        return {
            title: "This is an Detail Page"
        };
    },
    mounted:function(){
		//使用axios发送一个get请求。
        console.log(this.$route.params.id)
    }
};
</script>