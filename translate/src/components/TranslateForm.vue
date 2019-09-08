<template>
  <div class="row" id="translataForm">
	<div class="col-md-6 col-md-offset-3">
		<form id="transform" class="well form-inline" v-on:submit="formSubmit">
			<input class="form-control" type="text" v-model="textToTranslate" placeholder="请输入需要翻译的内容">
			<select class="foem-control">
				<option value="en">English</option>
				<option value="ko">korena</option>
				<option value="ja">Janpenese</option>
				<option value="ru">Russian</option>
			</select>
			<input class="btn btn-primary" type="submit" value="翻译">
		</form>
	</div>
		
  </div>
</template>

<script>

export default {
  name: 'translataForm',
  data() {
	  return {
		   textToTranslate:""
	  }
  },
  methods: {
	  formSubmit:function(e){
		  //alert(this.textToTranslate);
		  this.$emit("formSubmit",this.textToTranslate,this.language);
		  e.preventDefault();
	  }
  },
  created() {
	  this.language = "en";
  },
}
</script>

<style>
#transform{
	border-radius: 10px;
	border: 1px #ccc solid;
}
</style>
