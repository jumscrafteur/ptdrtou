<script lang="ts">
	import { AspectRatio } from '$components/ui/aspect-ratio';
	import { Button } from '$components/ui/button';
	import {
		Card,
		CardContent,
		CardDescription,
		CardFooter,
		CardHeader,
		CardTitle
	} from '$components/ui/card';

	let cities = ['city1', 'city2', 'city3'];
	let valid: null | string = null;

	let selected = false;
</script>

<Card>
	<CardHeader>
		<CardTitle>Où se trouve cette photo ?</CardTitle>
		<!-- <CardDescription>Card Description</CardDescription> -->
	</CardHeader>
	<CardContent>
		<AspectRatio ratio={16 / 9} class="bg-muted">
			<img
				src="https://images.unsplash.com/photo-1514565131-fce0801e5785?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2156&q=80"
				alt="city"
				class="rounded-md object-cover h-full w-full"
			/>
		</AspectRatio>
	</CardContent>
	<CardFooter class="flex flex-col gap-4">
		<!-- <h1>test</h1> -->
		<div class="flex gap-8 w-full">
			{#each cities as city}
				<input disabled={selected} type="radio" name="cities" value={city} id={city} />
				<label
					class={'grow border rounded-sm px-4 py-2 ' + (city == valid ? 'success' : 'danger')}
					for={city}>{city}</label
				>
			{/each}
		</div>
		<Button
			class="w-full bg-blue-500 hover:bg-blue-600"
			on:click={() => {
				valid = cities[0];
				selected = !selected;
			}}>Button</Button
		>
	</CardFooter>
</Card>

<style lang="postcss">
	input[type='radio'] {
		display: none;

		&:checked + label {
			border-color: theme(colors.blue.500);
			background-color: theme(colors.blue.50);
			color: theme(colors.blue.500);
		}

		&:disabled + label {
			&.success {
				border-color: theme(colors.green.500);
				background-color: theme(colors.green.50);
				color: theme(colors.green.500);
			}

			&.danger {
				border-color: theme(colors.red.500);
				background-color: theme(colors.red.50);
				color: theme(colors.red.500);
			}
		}
	}
</style>
