### t-table 表格


`table` 表格基本使用组件，让你制作简单表格只需要专注内容，而不用过度专注样式。

此组件基本全平台支持。（支付宝，百度，头条小程序理论上都支持，但是没有很细致的测试这几个平台）

[github 地址： https://github.com/mehaotian/t-table](https://github.com/mehaotian/t-table)         
[插件市场地址：http://ext.dcloud.net.cn/plugin?id=413](http://ext.dcloud.net.cn/plugin?id=413)
**功能亮点**
- 自定义全局表格样式
- 自定义局部表格样式
- 表格内容自定义
- 表格多选

**未实现**
- 合并单元格
- 调整列宽，行高

**效果演示**
![WX20190518-141534@2x.png](https://upload-images.jianshu.io/upload_images/4472817-5c26e7b529fc5461.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 调用方式

```html
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

```


### t-table
表格父组件，仅包含 `tr` 组件

**属性说明**

|  属性名		|    类型	| 默认值	| 说明									|
| ---			| ---		| ---		| ---									|
| border		| String	| 1			| 边框粗细								|
| border-color	| Color		| #d0dee5	| 边框颜色								|
| is-check		| Boolean	| false		| 是否开启列多选						|
| @change		|function	|			|开启多选生效，返回值 event = [0,1,2]	|

### t-tr
表格行组件 仅包含 `th`,`td` 组件

**属性说明**

|  属性名	|    类型	| 默认值	| 说明			|
| ---		| ---		| ---		| ---			|
| font-size	| String	| 15		|  行字体大小	|
| color		| Color		| #3b4246	|  行字体颜色	|
| align	| String	| center		|  行字体对其方式，可取值：'left' 左对齐;'center' 居中对齐;'right' 右对齐;	|

### t-th
表格内的表头单元格组件

**属性说明**

|  属性名	|    类型	| 默认值| 说明	|
| ---		| ---		| ---	| ---	|
| align	| String	| center		|  行字体对其方式，可取值：'left' 左对齐;'center' 居中对齐;'right' 右对齐;	|

### t-td
表格中的标准单元格组件

**属性说明**

|  属性名	|    类型	| 默认值| 说明	|
| ---		| ---		| ---	| ---	|
| align	| String	| center		|  行字体对其方式，可取值：'left' 左对齐;'center' 居中对齐;'right' 右对齐;	|


**Tips**
- 不提供定制，仅有这些简单内容
- 如需更复杂表格，参考源码逻辑，可自行扩展
- 不建议加载过多数据，如到一定数据，比如 10 条，建议制作翻页


### 更新日志

#### v1.0.0
- 初次提交