<script lang="ts">
	import ThSort from '$lib/components/client/ThSort.svelte';
	import ThFilter from '$lib/components/client/ThFilter.svelte';
	import Search from '$lib/components/client/Search.svelte';
	import RowsPerPage from '$lib/components/client/RowsPerPage.svelte';
	import RowCount from '$lib/components/client/RowCount.svelte';
	import Pagination from '$lib/components/client/Pagination.svelte';

	import data from '$lib/components/client/data';
	import { DataHandler } from '@vincjo/datatables';
	const yearMapping: { [key: number]: string } = {
		1025681: '2010-2020 decade',
		1970023: '2011',
		3395201: '2012',
		6994370: '2014',
		8822723: '2015',
		10809767: '2016',
		16007988: '2018',
		18753859: '2019',
		21802596: '2020-30 decade',
		25594068: '2021',
		29746236: '2022',
		34125628: '2023'
	};
	const processedData = data.map((item) => ({
		...item,
		year: yearMapping[item.post_id] ? yearMapping[item.post_id] : 'Unknown',
		commentLink: `https://news.ycombinator.com/item?id=${item.comment_id}`
	}));
	const handler = new DataHandler(processedData, { rowsPerPage: 20 });
	const rows = handler.getRows();
</script>

<div class="overflow-x-auto space-y-4">
	<!-- Header -->
	<header class="flex justify-between gap-4">
		<Search {handler} />
		<RowsPerPage {handler} />
	</header>
	<!-- Table -->
	<table class="table table-hover table-compact w-full table-auto">
		<thead>
			<tr>
				<ThSort {handler} orderBy="year">Prediction For</ThSort>
				<ThSort {handler} orderBy="text">Text</ThSort>
				<ThSort {handler} orderBy="result_enum">Result</ThSort>
				<ThSort {handler} orderBy="category">Category</ThSort>
				<ThSort {handler} orderBy="sub_category">Sub-category</ThSort>
				<ThSort {handler} orderBy="comment_author">Author</ThSort>
				<th>Explanation</th>
				<th>Post Link</th>
			</tr>
			<tr>
				<ThFilter {handler} filterBy="year" />
				<ThFilter {handler} filterBy="text" />
				<ThFilter {handler} filterBy="result_enum" />
				<ThFilter {handler} filterBy="category" />
				<ThFilter {handler} filterBy="sub_category" />
				<ThFilter {handler} filterBy="comment_author" />
				<ThFilter {handler} filterBy="explanation" />
				<th></th>
				<!-- No filter for Post Link -->
			</tr>
		</thead>
		<tbody>
			{#each $rows as row}
				<tr>
					<td>{row.year}</td>
					<td>{row.text}</td>
					<td>{row.result_enum}</td>
					<td>{row.category}</td>
					<td>{row.sub_category}</td>
					<td>{row.comment_author}</td>
					<td>{row.explanation}</td>
					<td><a href={row.commentLink} target="_blank" rel="noopener noreferrer">View Comment</a></td>
				</tr>
			{/each}
		</tbody>
	</table>
	<!-- Footer -->
	<footer class="flex justify-between">
		<RowCount {handler} />
		<Pagination {handler} />
	</footer>
</div>
