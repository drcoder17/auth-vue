<template>
	<div>
		<form
			@submit.prevent="handleRegister"
			class="mt-5 border rounded container"
		>
			<div class="d-block text-center my-3">
				<h4>Register new user!</h4>
			</div>
			<div class="d-block mb-3">
				<label for="firstName">First name</label>
				<input
					id="firstName"
					class="form-control"
					type="text"
					name="firstName"
					v-model="firstName"
					placeholder="First name..."
					autocomplete="off"
				/>
			</div>
			<div class="d-block mb-3">
				<label for="lastName">Last name</label>
				<input
					id="lastName"
					class="form-control"
					type="text"
					name="lastName"
					v-model="lastName"
					placeholder="Last name..."
					autocomplete="off"
				/>
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
			<div class="d-block mb-3 text-right">
				<router-link to="/login" class="mr-5">
					Do you have an account?
				</router-link>
				<button
					type="reset"
					@click="handleClear"
					class="btn btn-danger mr-3"
				>
					Clear form
				</button>
				<button type="submit" class="btn btn-primary">Submit</button>
			</div>
		</form>
	</div>
</template>

<script>
	import axios from 'axios';
	export default {
		data() {
			return {
				firstName: '',
				lastName: '',
				email: '',
				password: '',
			};
		},
		methods: {
			async handleRegister() {
				const user = {
					email: 'eve.holt@reqres.in',
					password: 'pistol',
				};
				const { data } = await axios.post(
					'https://reqres.in/api/register',
					user,
				);
				this.$router.push('/login');
			},
			handleClear() {
				this.firstName = '';
				this.lastName = '';
				this.email = '';
				this.password = '';
			},
		},
	};
</script>
