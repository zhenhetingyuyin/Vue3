<template>
  <div>
    <el-aside width="200px">
      <el-menu class="el-menu-vertical-demo" background-color="#545c64" text-color="#fff" :collapse="false">
        <el-menu-item
          :index="item.path"
          v-for="item in Nochildren()"
          :key="item.path"
        >
          <component class="icons" :is="item.icon"></component>
          <span>{{ item.label }}</span>
        </el-menu-item>
        <el-sub-menu
          :index="item.label"
          v-for="item in Haschildren()"
          :key="item.path"
        >
          <template #title>
            <component class="icons" :is="item.icon"></component>
            <span>{{ item.label }}</span>
          </template>
          <el-menu-item-group>
            <el-menu-item
              :index="subItem.path"
              v-for="(subItem, subIndex) in item.children"
              :key="subIndex"
            >
              <component class="icons" :is="subItem.icon"></component>
              <span>{{ subItem.label }}</span>
            </el-menu-item>
          </el-menu-item-group>
        </el-sub-menu>
      </el-menu>
    </el-aside>
  </div>
</template>

<script>
export default {
  setup() {
    const list = [
      {
        path: "/user",
        name: "user",
        label: "用户管理",
        icon: "user",
        url: "UserManage/UserManage",
      },
      {
        label: "其他",
        icon: "location",
        path: "/other",
        children: [
          {
            path: "/page1",
            name: "page1",
            label: "页面1",
            icon: "setting",
            url: "Other/PageOne",
          },
          {
            path: "/page2",
            name: "page2",
            label: "页面2",
            icon: "setting",
            url: "Other/PageTwo",
          },
        ],
      },
    ];
    const Nochildren = () => {
      return list.filter((item) => !item.children);
    };
    const Haschildren = () => {
      return list.filter((item) => item.children);
    };
    return {
      Nochildren,
      Haschildren,
    };
  },
};
</script>

<style lang="scss" scoped>
.icons {
  width: 18px;
  height: 18px;
}
</style>