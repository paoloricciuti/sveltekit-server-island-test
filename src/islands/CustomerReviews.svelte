<script lang="ts" module>
	import { shuffle } from '$lib';

	export async function load() {
		let p = new Promise((resolve) => setTimeout(resolve, 1000));
		await p;

		const all_reviews = [
			{
				name: 'Neil Davis',
				stars: 4,
				review: `Lovely island, great staff. Sunsets were amazing and a large variety of food offerings had something for everyone. The entertainment was fine, and the rooms were a little dated. Great value for an all-inclusive resort.`,
			},
			{
				name: 'Donna Neville',
				stars: 1,
				review: `The rooms were small and dirty, and the electricity often went out randomly. The toilet leaked and it took three days for maintenance to take a look at it. The beach was nice, but crowded and it was hard to relax. Not worth the money!!!`,
			},
			{
				name: 'JT',
				stars: 3,
				review: `I've been to better places, but I've also been to much worse. Clean and safe enough, but nothing special. There were good activities for the whole family. Ask for a room on the upper floor as the elevators are slow and often get stuck.`,
			},
			{
				name: 'beachlover',
				stars: 5,
				review: `A spectacular island resort that was perfect in every way! Crystal clear water and smooth white sand. Rooms were luxurious and the restaurants were delicious. My new favourite vacation spot!`,
			},
			{
				name: 'Antonia G.',
				stars: 3,
				review: `Pros: The bed was super comfortable, the drinks included in the package were strong, the beach was relaxing. Cons: It is a bit of a hassle to get to from the airport, and I'm pretty sure we were overcharged by the taxi. The food wasn't as fresh by the end of the week so we mostly stuck to safer choices. I'm pretty sure the ziplining tour wouldn't have passed a safety inspection. All in all, not a bad place for a beach vacation if your expectations are reasonable, especially if you book on sale.`,
			},
			{
				name: 'Pablo',
				stars: 4,
				review: `One of the better places I've travelled! Our dedicated valet Sam was always helpful when we needed anything. You can visit the nightclub in the evenings, but otherwise you're staying in your room, which suited us fine as we came to party! If you're looking for a quieter vacation, you might find it a little loud.`,
			},
			{
				name: 'Simona',
				stars: 2,
				review: `I don't like to complain but this place was NOT worth the money! Looked nothing like the photos online and there were hidden costs. The beach itself was fine, but they could have cleared away the debris from the sea a bit better. I don't know why they felt like they needed to trick you into going. If I hadn't felt cheated and scammed, I might have actually enjoyed it!`,
			},
			{
				name: 'Ana M',
				stars: 5,
				review: `We came to get away from the city and this was the perfect place to forget about life back home! We didn't want to leave! There was a fantastic reef with lots of coral and fish and we got some amazing photos. Special thanks to Maria who knew just when to refresh your drink!!`,
			},
			{
				name: 'stw',
				stars: 1,
				review: `DO NOT STAY HERE!! The beds were uncomfortable and smaller than expected. Our shower didn't work when we arrived. We brushed our teeth with the tap water and both got sick. Basic economy food with little choice. There was snorkelling twice a day but no attention paid to safety. The views were nice, but impossible to enjoy them. Would not go back until they get new management.`,
			},
			{
				name: 'cruize4life',
				stars: 4,
				review: `I normally go on cruises instead of staying at all-inclusive resorts, so I wasn't sure what to expect. Not as many activities, but the ones I did (snorkelling, boat trips, walking tours, beach volleyball) were fun and well organized. The casino had a nice selection of updated slots, but drink service wasn't very attentive. Would recommend!`,
			},
			{
				name: 'Olle',
				stars: 3,
				review: `My wife chose this place based on a recommendation and I wasn't sure what to expect. Everything in the room was old but everything was clean enough. The staff was very friendly and the sunsets were amazing. Lots of time spent relaxing on the beach and even won $300 in the casino. Might be a better trip for a large group of friends planning activities together. It's not exactly a romantic, luxury destination.`,
			},
		];

		const reviews = shuffle(all_reviews).slice(0, 3);

		return { reviews };
	}
</script>

<script lang="ts">
	import Stars from '$lib/Stars.svelte';

	import type { ServerIslandsProps } from 'sveltekit-server-islands';

	let { data }: ServerIslandsProps<typeof load> = $props();
</script>

<div class="space-y-6">
	<div class="text-lg font-medium text-white">
		<span class="text-orange-300">Selected</span> customer reviews
	</div>
	<div class="space-y-8">
		{#each data?.reviews ?? [] as { name, stars, review }}
			<div class="space-y-4">
				<div class="space-y-2">
					<div class="flex items-center gap-x-2">
						<div class="h-6 w-6 rounded-full bg-gray-700"></div>
						<div class="text-sm text-white">{name}</div>
					</div>
					<Stars {stars} />
				</div>
				<div class="text-gray-400">{review}</div>
			</div>
		{/each}
	</div>
</div>
