<script>
	import axios from "axios";
	let productCard = false;
	$: dataCode = "";
	$: codeBarre = "";
	$: productQuantity = 1;
	$: sugarQuantity = 1;
	$: imgProduct = "";
	$: url = 'https://fr.openfoodfacts.org/api/v0/product/' + codeBarre + '.json';
	let pourcentageSugar = 1;
	let nbSucreTotal = 1;

	function calculPourc() {
		let quantityNb = Number(productQuantity);
		let sugarNb = Number(sugarQuantity);
		let multiplePar = quantityNb / 100;
		let quantityFinal = productQuantity;
		let quantitySugarFinal = sugarQuantity * multiplePar;
		let pourcentageSugarNb = quantitySugarFinal * 100 / quantityFinal;
		pourcentageSugar = Math.round(pourcentageSugarNb * 10) / 10 ;
		nbSucreTotal = Math.round((quantitySugarFinal / 5) * 10) / 10;
	}

	function getData () {
		url = url;
		productCard = true;
		console.log(url);
		axios.get(url).then(resp => {
		dataCode = resp.data.product.product_name_fr;
		imgProduct = resp.data.product.selected_images.front.small.fr;
		productQuantity = resp.data.product.product_quantity;
		sugarQuantity = resp.data.product.nutriscore_data.sugars;
		calculPourc();
		});
	}

	
</script>

<style>
	h1, p {
		text-align: center;
		margin: 0 auto;
	}

	h1 {
		font-size: 2em;
		text-transform: uppercase;
		font-weight: 700;
		margin: 0 0 0.5em 0;
	}

	p {
		margin: 1em auto;
	}

	@media (min-width: 480px) {
		h1 {
			font-size: 4em;
		}
	}

	input {
		appearance: none;
		background-color: transparent;
		border: .1rem solid darkslategrey;
		border-radius: .4rem;
		box-shadow: none;
		box-sizing: inherit;
		height: 3.8rem;
		padding: .6rem 1.0rem;
		width: 50%;
		text-align: center;
	}

	input:focus {
		border-color: rgb(255,62,0);
		outline: 0
	}

	button {
		margin: 20px;
		background-color: rgb(255,62,0);
		border: .1rem solid whitesmoke;
		border-radius: .4rem;
		color: whitesmoke;
		cursor: pointer;
		display: inline-block;
		font-size: 1.1rem;
		font-weight: 700;
		height: 3.8rem;
		letter-spacing: .1rem;
		line-height: 3.8rem;
		padding: 0 3.0rem;
		text-align: center;
		text-decoration: none;
		text-transform: uppercase;
		white-space: nowrap;
	}

	button:focus,
	button:hover {
		background-color: rgb(238, 140, 107);
		border-color: white;
		color: white;
		outline: 0;
	}

	#divInput {
		display: flex;
		flex-direction: column;
		justify-content: stretch;
		align-items: center;
	}

	#productCard {
		background-color: whitesmoke;
  		box-shadow: 0 0.3em 0.4em -0.110em;
  		max-width: 70%;
		padding: 20px 40px 20px 40px;
		margin: auto;  
  		position: relative;
		margin-top: 30px;
		display: flex;
		flex-direction: row;
		align-items: stretch;
		justify-content: space-around;
	}

	#productCard p {
		text-align: left;
		margin-left: 30px;
	}

	#productCard img {
		margin-right: 30px;
		margin-top: 15px;
	}

	#productCard span {
		font-weight: bold;
	}

</style>

<svelte:head>
	<title>Tapez le code barre</title>
</svelte:head>

<h1>Tapez le code barre</h1>
<p>Pour connaitre les propriétés d'un produits</p>
<div id="divInput">

	<input type="number" bind:value={codeBarre}>
	<button on:click={getData}>Valider</button>

	

</div>

{#if productCard}
	<div id="productCard">
		<div>
			<p>Produit : <span>{dataCode}</span></p>
			<p>Poids/Contenance : {productQuantity}</p>
			<p>Pourcentage de sucre : <span>{pourcentageSugar} %</span></p>
			<p>Nombre de morceaux de sucres dans le produit total : <span>{nbSucreTotal}</span></p>
		</div>	
		<img src="{imgProduct}" alt="prduct" width="100" height="150">
	</div>
	{:else}
		<p>babababab</p>
	{/if}