<script>
export const username = "Maryam";
function go() {
	window.location = "about";
}
</script>

<svelte:head>
	<title>🍭Soukkar - Find the sugar🍭 </title>
</svelte:head>

<main>
	<section>
		<img src="./logo.png" alt="logo" id="logo">
		<!--<div>
			<a href="./#" class="button">Scanner un produit</a>
		</div>
		<div class="bloc-sep"><div class="sep"></div>ou<div class="sep"></div></div> -->
		<form>
			<p>Tapez le code barre du produit à analyser</p>
			<input type="number" placeholder="Ex: 0737628064502" id="inputCodeBarre"><br>
			<button href="./#" class="button" type="submit" on:click|preventDefault={go}>GO</button>
		</form>
	</section>
</main>

<style>
	main {
		text-align: center;
		font-size: 1.2em;
		font-family: "Laksaman", sans-serif;
	}

	section {
		padding: 10%;
	}

	form {
		margin-top: 5%;
	}

	/*.sep {
		height: 1px;
		width: 40%;
		border-top: 1px solid grey;
	}

	.bloc-sep {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		padding: 8%;
	} */

	p {
		padding: 0;
	}

	#logo {
		height: auto;
		width: 80%;
		margin-bottom: 10%;
		margin-top: 7%;
	}

	input {
		border: 2px solid rgb(43, 45, 53);
		background-color: rgb(249, 249, 249);
		width: 80%;
		padding: 7%;
		color: rgb(43, 45, 53);
		font-family: "Laksaman", sans-serif;
		font-size: 1em;
	}

	button[type='submit'] {
		box-shadow: 2px 2px rgba(43, 45, 53, 0.219);
		color: rgb(249, 249, 249);
		font-size: 1.3em;
		padding: 5%;
		text-align: center;
		line-height: 0;
		font-weight: 500;
		margin: 2%;
		font-family: "Laksaman", sans-serif;
	}

	@media (max-width: 320px) {
		section {
			padding-left: 3%;
			padding-right: 3%;
		}
	}

	@media (min-width: 425px) {
		#logo {
			width: 60%;
		}
	}

	@media (min-width: 1024px) {
		#logo {
			width: 40%;
			margin-bottom: 6%;
		}

		input {
			padding: 4%;
			margin: 2%;
		}

		p {
			font-size: 1.2em;
		}

		button[type='submit'] {
			padding: 3.5%;
		}
	}

	@media (min-width: 1300px) {
		section {
			padding: 2%;
		}

		#logo {
			width: 15%;
			margin-bottom: 0;
			margin-top: 2%;
		}

		input {
			padding: 1.5%;
			margin: 2%;
			margin-top: 0;
			width: 27%;
		}

		p {
			font-size: 1.2em;
		}

		button[type='submit'] {
			margin-top: 0;
			padding: 1.5%;
		}
	}

</style>
