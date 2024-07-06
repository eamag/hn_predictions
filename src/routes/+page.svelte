<script>
	export let categories = [
		{ name: 'Technology', successRate: '49.03%', predictions: 1086 },
		{ name: 'Economy', successRate: '56.91%', predictions: 246 },
		{ name: 'Health', successRate: '53.93%', predictions: 140 },
		{ name: 'Politics', successRate: '38.02%', predictions: 509 },
		{ name: 'Society', successRate: '63.51%', predictions: 37 },
		{ name: 'Markets', successRate: '39.52%', predictions: 248 },
		{ name: 'Environment', successRate: '53.64%', predictions: 55 },
		{ name: 'Energy', successRate: '68.42%', predictions: 19 },
		{ name: 'Education', successRate: '69.44%', predictions: 18 },
		{ name: 'Finance', successRate: '54.17%', predictions: 24 }
	];

	export let authors = [
		{ name: 'asah', successRate: '88.10%', predictions: 21, id: '29768678' },
		{ name: 'bryan0', successRate: '90.62%', predictions: 16, id: '29782939' },
		{ name: 'redbar0n', successRate: '84.21%', predictions: 19, id: '34132249' },
		{ name: 'elihu', successRate: '91.67%', predictions: 12, id: '25602265' },
		{ name: 'guillem_lefait', successRate: '88.46%', predictions: 13, id: '25603049' },
		{ name: 'notional', successRate: '95.00%', predictions: 10, id: '25618257' },
		{ name: 'IsaacL', successRate: '95.00%', predictions: 10, id: '1027093' },
		{ name: 'AnimalMuppet', successRate: '84.62%', predictions: 13, id: '10809905' },
		{ name: 'birdymcbird', successRate: '90.00%', predictions: 10, id: '34125732' },
		{ name: 'dan-robertson', successRate: '66.00%', predictions: 25, id: '25602728' }
	];

	export let overall = {
		totalPredictions: 2804,
		successRate: '45.77%'
	};
</script>

<div class="space-y-10">
	<!-- Header -->
	<header class="flex justify-center items-center gap-10">
		<p class="text-2xl text-center text-balance">
			Hacker News Predictions
			<a class="anchor" href="https://news.ycombinator.com/item?id=1025681" target="_blank"> from Ask HN posts</a>
			 evaluated using LLMs
		</p>
	</header>
	<div class="text-center">
		<a class="btn variant-filled" href="/table" target="_blank"> See the full table &rarr; </a>
	</div>
	<div class="text-center">
		<h1>Some Statistics</h1>
		<p>
			Total predictions: {overall.totalPredictions} <br />
			Overall success rate: {overall.successRate} <br />
			16 out of 21 predictions about Linux are wrong <br />
			26 out of 49 predictions about Bitcoin are wrong <br />
			Nobody predicted anything about Nvidia <br />
			Lots of predictions about the fall of Microsoft <br />
		</p>
	</div>
	<div class="card p-4">
		<nav class="list-nav">
			<h1>Top Authors</h1>
			<ul>
				{#each authors as author, i}
					<li>
						<a href={`https://news.ycombinator.com/item?id=${author.id}`} target="_blank">
							<span class="badge-icon p-4 variant-soft-primary">{i + 1}</span>
							<span>
							{author.name} : {author.successRate} success rate, {author.predictions} predictions
							</span>
						</a>
					</li>
				{/each}
			</ul>
		</nav>
	</div>
	<div class="card p-4">
		<h1>Top Categories</h1>
		<ul class="list">
			{#each categories as category, i}
				<li>
					<span class="badge-icon p-4 variant-soft-primary">{i + 1}</span>
					<span class="flex-auto"
						>{category.name}: {category.successRate} success rate, {category.predictions} predictions
					</span>
				</li>
			{/each}
		</ul>
	</div>

	<!-- Links -->
	<div class="max-w-[600px] mx-auto grid grid-cols-1 gap-4">
		<!-- Client -->
		<a class="card card-hover overflow-hidden" href="/table">
			<header class="flex justify-between items-center p-4">
				<h3 class="h3">All Data In A Table</h3>
				<h3 class="h3">&rarr;</h3>
			</header>
			<hr class="hr" />
			<div class="p-4 space-y-4">
				<article>
					<p>All data in a table with a filter and search functionality.</p>
				</article>
			</div>
		</a>
	</div>
	<!-- Credit -->
	<footer class="text-center">
		<small>
			<span class="opacity-60">This site is built using </span>
			<a
				class="anchor"
				href="https://github.com/skeletonlabs/skeleton-datatables-integration"
				target="_blank">Skeleton DataTables Template</a
			>
		</small>
	</footer>
</div>