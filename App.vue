<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	@import './common/uni.css';
	@import './common/iconfont/iconfont.css';
	@import './common/animate.min.css';
  .c_flex {
    display: flex;
  }
  .c_flex_j_sb{
    justify-content: space-between;
  }
  .c_flex_a_c{
    align-items: center; 
  }
  .c_flex_j_c{
    justify-content: center;
  }
</style>
