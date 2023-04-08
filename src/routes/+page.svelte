<script>
	import Counter from "./Counter.svelte";
	import {data} from "./data"

	$: totalpackage = 0;

	function getTotalPackage(total){
		totalpackage = total
	} 
</script>

<section>
	<h3 class="header-h3">Svelte Counter</h3>
	<div class="my-flex">
	{#each data as dt}
	<Counter data={dt} totalPackage={totalpackage} getTotal={getTotalPackage} />
	{/each}
	</div>
	
	<section class="checkout">
		<button>Checkout</button>
		<p>Total ₦{totalpackage}</p>
	</section>
</section>

<style>
	.header-h3{
		color: chocolate;
		font-weight: 600;
		font-size: 2rem;
	}
	.my-flex{
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		align-items: center;
		justify-content: flex-start;
		flex-wrap: wrap;

	}
	button{
		outline: none;
		border: 0;
		padding: 0.5rem 1rem;
		background-color: chocolate;
		border-radius: 0.5rem;
		color: white;
		cursor: pointer;
	}
	.checkout{
		display: flex;
		justify-content: space-between;
	}
</style>