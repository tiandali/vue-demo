

<template>
  <el-menu
    default-active="search"
    router="true"
    class="el-menu-demo"
    mode="horizontal"
    @select="handleSelect"
    background-color="#0F1629"
    text-color="#fff"
    active-text-color="#DAF2F6"
  >
    <template v-for="menu in menus">
      <el-submenu v-bind:key="menu.name" v-if="menu.children" :index="menu.path">
        <template slot="title">
          <!-- <i class="el-icon-location"></i> -->
          <i :class="menu.iconStyle"></i>
          <span>{{menu.name}}</span>
        </template>
        <template v-for="menuson in menu.children">
          <el-submenu v-bind:key="menuson.name" v-if="menuson.children " :index="menuson.path">
            <!-- 此处是菜单级到第三层，暂时不写 -->
          </el-submenu>
          <el-menu-item v-bind:key="menuson.name" v-else :index="menuson.path">
            <span slot="title">{{menuson.name}}</span>
          </el-menu-item>
        </template>
      </el-submenu>
      <el-menu-item v-bind:key="menu.name" v-else :index="menu.path">
        <template slot="title">
          <!-- <i class="el-icon-location"></i> -->
          <i :class="menu.iconStyle"></i>
          <span>{{menu.name}}</span>
        </template>
      </el-menu-item>
    </template>
  </el-menu>
</template>
<script>
import { menus } from "../../router/menus";
console.log("menus: ", menus);
export default {
  name: "MenuBar",
  data() {
    return {
      menus
    };
  },
  created() {},
  methods: {
    handleSelect(key, keyPath) {
      console.log(key, keyPath);
    }
  }
};
</script>
<style lang="scss">
.el-menu-demo {
  display: flex;
  height: 80px;
  align-items: center;

  .el-menu-item {
    display: flex;
    height: 80px;
    align-items: center;
    padding: 0 40px;
    border-top: 2px solid transparent;
    border-bottom: 2px solid transparent;
    i {
      margin-right: 8px;
    }
  }
  .is-active {
    border-top: 2px solid #13c6e2;
    border-bottom-color: transparent !important;
  }
}
</style>