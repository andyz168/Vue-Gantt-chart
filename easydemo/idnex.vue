<template>
  <v-gantt-chart :startTime="startTime"
           :endTime="endTime"
           :datas="datas">
      <template v-slot:block="{data,item}">
        <!-- 你的容器块组件 -->
        <Test :data="data" :item="item"></Test>
      </template>
      <template v-slot:left="{data}">
        <!-- 你的行名组件 -->
        <TestLeft :data="data"></TestLeft>
      </template>
      <template v-slot:title>
        <!-- 你的表头组件 -->
        hola
      </template>
    </v-gantt-chart>
</template>

<script>
	import Test from "./test.vue"; //你自己的gantt条容器
	import TestLeft from "./test-left.vue"; //你自己的行名称组件
	import { mockDatas } from "@src/mock/index.js"; //伪造的数据
	import dayjs from "dayjs" //时间库
	
	export default {
	  name: "App",
	  components: { Test, TestLeft },
	  data() {
	    return {
	      startTime: dayjs().toString(),//时间轴开始时间
	      endTime: dayjs() 
	        .add(2, "d")
	        .add(2, "h")
	        .add(5, "s").toString(), //时间结束时间
	      datas: mockDatas(100), // gantt数据
	    };
	  },
	};
</script>

<style>
</style>
