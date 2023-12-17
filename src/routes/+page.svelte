<script>
	let passwordForgotten = true;
	let email = '';
	let password = '';

	$: loginBtnLabel = passwordForgotten ? 'Se connecter par email' : 'Se connecter';
	$: canUseLoginBtn = !email || (!password && !passwordForgotten);
</script>

<div
	class="w-full min-h-screen p-2.5 flex-col justify-start items-start gap-2.5 inline-flex bg-white"
>
	<form
		class="p-6 bg-white rounded-md border border-slate-200 flex-col justify-start items-start gap-6 flex m-auto drop-shadow-lg"
	>
		<div class="py-1 bg-white flex-col justify-start items-start gap-2.5 flex">
			<div class="w-60 bg-white rounded justify-start items-center gap-7 inline-flex">
				<div class="grow shrink basis-0 text-slate-900 text-xl font-semibold leading-7">
					Connexion
				</div>
			</div>
		</div>
		<div class="flex-col justify-start items-start gap-6 flex">
			<div class="flex-col justify-start items-start gap-4 flex">
				<div class="h-16 flex-col justify-start items-start gap-1.5 flex">
					<div class="text-slate-900 text-base font-medium leading-tight">Email</div>
					<div class="self-stretch justify-start items-start gap-2 inline-flex">
						<div class="grow shrink basis-0 flex-col justify-start items-start gap-1.5 inline-flex">
							<input
								type="email"
								placeholder="Email"
								bind:value={email}
								class="text-base font-normal leading-tight self-stretch pl-3 pr-14 py-2 bg-white rounded-md border border-slate-300 justify-start items-center inline-flex"
							/>
						</div>
					</div>
				</div>
				<button
					class="justify-start items-center gap-2 inline-flex cursor-pointer"
					on:click={() => (passwordForgotten = !passwordForgotten)}
					role={'button'}
				>
					<div class="w-11 h-6 relative">
						<div
							class="w-11 h-6 left-0 top-0 absolute bg-slate-200 rounded-3xl transition-all duration-200 ease-in-out"
							class:bg-slate-900={!passwordForgotten}
						></div>
						<div
							class="w-5 h-5 left-[2px] top-[2px] absolute bg-white rounded-full transition-all duration-200 ease-in-out"
							class:left-[22px]={!passwordForgotten}
						></div>
					</div>
					<div class="text-black text-base font-medium leading-none">
						Je connais mon mot de passe
					</div>
				</button>
				<div
					class="self-stretch h-16 flex-col justify-start items-start gap-1.5 flex"
					class:opacity-50={passwordForgotten}
				>
					<div
						class="text-slate-900 text-base font-medium leading-tight"
						class:text-slate-500={passwordForgotten}
					>
						Mot de passe
					</div>
					<div class="self-stretch justify-start items-start gap-2 inline-flex">
						<div class="grow shrink basis-0 flex-col justify-start items-start gap-1.5 inline-flex">
							<input
								type="password"
								placeholder="Mot de passe"
								disabled={passwordForgotten}
								class:cursor-not-allowed={passwordForgotten}
								bind:value={password}
								class="text-base font-normal leading-tight self-stretch pl-3 pr-14 py-2 bg-white rounded-md border border-slate-300 justify-start items-center inline-flex"
							/>
						</div>
					</div>
				</div>
			</div>
			<div
				class="px-4 py-2 bg-slate-900 rounded-md justify-center items-center gap-2.5 inline-flex cursor-pointer hover:bg-opacity-90 transition-all duration-200 ease-in-out active:bg-opacity-100"
				class:opacity-70={canUseLoginBtn}
				class:cursor-not-allowed={canUseLoginBtn}
			>
				<input
					type="submit"
					class="text-white text-base font-medium leading-normal cursor-pointer"
					class:cursor-not-allowed={canUseLoginBtn}
					disabled={canUseLoginBtn}
					value={loginBtnLabel}
				/>
			</div>
		</div>
	</form>
	<div class="justify-start items-start gap-2.5 flex flex-row text-slate-400 gap-3">
		<span>@Em_ilien</span>
		<span>2023</span>
		<a
			target="_blank"
			class="text-slate-400 hover:text-slate-500 transition-all duration-200 ease-in-out"
			href="https://github.com/Em-ilien/login-form-without-password"
			>github.com/Em-ilien/login-form-without-password</a
		>
		<a
			target="_blank"
			class="text-slate-400 hover:text-slate-500 transition-all duration-200 ease-in-out"
			href="https://login-form-without-password.vercel.app"
			>login-form-without-password.vercel.app/</a
		>
	</div>
</div>

<style lang="postcss">
	:global(html) {
		background-color: theme(colors.gray.100);
	}

	:global(body) {
		font-family: 'Inter', sans-serif;
	}
</style>
