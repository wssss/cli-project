<template>
    <article>
        <aside>
            <div class="l_box">
                <div class="search">
                    <form id="searchform">
                        <input class="input_text" v-model="params.title" type="text">
                        <input class="input_submit" value="搜索" type="submit" @click.prevent="search()">
            </form>
                </div>
                <div class="fenlei">
                    <h2>文章分类</h2>
                    <ul>
                        <li><a @click="SelectType()">学无止境（33）</a></li>
                        <li><a >日记（19）</a></li>
                        <li><a >慢生活（520）</a></li>
                        <li><a >美文欣赏（40）</a></li>
                    </ul>
                </div>
                <div class="tuijian">
                    <h2>站长推荐</h2>
                    <ul>
                        <li><a href="/">你是什么人便会遇上什么人</a></li>
                        <li><a href="/">帝国cms 列表页调用子栏目，没有则不显示栏目名称</a></li>
                        <li><a href="/">第二届 优秀个人博客模板比赛参选活动</a></li>
                        <li><a href="/">个人博客模板《绅士》后台管理</a></li>
                        <li><a href="/">你是什么人便会遇上什么人</a></li>
                        <li><a href="/">帝国cms 列表页调用子栏目，没有则不显示栏目名称</a></li>
                        <li><a href="/">第二届 优秀个人博客模板比赛参选活动</a></li>
                        <li><a href="/">个人博客模板《绅士》后台管理</a></li>
                    </ul>
                </div>
                <div class="tuijian">
                    <h2>点击排行</h2>
                    <ul>
                        <li><a href="/">你是什么人便会遇上什么人</a></li>
                        <li><a href="/">帝国cms 列表页调用子栏目，没有则不显示栏目名称</a></li>
                        <li><a href="/">第二届 优秀个人博客模板比赛参选活动</a></li>
                        <li><a href="/">个人博客模板《绅士》后台管理</a></li>
                        <li><a href="/">你是什么人便会遇上什么人</a></li>
                        <li><a href="/">帝国cms 列表页调用子栏目，没有则不显示栏目名称</a></li>
                        <li><a href="/">第二届 优秀个人博客模板比赛参选活动</a></li>
                        <li><a href="/">个人博客模板《绅士》后台管理</a></li>
                    </ul>
                </div>
                <div class="cloud">
                    <h2>标签云</h2>
                    <ul>
                        <a href="/">陌上花开</a> <a href="/">校园生活</a> <a href="/">html5</a> <a href="/">SumSung</a> <a href="/">青春</a>
                        <a href="/">温暖</a> <a href="/">阳光</a> <a href="/">三星</a><a href="/">索尼</a> <a href="/">华维荣耀</a> <a href="/">三星</a>
                        <a href="/">索尼</a>
                    </ul>
                </div>
                <div class="guanzhu">
                    <h2>关注我 么么哒</h2>
                    <ul>
                        <img src="images/wx.jpg">
            </ul>
                </div>
            </div>
        </aside>
        <div class="r_box">
            <main>
                <li v-for="item in list" :key="item.Id">
                    <i><a href="/"><img src="images/1.jpg"></a></i>
                    <h3><a href="/">{{ item.Title }}</a></h3>
                    <p>{{ item.SimpleInfo }}</p>
                </li>
                <pager :total="params.total" :page-size="params.limit" :change="pageChange" :page-index="params.page"></pager>
            </main>
        </div>
    </article>

</template>

<script>
import axios from 'axios';
import Pager from "../components/Pager.vue";
export default {
    data: function () {
        return {
            list:[],
            params: {
                title: this.$route.query.title||"",
                type: "",
                limit:10,
                page:1
            }
        }
    },
    components: {
        Pager
    },
    methods: {
        pageChange: function (item) {
            console.log(item)
        },
        search: function () {
            console.log("sss")
            this.getData();
        },
        getData: function () {
            var _this = this;
            axios.get("http://localhost:64786/Back/Article/Search", {
                params: this.params
            })
            .then(function (res) {
                _this.list = res.data.data;
                _this.params.total = res.data.count;
            });
        },
        SelectType: function (type) {
            this.params.type = type;
            this.getData();
        }
    },
    created: function () {
        this.getData();
    }
}
</script>
