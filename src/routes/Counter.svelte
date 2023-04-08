<script>
	export let data;
	export let totalPackage;
	export let getTotal;
	let count = 0;
	let total = 0;

	$: console.log(total)

	function incrementCount(amount){
		count += 1
		total = amount * count;
		getTotal(total)
	}

	function decrementCount(amount){
		count -= 1;
		total = total - amount
		getTotal(total)
	}
</script>

<section class="container">
	<div style="display: flex;align-items:center;justify-content:space-between;font-style:italic">
	<h4>{data.name}</h4>
	<span>₦{data.amount}</span>
	</div>
	<p>{data.description}</p>
	<section class="wrapper-container">
		<div class="wrapper">
			<button on:click={() => incrementCount(Number(data.amount))}>+</button>
			<div>
			<h3>{count}</h3>
			</div>
			{#if count === 0}
				<button disabled>-</button>
				{:else}
				<button  on:click={()=>decrementCount(Number(data.amount))}>-</button>
				{/if}
		</div>
		<div>
			<p style="font-weight: 700;">₦{total}</p>
		</div>
	</section>
	
</section>

<style>
	.container{
		width: 300px;
		border-radius: 10px;
		padding: 0.7rem;
		background-color: lightgray;
		margin:1rem;
		
	}
	.wrapper-container{
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
	
	.wrapper{
		display: flex;
		justify-content: flex-start;
		align-items: center;
	}
	button{
		outline: none;
		border: 0;
		padding: 0.5rem 1rem;
		background-color: chocolate;
		color: white;
		border-radius: 00.5rem;
		text-align: center;
		margin: 0.5rem;
		cursor: pointer;
	}
	.bottom-flex{
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
</style>