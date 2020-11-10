<script>
	import Tabular from '../components/Tabular.svelte'
	
	const femaleAvatar = 'https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2.2&w=160&h=160&q=80'

	const personData = [
		{ avatarImg: femaleAvatar, email: 'joe@gmail.com', 
			firstName: 'Joseph', lastName: 'Murtaugh', status: 'Active' },
		{ avatarImg: femaleAvatar, email: 'jane@yahoo.com', 
			firstName: 'Jane', lastName: 'Knope', status: 'Inactive' },
		{ avatarImg: femaleAvatar, email: 'mdale@gmail.com', 
			firstName: 'Michael', lastName: 'Dale', status: 'Inactive' },
		{ avatarImg: femaleAvatar, email: 'juliesmith@gmail.com', 
			firstName: 'Julie', lastName: 'Smith', status: 'Active' },
		{ avatarImg: femaleAvatar, email: 'adnan@gmail.com', 
			firstName: 'Adnan', lastName: 'Risha', status: 'Inactive' },
		{ avatarImg: femaleAvatar, email: 'regisp@gmail.com', 
			firstName: 'Regis', lastName: 'Piltry', status: 'Active' },
		{ avatarImg: femaleAvatar, email: 'aiman@gmail.com', 
			firstName: 'Trion', lastName: 'Tobor', status: 'Active' },
		{ avatarImg: femaleAvatar, email: 'angelam@gmail.com', 
			firstName: 'Angela', lastName: 'May', status: 'Active' },
		{ avatarImg: femaleAvatar, email: 'rjsingh@gmail.com', 
			firstName: 'RJ', lastName: 'Singh', status: 'Active' },
		{ avatarImg: femaleAvatar, email: 'johnm@gmail.com', 
			firstName: 'John', lastName: 'McMurty', status: 'Inactive' },
		{ avatarImg: femaleAvatar, email: 'nfederko@hotmail.com', 
			firstName: 'Natalia', lastName: 'Federko', status: 'Active' },
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
						{ value: 'Active', pillColor: 'bg-green-400' },
						{ value: 'Inactive', pillColor: 'bg-red-400' },
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