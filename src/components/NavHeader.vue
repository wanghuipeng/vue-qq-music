<template>
  <div>
    <header id="header">
        <img src="../assets/logo.png" alt="qq音乐" id="logo">
        <a href="javascript:;" class="btn_download">下载APP</a>
    </header>
    <nav class="navbar">
        <ul class="nav-list">
            <li class="nav-item" 
            v-for="(list) in navConfig" 
            :key="list.key"><router-link :to="list.href" tag="li" exact-active-class="active">{{list.name}}</router-link></li>
        </ul>
    </nav>
  </div>
</template>


<script lang="ts">
import Vue from 'vue';
import Component from 'vue-class-component';

@Component
export default class NavHeader extends Vue {
    navConfig = [
        {
            name: '推荐',
            key: 0,
            href: '/'
        },
        {
            name: '排行榜',
            key: 1,
            href: '/rank'
        },
        {
            name: '搜索',
            key: 2,
            href: '/search'
        }
    ];
}
</script>


<style lang="scss" scoped>
@import '../style/_var';

#header {
    display: flex;
    align-items: center;
    position: relative;
    height: $header-height;
    background: $header-background;
    #logo {
        height: $logo-height;
        margin-left: 10px;
    }
    .btn_download {
        position: absolute;
        right: 10px;
        height: 28px;
        line-height: 28px;
        font-size: 14px;
        padding: 0 12px;
        background: #149c5a;
        color: #fff;
        border-radius: 99px;
    }
}

.navbar {
    background: #fff;
    .nav-list {
        display: flex;
        align-items: center;
        .nav-item {
            text-align: center;
            flex: 1;
            position: relative;
            color: $nav-item-color;
            height: $nav-item-height;
            line-height: $nav-item-height;
            & .active {
                color: $nav-item-active;
                &:after {
                    position: absolute;
                    display: block;
                    content: '';
                    bottom: 0;
                    left: 0;
                    right: 0;
                    height: 2px;
                    background-color: $nav-item-active;
                }
            }
        }
    }
}

</style>