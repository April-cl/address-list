<template>
	<view>
		<unicloud-db v-slot:default="{data, loading, error, options}" collection="contact" ref=udb>
			<view v-if="error">{{error.message}}</view>
			<view v-else>
				<uni-list>
					<uni-list-item v-for="item in data" :key="item.id" :title="item.name" :note="item.phone" @longpress.native="rmItem(item._id)" @click.native="updateFn(item)" link></uni-list-item>
				</uni-list>
			</view>
		</unicloud-db>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			rmItem(id) {
				this.$refs.udb.remove(id)
			},
			updateFn(item) {
				uni.navigateTo({
					url: '../update/update?item=' + JSON.stringify(item),
					success: res => {},
					fail: () => {},
					complete: () => {}
				})
			}
		}
	}
</script>

<style>

</style>
