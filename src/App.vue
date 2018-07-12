<template>
  <div id="app">

    <div class="layout">
      <Layout>
        <Header>
          <Menu mode="horizontal" theme="dark" active-name="1">
            <div class="layout-logo"></div>
            <div class="layout-nav">
              <MenuItem name="1">
                <Icon type="ios-navigate"></Icon>
                个人中心
              </MenuItem>
              <MenuItem name="2">
                <Icon type="ios-keypad"></Icon>
                退出
              </MenuItem>
            </div>
          </Menu>
        </Header>
        <Layout>
          <Sider hide-trigger :style="{background: '#fff'}" ref="side1" hide-trigger collapsible :collapsed-width="80" v-model="isCollapsed">
            <Menu active-name="1-2" theme="light" width="auto" :open-names="['1']"  :class="menuitemClasses">
              <Submenu name="1" v-model="isCollapsed">
                <template slot="title">
                  <Icon type="ios-keypad"></Icon>
                  <span>Item 1</span>
                </template>
                <MenuItem name="1-1">
                  <Icon type="ios-navigate"></Icon>
                  <span>Option 1</span>
                </MenuItem>
                <MenuItem name="1-2">
                  <Icon type="ios-navigate"></Icon>
                  <span>Option 2</span>
                </MenuItem>
                <MenuItem name="1-3">
                  <Icon type="ios-navigate"></Icon>
                  <span>Option 3</span>
                </MenuItem>
              </Submenu>
            </Menu>
          </Sider>
          <Layout :style="{textAlign:'left'}">
            <Header :style="{padding: 0}" class="layout-header-bar">
              <Icon @click.native="collapsedSider" :class="rotateIcon" :style="{margin: '20px 20px 0'}" type="navicon-round" size="24"></Icon>
              <Breadcrumb :style="{margin: '24px 0', textAlign:'left'}">
                <BreadcrumbItem>Home</BreadcrumbItem>
                <BreadcrumbItem>Components</BreadcrumbItem>
                <BreadcrumbItem>Layout</BreadcrumbItem>
              </Breadcrumb>
            </Header>
            <Content :style="{padding: '24px', minHeight: '280px', background: '#fff'}">
              Content
              <router-view/>
            </Content>
          </Layout>
        </Layout>
      </Layout>
    </div>

  </div>
</template>

<script>
export default {
  name: 'App',
  data(){
    return {
      selectName:1,
      isCollapsed: false
    }
  },
  computed: {
    rotateIcon () {
      return [
        'menu-icon',
        this.isCollapsed ? 'rotate-icon' : ''
      ];
    },
    menuitemClasses () {
      return [
        'menu-item',
        this.isCollapsed ? 'collapsed-menu' : ''
      ]
    }
  },
  methods:{
    collapsedSider () {
      this.$refs.side1.toggleCollapse();
    },
    login(){
      this.$router.push({path:'/login'});
    },
    selected(name){
      this.$data.selectName = name;
      alert(this.$data.selectName);
    }
  }
}
</script>

<style scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /*margin-top: 60px;*/
}
.layout{
  border: 1px solid #d7dde4;
  background: #f5f7f9;
  position: relative;
  border-radius: 4px;
  overflow: hidden;
}
.layout-logo{
  width: 100px;
  height: 55px;
  /*background: #5b6270;*/
  background-image: url("assets/logo.png");
  background-repeat: no-repeat;
  background-size: 64px 64px;
  float: left;
  position: relative;
  top: 5px;
  left: 20px;
}
.layout-nav{
  width: 420px;
  margin: 0 auto;
}
.layout-header-bar{
  background: #fff;
  box-shadow: 0 1px 1px rgba(0,0,0,.1);
}
.layout-logo-left{
  width: 90%;
  height: 30px;
  background: #5b6270;
  border-radius: 3px;
  margin: 15px auto;
}
.menu-icon{
  transition: all .3s;
}
.rotate-icon{
  transform: rotate(-90deg);
}
.menu-item span{
  display: inline-block;
  overflow: hidden;
  width: 69px;
  text-overflow: ellipsis;
  white-space: nowrap;
  vertical-align: bottom;
  transition: width .2s ease .2s;
}
.menu-item i{
  transform: translateX(0px);
  transition: font-size .2s ease, transform .2s ease;
  vertical-align: middle;
  font-size: 16px;
}
.collapsed-menu span{
  width: 0px;
  transition: width .2s ease;
}
.collapsed-menu i{
  transform: translateX(5px);
  transition: font-size .2s ease .2s, transform .2s ease .2s;
  vertical-align: middle;
  font-size: 22px;
}
</style>
