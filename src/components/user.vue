<template>
  <div>
    <group :title="('权限设置')">
      <x-switch :title="('信息推送')" :value-map="['0', '1']" v-model="stringValue"></x-switch>
      <group :title="value[0] + ' ' + value[1] + ':' + value[2]">
      <datetime-range :title="('推送时间设置')" start-date="2017-01-01" end-date="2017-02-02" format="YYYY-MM-DD" v-model="value"></datetime-range>
    </group>
    </group>
    <group :title="('隐私设置')">
      <x-switch :title="('共享我的位置信息')"></x-switch>
      <x-switch :title="('读书圈好友可见')" v-model="value1"></x-switch>
    </group>
    <group :title="('系统默认设置')">
      <x-switch :title="('我的图书馆')" disabled></x-switch>
      <x-switch :title="('个人借阅信息更新')" :value="true" disabled></x-switch>
    </group>
    <group :title="('外部设置')">
      <x-switch :title="('自动延期')" prevent-default v-model="value2"></x-switch>
    </group>
    <group :title="('设备')">
      <x-switch disabled :title="('铃声')"></x-switch>
    </group>
  </div>
</template>

<script>
import { XSwitch, Group, Cell, DatetimeRange } from 'vux'

export default {
  components: {
    XSwitch,
    Group,
    Cell,
    DatetimeRange
  },
  methods: {
    // onClick (newVal, oldVal) {
    //   console.log(newVal, oldVal)
    //   this.$vux.loading.show({
    //     text: 'in processing'
    //   })
    //   setTimeout(() => {
    //     this.$vux.loading.hide()
    //     this.value2 = newVal
    //   }, 1000)
    // }
  },
  data () {
    return {
      value1: true,
      value2: false,
      stringValue: '1',
      value: ['2019-03-13', '03', '05']
    }
  }
}
</script>