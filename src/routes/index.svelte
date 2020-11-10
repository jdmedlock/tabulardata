<script>
	import Tabular from '../components/Tabular.svelte'

	const personData = [
		{ avatarImg: 'https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2.2&w=160&h=160&q=80', 
			email: 'Joe@gmail.com', firstName: 'Joseph', lastName: 'Murtaugh', status: 'Active' },
		{ avatarImg: 'https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2.2&w=160&h=160&q=80', 
			email: 'Jane@company.com', firstName: 'Jane', lastName: 'Knope', status: 'Inactive' },
	]

	const getPersonData = ((rowsPerPage, noRowsDisplaed) => {
		// TODO: define this function
	})

	const personRpt = {
		dataSource: {
			reader: getPersonData,
			rowsPerPage: 5
		},
		columns: [
			{ type: 'image', heading: 'Avatar', dataName: 'avatarImg' },
			{ type: 'text', heading: 'email', dataName: 'email' },
			{ type: 'text', heading: 'Last Name', dataName: 'lastName' },
			{ type: 'text', heading: 'First Name', dataName: 'firstName' },
			{ type: 'pill', heading: 'Status', dataName: 'status',
					decorators: [ 
						{ value: 'Active', pillColor: 'bg-blue-200' },
						{ value: 'Inactive', pillColor: 'bg-blue-400' },
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