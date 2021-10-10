<template>
	<section class="products" id="products">
		<h1 class="heading">latest<span>products</span> </h1>
		<div class="box-container">

			<div v-for="(prod , index) in products" :key="index" class="box">
				<div class="icons">
					<a href="#" class="fas fa-heart"></a>
					<a href="#" class="fas fa-share"></a>
					<a href="#" class="fas fa-eye"></a>
				</div>
				<img :src="`https://attakus.masoodapp.com/static/products/${prod.src}`" alt="">
				<div class="content">
					<h3>{{ prod.title }}</h3>
					<div class="price">$120.99 <span>$150.99</span></div>
					<div class="stars">
						<i class="fas fa-star"></i>
						<i class="fas fa-star"></i>
						<i class="fas fa-star"></i>
						<i class="fas fa-star"></i>
						<i class="far fa-star"></i>
					</div>
					<a href="#" class="btn">add to cart</a>
				</div>
			</div>

		</div>
	</section>
</template>

<script>
	export default {
		props: ['products'],
	}
</script>