<script>
	import {Card, CardBody, CardFooter, CardHeader, CardTitle} from 'sveltestrap';
	import Logo from "../lib/assets/LightningbulbLogo.png"

	import { slide } from 'svelte/transition';
	let showingCard = true;

	function toggleCard() {
		showingCard = !showingCard;
	}

</script>

<svelte:head>
	<title>Digital Hobbies</title>
	<meta name="description" content="Digital Hobbies" />
</svelte:head>

<div class="d-flex justify-content-center p-5">


	<Card style="width: 20rem" class="shadow-lg bg-notquiteblack text-center text-light">
		<div style="height: 25rem" class=" shadow-lg bg-notequiteblack"
			 on:mouseenter={() => {toggleCard();}}
			 on:mouseleave={() => {toggleCard();}}>

		{#if showingCard}

			<div transition:slide|local>

				<CardHeader>
					<CardTitle>Welcome to Digital Hobbies</CardTitle>
				</CardHeader>
				<CardBody>
					<img src={Logo} class="w-100 rounded-2" alt="Lightningbulb Logo">
				</CardBody>
				<CardFooter>
					A Lightningbulb website.
				</CardFooter>

			</div>

		{/if}

		{#if !showingCard}

			<div transition:slide|local>

				<CardHeader>
					<CardTitle>Lightningbulb.png</CardTitle>
				</CardHeader>
				<CardBody>
					I made this image in photoshop,<br> March of 2020.
				</CardBody>

			</div>

		{/if}

		</div>
	</Card>


</div>


