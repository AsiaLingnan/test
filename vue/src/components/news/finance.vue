<template>
	<main>
		<ul class="headlineul">
			<li v-for="v in list">
				<div>
					<h2>{{v.title}}</h2>
					<ol>
						<li>{{v.replyCount}}人浏览</li>
						<li>{{v.mtime | time}}</li>
						<li>来源：{{v.source}}</li>
					</ol>
				</div>
				<img :src="v.imgsrc" alt="" />
			</li>
			<li><p>无更多内容</p></li>
		</ul>
		
	</main>
</template>

<script>
	export default{
		data(){
			return{
				list:[]
			}
		},
		mounted(){
			this.$http.get("./src/static/finance.json").then(function(res){
				this.list=res.body.T1348648756099
				
			})
		},
		filters:{
			time(n){
				n=n.split(' ');
				return n[0];
			}
		}
	}
</script>

<style scoped="">
	
</style>