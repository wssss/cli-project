<template>
	<div id="app">
		<header class="header-navigation" id="header">
            <nav><div class="logo"><a href="/">杨青个人博客</a></div>
                <h2 id="mnavh"><span class="navicon"></span></h2>
                <ul id="starlist">
                <li><router-link to="/">网站首页</router-link> </li>
                <li><router-link to="/gallery">我的相册</router-link> </li>
                <li><router-link to="/list">我的日记</router-link> </li>
                <li><router-link to="/about">关于我</router-link> </li>
                </ul>
            </nav>
		</header>
		<router-view/>
	</div>
</template>

<style>
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;

    color: #2c3e50;
}
.header-block{
    height: 60px;
}

#nav {
    padding: 30px;
}

#nav a {
    font-weight: bold;
    color: #2c3e50;
}

#nav a.router-link-exact-active {
    color: #42b983;
}
</style>
