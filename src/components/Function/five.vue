<template>
	<div>
		<Modal id="one" :fullscreen="fullscreen" v-model="isFiveViewBool" footer-hide :draggable="draggable" :closable="false" >
			<div slot="header" style="width: 100%;display: flex;align-items: center;justify-content:space-between;">
				<div style="width: 50%;display: flex;align-items: center;">
					<Icon size="25" :type="menu.icon" style="margin: 0.5rem;" />
					<span style="color: white;"><b>{{menu.menuName}}</b></span>
				</div>
				<div style="width: 90px;display: flex;align-items: center;justify-content: space-between">
					<Button size="large" type="text" ghost @click="mini()" icon="md-remove"></Button>
					<Button size="large" type="text" ghost v-show="!fullscreen" @click="big()" icon="ios-expand"></Button>
					<Button size="large" type="text" ghost v-show="fullscreen" @click="small()" icon="md-expand"></Button>
					<Button size="large" type="text" ghost @click="closeView()" icon="md-close"></Button>
				</div>
			</div>
			<div>有多少人在为了它而奋斗</div>
		</Modal>
	</div>
</template>

<script>
	export default {
		name: "five",
		props: {
			menu: '',
		},
		data() {
			return {
				//全屏
				fullscreen:false,
				//移动
				draggable:true,
			}
		},
		computed: {
			//判断是否展示该面板
			isFiveViewBool: {
				get() {
					return this.$store.state.control.fiveViewBool;
				},
				set(v) {
					this.$store.commit("setFalseFiveVB");
				}
			}
		},
		methods: {
			//关闭对话框
			closeView(){
				this.$store.commit("setFalseFiveVB");
				this.$store.commit("deleteTaskList",this.menu);
			},
			//缩小对话框
			small(){
				this.fullscreen=false
				this.draggable=true
			},
			//放大对话框
			big(){
				this.fullscreen=true
				this.draggable=false
			},
			//最小化
			mini(){
				this.$store.commit("setFalseFiveVB");
			}

		},
		mounted() {}
	}
</script>

<style scoped="scoped">
</style>
<style>
#noAssessmentDate .ivu-modal-body {
	margin-bottom: 2.5rem;
}
#one .ivu-modal-header {
	background-color:#348DC1; 
	padding: 5px;
}
</style>

