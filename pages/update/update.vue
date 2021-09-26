<template>
	<view>
		<uni-easyinput v-model="item.name" placeholder="name"></uni-easyinput>
		<uni-easyinput v-model="item.phone" placeholder="phone"></uni-easyinput>
		<button type="default" @click="submit">提交</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				item: {
					"_id": "",
					"name": "",
					"phone": ""
				}
			}
		},
		onLoad({item}) {
			console.log(item)
			this.item = JSON.parse(item)
		},
		methods: {
			submit() {
				const db = uniCloud.database()
				let item = {...this.item}
				delete item._id
				db.collection('contact').doc(this.item._id).update(item).then( e => {
					console.log(e)
				})
			}
		}
	}
</script>

<style>

</style>
