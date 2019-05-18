<script>
export default {
	onLaunch: function() {
		console.log('App Launch');
	},
	onShow: function() {
		console.log('App Show');
	},
	onHide: function() {
		console.log('App Hide');
	}
};
</script>

<style>
/*每个页面公共css */
page {
}
.h-wrapper-bg {
	position: fixed;
	top: 0;
	bottom: 0;
	width: 100%;
	box-sizing: border-box;
	z-index: -1;
}
.h-wrapper-bg image {
	width: 100%;
	height: 100%;
}
</style>
