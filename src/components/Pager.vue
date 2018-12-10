<template>
    <div class="pagelist">
        <a @click="jump(item)" :class="{'curPage': item == currPage}" v-for="item in pageList" :key="item">{{item}}</a>
    </div>
</template>

<script>
export default {
    props: ["total", "pageIndex", "pageSize", "change"],
    data: function () {
        return {
            pageList: [],
            currPage: this.pageIndex
        }
    },
    methods: {
        pagers: function () {
            this.pageList = [];
            console.log(this.total);
            console.log(this.currPage);
            var pages = Math.ceil(this.total / this.pageSize);
            for (var i = 1; i <= pages; i++) {
                this.pageList.push(i);
            }
        },
        jump: function (item) {
            this.currPage = item
            this.pagers();
            this.change(this.currPage);
        }
    },
    mounted: function () {
        this.pagers();
    },
    watch:{
        total:function(newValue){
            this.total = newValue;
            this.pagers();
        },
        pageSize: function(newValue){
            this.pageSize = newValue;
            this.pagers();
        }
    }
}
</script>
