<template>
	<!--这里将来要做slot增强其扩展性-->
<!--新增的弹出-->
<div class="modal fade"  id="addModal" tabindex="-1" role="dialog" aria-labelledby="myModalLabel" aria-hidden="true" onscroll="true">
  <div class="modal-dialog" style="width: 70%;">
    <div class="modal-content">
      <div class="modal-header">
        <button type="button" class="close" style="margin-right: 5px;" data-dismiss="modal"><span aria-hidden="true">&times;</span><span class="sr-only">Close</span></button>
        <h4 class="modal-title" id="myModalLabel"><span style="font-size: 14px;display: block;margin-bottom: 7px;margin-left: 50%">新增</span></h4>
      </div>
      <div class="modal-body col-lg-12">
           	<!--form表单-->
           	<form class="form-horizontal" id="form">
          		<form_temp :inputs="inputs" :width="width" :values="values2"></form_temp>                             		
           	</form>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-default1" data-dismiss="modal">关闭</button>
        <button type="button" class="btn btn-info" id="save" @click="saved">保存</button>
      </div>
    </div>
  </div>
</div>

</template>
<script>
	import form_temp from '../components/new/form'
	import data from '../json/form'
	var maolFormData = [{
  			name:"buyerId",
  			label:"间接客户编号",
  			type:'text',
        button:{
          id:'button',
          text:'查询'
        }
  		},
  		{
  			name:"invNo",
  			label:"应收账款凭证编号",
  			type:'text'
  		},{
  			name:"invCcy",
  			label:"币别",
  			type:'text'
  		},
  		{
  			name:"invAmt",
  			label:"应收账款金额",
  			type:'text'
  		},
  		{
  			name:"invValDt",
  			label:"应收账款起算日",
  			type:'text'
  		},
  		{
  			name:"invDt",
  			label:"应收账款开立日期",
  			type:'text'
  		},{
  			name:"invDueDt",
  			label:'应收账款到期日',
  			type:"text"
  		},{
			name:"acctPeriod",
  			label:'账期',
  			type:"text"
  		},{
			name:"sysRefNo",
  			label:'',
  			type:"hidden"
  		},{
			name:"selId",
  			label:'',
  			type:"hidden"
  		},{
			name:"invLoanAval",
  			label:'',
  			type:"hidden"
  		}]	

	export default{
		name:'modal',
		components:{
			form_temp
		},
		props:{
			save:Function,
			values:Object
		},
		computed:{
		},
		methods:{
			saved:function(){
				debugger
				this.save(this);
				$('#addModal').modal('hide');
			}
		},
		watcher:{
			values2:function(){
				debugger
				this.values2
			}
		},
		data(){
			return{
				inputs:maolFormData,
				width:'4',
				values2:this.values
				
			}
		}
	}
</script>