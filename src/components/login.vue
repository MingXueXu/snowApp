<template>
    <div>
    <group title="登陆页面">
      <x-input title="姓名" name="username" placeholder="请输入姓名" is-type="china-name"></x-input>
    </group>

    <group title="">
      <x-input title="手机号码" name="mobile" mask="999 9999 9999" placeholder="请输入手机号码" keyboard="number" is-type="china-mobile" v-model="phone"></x-input>
    </group>

    <group title="">
      <x-input title="邮箱" name="email" placeholder="请输入邮箱地址" is-type="email"></x-input>
    </group>
     <group title="">
      <x-input title="密码" placeholder="请输入密码" type="password" v-model="password"></x-input>
    </group>
     <x-button @click.native="Login" type="primary">登陆</x-button>
    </div>
</template>
<script>
import { XInput, Group, XButton, Cell,  AlertModule, Alert} from 'vux'
export default {
  components: {
    Alert,
    XInput,
    XButton,
    Group,
    Cell
  },
  methods:{
     Login(){
         if(this.password==='123'){
         this.$router.push('/')}
         else{ AlertModule.show({
          title: '登陆失败',
          content: '密码错误'
          })
     }
  }
},
 data(){
      return {
        phone:'17771581136',
        password:''
      }
  }
}
</script>

