<template>
  <div class="menu">
    <template
      v-for="(item, index) in routes">
      <router-link :to="item.to" :key="item.name + index" class="menu-item" @click.native="changeActive(index)">{{item.name}}</router-link>
      <transition :key="index" name="fade">
      <div :key="index" class="menu-child" v-show="active === index">
        <router-link v-for="(child, index) in item.children" :key="child.name + index" :to="child.to" class="child">{{child.name}}</router-link>
      </div>
      </transition>
    </template>
  </div>
</template>

<script>
export default {
  name: 'leftMenu',
  data () {
    return {
      active: 0,
      routes: [
        {
          to: '/systemHome',
          name: '系统首页',
          children: [
            { to: '/systemHome/systemInfo', name: '系统信息' }
          ]
        },
        {
          to: '/systemSetting',
          name: '系统设置',
          children: [
            { to: '/systemSetting/ipAddr', name: 'IP地址' },
            { to: '/systemSetting/addrFilter', name: '地址过滤' },
            { to: '/systemSetting/userManage', name: '用户管理' },
            { to: '/systemSetting/snmp', name: 'snmp设置' },
            { to: '/systemSetting/mqtt', name: 'mqtt设置' }
          ]
        },
        {
          to: '/serialSetting',
          name: '串口设置',
          children: [
            { to: '/serialSetting/p1', name: 'P1' }
          ]
        },
        {
          to: '/workMode',
          name: '工作模式',
          children: [
            { to: '/workMode/p1', name: 'P1' }
          ]
        },
        {
          to: '/statusSearch',
          name: '状态查询',
          children: [
            { to: '/statusSearch/comParams', name: '串口通信参数' },
            { to: '/statusSearch/networkLink', name: '网络连接状态' },
            { to: '/statusSearch/serialCom', name: '串口通信状态' }
          ]
        },
        {
          to: '/deviceManage',
          name: '设备管理',
          children: [
            { to: '/deviceManage/firmwareUpdate', name: '固件升级' },
            { to: '/deviceManage/recovery', name: '恢复出厂' },
            { to: '/deviceManage/portReboot', name: '端口重启' },
            { to: '/deviceManage/systemReboot', name: '系统重启' }
          ]
        }
      ]
    }
  },
  methods: {
    changeActive (index) {
      console.log('nice')
      console.log(index)
      this.active = index
    }
  }
}
</script>

<style scoped lang='scss'>

  .fade-enter-active{
    transition: opacity 1s;
  }

  .fade-enter, .fade-leave-to{
    opacity: 0;
  }

  .menu{
    width: 180px;
    background-color: #161616;
    height: 100%;
    .menu-item{
      display: block;
      text-align: center;
      font-size: 14px;
      color: #6C6C6C;
      height: 30px;
      line-height: 30px;
      font-weight: bold;

      &.router-link-active, &.router-link-exact-active{
        background-color: #27D967;
        color: #FFFFFF !important;
      }

      &:hover{
        background-color: #27D967;
        color: #FFFFFF;
        transition: all linear .2s;
      }
    }
    .menu-child{
      a.child{
        display: block;
        width: 100%;
        text-align: center;
        color: #ccc;
        height: 25px;
        line-height: 25px;

        &:hover{
          background-color: rebeccapurple;
        }

      &.router-link-active, &.router-link-exact-active{
          background-color: rebeccapurple;
        }
      }
    }
  }
</style>
