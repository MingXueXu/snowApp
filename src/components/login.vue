<template>
    <div>
    <group title="登陆页面">
      <x-input title="姓名" name="username" placeholder="请输入姓名" is-type="china-name"></x-input>
    </group>

    <group title="">
      <x-input title="手机号码" name="mobile" placeholder="请输入手机号码" keyboard="number" is-type="china-mobile"></x-input>
    </group>

    <group title="">
      <x-input title="邮箱" name="email" placeholder="请输入邮箱地址" is-type="email"></x-input>
    </group>
     <group title="">
      <x-input title="密码" placeholder="请输入密码" type="password"></x-input>
    </group>
     <x-button @click.native="Login" type="primary">登陆</x-button>
    </div>
</template>
<script>
import { XInput, Group, XButton, Cell } from 'vux'
export default {
  components: {
    XInput,
    XButton,
    Group,
    Cell
  },
  methods:{
     Login(){
         this.$router.push('/')
     }
  }
}
</script>

