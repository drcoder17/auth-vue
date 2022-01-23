<template>
	<div>
		<navbar v-if="isNavbar"></navbar>
		<form
			@submit.prevent="handleRegister"
			class="mt-5 border rounded container"
		>
			<div class="d-block text-center my-3">
				<h4>Sign in</h4>
			</div>
			<div class="d-block mb-3">
				<label for="email">Email address</label>
				<input
					id="email"
					class="form-control"
					type="email"
					v-model="email"
					placeholder="example@test.com"
					autocomplete="off"
				/>
			</div>
			<div class="d-block mb-3">
				<label for="password">Password</label>
				<input
					id="password"
					class="form-control"
					type="password"
					name="password"
					v-model="password"
					placeholder="Password"
					autocomplete="off"
				/>
			</div>
			<div
				class="d-flex align-items-center justify-content-between mb-3 text-right"
			>
				<router-link to="/register" class="mr-a">
					Don't you have an account?
				</router-link>
				<button type="submit" class="btn btn-primary">Login</button>
			</div>
		</form>
	</div>
</template>

<script>
	import axios from 'axios';
	import Navbar from '../components/Navbar.vue';
	export default {
		data() {
			return {
				email: '',
				password: '',
				isNavbar: '',
			};
		},
		components: {
			Navbar,
		},
		created() {
			const token = localStorage.getItem('token');
			this.isNavbar = token;
		},
		methods: {
			async handleRegister() {
				const user = {
					email: 'eve.holt@reqres.in',
					password: 'cityslick',
				};
				const { data } = await axios.post(
					'https://reqres.in/api/login',
					user,
				);
				if (data && data.token) {
					localStorage.setItem('token', data.token);
					this.$router.push('/');
				} else {
					localStorage.removeItem('token');
					this.$router.push('/login');
				}
			},
		},
	};
</script>
