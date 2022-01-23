<template>
	<nav class="navbar bg-dark px-5 py-3">
		<router-link class="text-decoration-none text-white" to="/"
			>Logo</router-link
		>
		<ul class="d-flex flex-row list-group">
			<li class="list-group">
				<router-link class="text-decoration-none text-info mr-5" to="/">
					Home
				</router-link>
			</li>
			<li class="list-group">
				<router-link
					class="text-decoration-none text-info mr-5"
					to="/about"
				>
					About
				</router-link>
			</li>
			<li class="list-group" v-if="!isNavbar">
				<router-link
					class="text-decoration-none text-info mr-5"
					to="/login"
				>
					Login
				</router-link>
			</li>
			<li class="list-group" v-if="!isNavbar">
				<router-link
					class="text-decoration-none text-info"
					to="/register"
				>
					Register
				</router-link>
			</li>
			<li class="list-group" v-if="isNavbar">
				<a
					class="text-decoration-none text-info"
					@click="handleLogout"
					href="/login"
				>
					Logout
				</a>
			</li>
		</ul>
	</nav>
</template>

<script>
	export default {
		name: 'Navbar',
		data() {
			return {
				isNavbar: false,
			};
		},
		created() {
			const token = localStorage.getItem('token');
			if (token) {
				this.isNavbar = true;
			}
		},
		methods: {
			handleLogout() {
				localStorage.removeItem('token');
			},
		},
	};
</script>
