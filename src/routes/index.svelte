<script>
	import Tabular from '../components/Tabular.svelte'
	import TabStart from '../components/TabStart.svelte'
	import TabImageCell from '../components/TabImageCell.svelte'
	import TabPillCell from '../components/TabPillCell.svelte'
	import TabTextCell from '../components/TabTextCell.svelte'
	import TabRender from '../components/TabRender.svelte'

	const personData = [
		{ avatarImg: 'https://url.com/joesicon', email: 'Joe@gmail.com', 
			firstName: 'Joseph', lastName: 'Murtaugh', status: 'Active' },
		{ avatarImg: 'https://url.com/janesicon', email: 'Jane@company.com', 
			firstName: 'Jane', lastName: 'Knope', status: 'Inactive' }
	]

	const personRpt = {
		columns: [
			{ type: 'image', heading: 'Avatar', dataName: 'avatarImg' },
			{ type: 'text', heading: 'email', dataName: 'email' },
			{ type: 'text', heading: 'Last Name', dataName: 'lastName' },
			{ type: 'text', heading: 'First Name', dataName: 'firstName' },
			{ type: 'pill', heading: 'Status', dataName: 'status',
					decorators: [ 
						{ value: 'Awesome', pillColor: 'bg-blue-200' },
						{ value: 'Unknown', pillColor: 'bg-blue-400' },
					]
			}
		]
	}
</script>

<style type="text/postcss">
	h1 {
		@apply text-center text-5xl text-green-700 uppercase font-semibold mb-2;
	}
</style>

<svelte:head>
	<title>Tabular Data Test</title>
</svelte:head>

<h1>Tabular Data Test</h1>

<Tabular definition={ personRpt } data={ personData } />