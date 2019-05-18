<template>
	<view class="warp">
		<view class="box">
			<view class="title">默认效果</view>
			<t-table @change="change">
				<t-tr>
					<t-th>序号</t-th>
					<t-th>姓名</t-th>
					<t-th>年龄</t-th>
					<t-th>爱好</t-th>
				</t-tr>
				<t-tr v-for="item in tableList" :key="item.id">
					<t-td>{{ item.id + 1 }}</t-td>
					<t-td>{{ item.name }}</t-td>
					<t-td>{{ item.age }}</t-td>
					<t-td>{{ item.hobby }}</t-td>
				</t-tr>
			</t-table>
		</view>
		<view class="box">
			<view class="title">自定义样式</view>
			<t-table border="2" border-color="#95b99e" :is-check="true" @change="change">
				<t-tr font-size="14" color="#95b99e" align="left">
					<t-th align="left">姓名</t-th>
					<t-th align="left">年龄</t-th>
					<t-th align="left">爱好</t-th>
					<t-th align="center">操作</t-th>
				</t-tr>
				<t-tr font-size="12" color="#5d6f61" align="right" v-for="item in tableList" :key="item.id">
					<t-td align="left">{{ item.name }}</t-td>
					<t-td align="left">{{ item.age }}</t-td>
					<t-td align="left">{{ item.hobby }}</t-td>
					<t-td align="left"><button @click="edit(item)">编辑</button></t-td>
				</t-tr>
			</t-table>
		</view>
	</view>
</template>

<script>
	import tTable from '@/components/t-table/t-table.vue';
	import tTh from '@/components/t-table/t-th.vue';
	import tTr from '@/components/t-table/t-tr.vue';
	import tTd from '@/components/t-table/t-td.vue';
	export default {
		components: {
			tTable,
			tTh,
			tTr,
			tTd
		},
		data() {
			return {
				tableList: [{
						id: 0,
						name: '张三',
						age: '19',
						hobby: '游泳'
					},
					{
						id: 1,
						name: '李四',
						age: '21',
						hobby: '绘画'
					},
					{
						id: 2,
						name: '王二',
						age: '29',
						hobby: '滑板'
					},
					{
						id: 3,
						name: '码字',
						age: '20',
						hobby: '蹦极'
					}
				]
			};
		},
		methods: {
			change(e) {
				console.log(e.detail);
			},
			edit(item) {
				uni.showToast({
					title: item.name,
					icon: 'none'
				});
			}
		}
	};
</script>

<style>
	.title {
		font-size: 32upx;
		color: #666;
	}
	.box {
		margin: 20upx;
	}

	button {
		font-size: 24upx;
	}
</style>
