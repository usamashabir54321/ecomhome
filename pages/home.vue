<template>
	<div id="ecom_home_id" class="container">

		<div 
			v-for="(cat , index) in cattsArr" 
			:key="index" 
			class="product" 
			:class="[slectCard == index ? 'flip_card' : '']"
			@mouseenter="cardAnimEnter(index)" 
			@mouseleave="cardAnimExit" 
		>
			<div class="product-card">
				<h2 class="name">{{ cat.title }}</h2>
				<a class="popup-btn">Quick View</a>
				<img :src="`https://attakus.masoodapp.com/static/catts/${cat.src}`" class="product-img" alt="">
			</div>
		</div>

	</div>
</template>


<script>
	export default {
		data () {
			return {
				cattsArr: [],
				slectCard: null,
			}
		},
		async fetch() {
			await this.getMyProds();
		},
		fetchDelay: 1000,
		mounted () {
			
		},
		methods: {
			async getMyProds() {
				const data = [
					{src:'catt1.png',title:'Category 1'},
					{src:'catt2.png',title:'Category 2'},
					{src:'catt3.png',title:'Category 3'},
				];
				const result = await data;
				result.forEach((cat) => {
					this.cattsArr.push(cat)
				})
			},
			cardAnimEnter (index) { this.slectCard = index; },
			cardAnimExit () { this.slectCard = null; },
		},
	}
</script>
