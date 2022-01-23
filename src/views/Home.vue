<template>
	<div class="home">
		<navbar></navbar>
		<div>Home Page</div>
	</div>
</template>

<script>
	import Navbar from '../components/Navbar.vue';

	export default {
		name: 'Home',
		components: {
			Navbar,
		},
		updated() {
			const token = localStorage.getItem('token');
			if (!token) {
				this.$router.push('/login');
			}
		},
	};
</script>
