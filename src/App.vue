<template>
	<div class="app-container">
			<el-button @click="dialog = true">打开表单</el-button>
			<!-- 表单 -->
			<el-dialog-form :visible.sync="dialog" title="表单标题" width="500px" :items="items" :form="form"
				@submit="onSubmit">
			</el-dialog-form>
			<div class="renwu">
				<div>{{input}}</div>
				<div>{{switch2}}</div>
				<div>{{timePicker}}</div>
				<div>{{radioGroup}}</div>
			
				<div>{{select}}</div>
				<div>{{checkbox}}</div>
			</div>
	</div>
</template>

<script>
	import elDialogForm from 'el-dialog-form'
		export default {
			components: {
				elDialogForm
			},
			data() {
						return {
							input: undefined,
							switch2:undefined,
							timePicker:undefined,
							radioGroup:undefined,
					
							select:undefined,
							checkbox:undefined,
							form: {
								input: '',
								switch:false,
								timePicker:'',
						
								radioGroup:1,
							
								select:[],
								checkbox:true
							},
							dialog: false,
							items: [
								{
									type: 'input',
									label: '任务',
									prop: 'input',
									rules: [{
										required: true,
										message: "请输入任务",
										trigger: 'blur'
									}],
									attrs:{
										placeholder:'请输入任务'
									},
									on: {
										blur: (e) => {
											console.log(e);
										}
									},
								},
								
								{
									type: 'time-picker',
									label: '时间选择',
									prop: 'timePicker',
									on: {
										
									}
								},
								{
									type: 'radio-group',
									label: '单选框组',
									prop: 'radioGroup',
									tip:'注意别勾选错误',
									options:[
										{
											label:'购买',
											value:'购买'
										},
										{
											label:'取消',
											value:'取消'
										}
									],
									on:{
										change:(e)=>{
											console.log('-----------');
											console.log(e);
										}
									}
								},
								{
									type: 'select',
									label: '下拉选择',
									prop: 'select',
									options:[
										{
											label:'退货',
											value:'退货'
										},
										{
											label:'换购',
											value:'换购'
										}
									],
									attrs:{
										placeholder:'请输入售后服务'
									},
									on:{
										change:(e)=>{
											console.log('-----------');
											console.log(e);
										}
									}
								},
								{
									type: 'checkbox',
									label: '选择',
									prop: 'checkbox',
									attrs:{
										label:"我同意"
									},
									on:{
										change:(e)=>{
											console.log('-----------');
											console.log(e);
										}
									}
								},
							]
						}
					},
			methods: {
				onSubmit(form) {
					this.input = form.input
					this.inputNumber = form.inputNumber
					this.switch2=form.switch2
					this.timePicker=form.timePicker
					this.datePicker=form.datePicker
					this.radioGroup=form.radioGroup
					this.checkboxGroup=form.checkboxGroup
					this.select=form.select
					this.checkbox=form.checkbox
					console.log(form);
				}
			},
		}
</script>

<style>
.renwu{
	width: 400px;
	height: 400px;
	border:1px solid #000;
}
</style>
