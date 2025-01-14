<script>
    import { fade, fly } from 'svelte/transition';
    import { quintOut } from 'svelte/easing';

    let fullName = '';
    let email = '';
    let password = '';
    let confirmPassword = '';
    let showPassword = false;
    let showConfirmPassword = false;
    let loading = false;
    /**
     * @type {string | null}
     */
    let currentFocus = null;
    let agreeToTerms = false;

    // Password strength variables
    $: passwordStrength = getPasswordStrength(password);
    $: passwordMatch = password === confirmPassword;

    /**
     * @param {string} pass
     */
    function getPasswordStrength(pass) {
      if (!pass) return 0;
      let strength = 0;
      if (pass.length >= 8) strength += 25;
      if (pass.match(/[A-Z]/)) strength += 25;
      if (pass.match(/[0-9]/)) strength += 25;
      if (pass.match(/[^A-Za-z0-9]/)) strength += 25;
      return strength;
    }

    const handleSubmit = () => {
      if (!passwordMatch || passwordStrength < 75 || !agreeToTerms) return;
      loading = true;
      setTimeout(() => loading = false, 1500);
    };

    const focusInput = (/** @type {string | null} */ input) => {
      currentFocus = input;
    };

    const blurInput = () => {
      currentFocus = null;
    };
</script>

<div class="h-screen w-screen bg-gray-50 flex items-center justify-center p-4 relative overflow-hidden">
    <!-- Background elements -->
    <div class="absolute inset-0 overflow-hidden">
      <div class="absolute top-1/4 -left-48 w-96 h-96 bg-purple-100 rounded-full blur-3xl opacity-30"
           style="animation: float 6s ease-in-out infinite;"></div>
      <div class="absolute bottom-1/4 -right-48 w-96 h-96 bg-blue-100 rounded-full blur-3xl opacity-30"
           style="animation: float 8s ease-in-out infinite;"></div>
    </div>

    <!-- Signup Container -->
    <div
      in:fly="{{ y: 20, duration: 600, delay: 200 }}"
      class="relative w-full max-w-sm">
      <div class="bg-white rounded-2xl shadow-xl p-6 space-y-6">
        <!-- Header -->
        <div class="text-center space-y-2">
          <h2 class="text-2xl font-bold bg-clip-text text-transparent bg-gradient-to-r from-purple-600 to-blue-600">
            Create Account
          </h2>
          <p class="text-gray-500">
            Join our community and start your journey
          </p>
        </div>

        <!-- Social Signup -->
        <div class="space-y-4">
          <button
            class="w-full flex items-center justify-center gap-3 p-3 border border-gray-200 rounded-xl hover:bg-gray-50 transition-all duration-300 hover:-translate-y-0.5"
          >
            <svg class="w-5 h-5" viewBox="0 0 24 24">
              <path fill="currentColor" d="M12.545,10.239v3.821h5.445c-0.712,2.315-2.647,3.972-5.445,3.972c-3.332,0-6.033-2.701-6.033-6.032s2.701-6.032,6.033-6.032c1.498,0,2.866,0.549,3.921,1.453l2.814-2.814C17.503,2.988,15.139,2,12.545,2C7.021,2,2.543,6.477,2.543,12s4.478,10,10.002,10c8.396,0,10.249-7.85,9.426-11.748L12.545,10.239z"/>
            </svg>
            <span>Sign up with Google</span>
          </button>
        </div>

        <!-- Divider -->
        <div class="relative">
          <div class="absolute inset-0 flex items-center">
            <div class="w-full border-t border-gray-200"></div>
          </div>
          <div class="relative flex justify-center text-sm">
            <span class="px-2 bg-white text-gray-500">Or sign up with email</span>
          </div>
        </div>

        <!-- Signup Form -->
        <form on:submit|preventDefault={handleSubmit} class="space-y-4">
          <!-- Full Name Input -->
          <div class="space-y-2">
            <label for="fullName" class="text-sm font-medium text-gray-700">Full Name</label>
            <div class="relative">
              <input
                type="text"
                id="fullName"
                bind:value={fullName}
                on:focus={() => focusInput('fullName')}
                on:blur={blurInput}
                class="w-full pl-10 pr-4 py-2 rounded-xl border {currentFocus === 'fullName' ? 'border-purple-500 ring-2 ring-purple-100' : 'border-gray-200'}
                       focus:outline-none transition-all duration-300"
                required
              />
              <div class="absolute inset-y-0 left-4 flex items-center pointer-events-none
                          {currentFocus === 'fullName' ? 'text-purple-500' : 'text-gray-400'}">
                <svg class="w-5 h-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                  <path d="M20 21v-2a4 4 0 00-4-4H8a4 4 0 00-4 4v2M12 11a4 4 0 100-8 4 4 0 000 8z"/>
                </svg>
              </div>
            </div>
          </div>

          <!-- Email Input -->
          <div class="space-y-2">
            <label for="email" class="text-sm font-medium text-gray-700">Email</label>
            <div class="relative">
              <input
                type="email"
                id="email"
                bind:value={email}
                on:focus={() => focusInput('email')}
                on:blur={blurInput}
                class="w-full pl-10 pr-4 py-2 rounded-xl border {currentFocus === 'email' ? 'border-purple-500 ring-2 ring-purple-100' : 'border-gray-200'}
                       focus:outline-none transition-all duration-300"
                required
              />
              <div class="absolute inset-y-0 left-4 flex items-center pointer-events-none
                          {currentFocus === 'email' ? 'text-purple-500' : 'text-gray-400'}">
                <svg class="w-5 h-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                  <path d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
                </svg>
              </div>
            </div>
          </div>

          <!-- Password Input -->
          <div class="space-y-2">
            <label for="password" class="text-sm font-medium text-gray-700">Password</label>
            <div class="relative">
              <input
                id="password"
                bind:value={password}
                on:focus={() => focusInput('password')}
                on:blur={blurInput}
                class="w-full pl-10 pr-12 py-2 rounded-xl border {currentFocus === 'password' ? 'border-purple-500 ring-2 ring-purple-100' : 'border-gray-200'}
                       focus:outline-none transition-all duration-300"
                required
              />
              <div class="absolute inset-y-0 left-4 flex items-center pointer-events-none
                          {currentFocus === 'password' ? 'text-purple-500' : 'text-gray-400'}">
                <svg class="w-5 h-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                  <path d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8V7a4 4 0 00-8 0v4h8z"/>
                </svg>
              </div>
              <button
                type="button"
                on:click={() => showPassword = !showPassword}
                class="absolute inset-y-0 right-4 flex items-center text-gray-400 hover:text-gray-600"
              >
                {#if showPassword}
                  <svg class="w-5 h-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                    <path d="M13.875 18.825A10.05 10.05 0 0112 19c-4.478 0-8.268-2.943-9.543-7a9.97 9.97 0 011.563-3.029m5.858.908a3 3 0 114.243 4.243M9.878 9.878l4.242 4.242M9.88 9.88l-3.29-3.29m7.532 7.532l3.29 3.29M3 3l3.59 3.59m0 0A9.953 9.953 0 0112 5c4.478 0 8.268 2.943 9.543 7a10.025 10.025 0 01-4.132 5.411m0 0L21 21"/>
                  </svg>
                {:else}
                  <svg class="w-5 h-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                    <path d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"/>
                    <path d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z"/>
                  </svg>
                {/if}
              </button>
            </div>
            <!-- Password Strength Indicator -->
            <div class="space-y-2">
              <div class="flex gap-2">
                {#each Array(4) as _, i}
                  <div class="h-1 flex-1 rounded-full bg-gray-200 overflow-hidden">
                    <div
                      class="h-full transition-all duration-300 {passwordStrength >= (i + 1) * 25 ?
                        passwordStrength === 100 ? 'bg-green-500' : 'bg-blue-500' : ''}"
                    ></div>
                  </div>
                {/each}
              </div>
              <p class="text-xs text-gray-500">
                Password must contain at least 8 characters, including uppercase, number, and special character
              </p>
            </div>
          </div>

          <!-- Confirm Password Input -->
          <div class="space-y-2">
            <label for="confirmPassword" class="text-sm font-medium text-gray-700">Confirm Password</label>
            <div class="relative">
              <input
                id="confirmPassword"
                bind:value={confirmPassword}
                on:focus={() => focusInput('confirmPassword')}
                on:blur={blurInput}
                class="w-full pl-10 pr-12 py-2 rounded-xl border
                       {currentFocus === 'confirmPassword' ? 'border-purple-500 ring-2 ring-purple-100' : 'border-gray-200'}
                       {confirmPassword && !passwordMatch ? 'border-red-500' : ''}
                       focus:outline-none transition-all duration-300"
                required
              />
              <div class="absolute inset-y-0 left-4 flex items-center pointer-events-none
                          {currentFocus === 'confirmPassword' ? 'text-purple-500' : 'text-gray-400'}">
                <svg class="w-5 h-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                  <path d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"/>
                </svg>
              </div>
              <button
                type="button"
                on:click={() => showConfirmPassword = !showConfirmPassword}
                class="absolute inset-y-0 right-4 flex items-center text-gray-400 hover:text-gray-600"
              >
                {#if showConfirmPassword}
                  <svg class="w-5 h-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                    <path d="M13.875 18.825A10.05 10.05 0 0112 19c-4.478 0-8.268-2.943-9.543-7a9.97 9.97 0 011.563-3.029m5.858.908a3 3 0 114.243 4.243M9.878 9.878l4.242 4.242M9.88 9.88l-3.29-3.29m7.532 7.532l3.29 3.29M3 3l3.59 3.59m0 0A9.953 9.953 0 0112 5c4.478 0 8.268 2.943 9.543 7a10.025 10.025 0 01-4.132 5.411m0 0L21 21"/>
                  </svg>
                {:else}
                  <svg class="w-5 h-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"/>
                    <path d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z"/>
                  </svg>
                {/if}
              </button>
            </div>
            {#if confirmPassword && !passwordMatch}
              <p class="text-sm text-red-500">Passwords do not match</p>
            {/if}
          </div>

          <!-- Terms and Conditions -->
          <div class="space-y-4">
            <label class="flex items-center gap-3">
              <input
                type="checkbox"
                bind:checked={agreeToTerms}
                class="w-4 h-4 rounded border-gray-300 text-purple-600 focus:ring-purple-500"
              >
              <span class="text-sm text-gray-500">
                I agree to the
                <a href="/terms" class="text-purple-600 hover:text-purple-500">Terms and Conditions</a>
                and
                <a href="/privacy" class="text-purple-600 hover:text-purple-500">Privacy Policy</a>
              </span>
            </label>
          </div>

          <!-- Submit Button -->
          <button
            type="submit"
            class="w-full flex items-center justify-center gap-2 py-2 px-4 rounded-xl bg-black text-white font-medium
                   hover:bg-opacity-90 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-purple-500
                   transition-all duration-300 hover:-translate-y-0.5 relative overflow-hidden
                   disabled:opacity-50 disabled:cursor-not-allowed"
            disabled={loading || !agreeToTerms || !passwordMatch || passwordStrength < 75}
          >
            {#if loading}
              <div class="absolute inset-0 flex items-center justify-center bg-black">
                <div class="w-5 h-5 border-2 border-white border-t-transparent rounded-full animate-spin"></div>
              </div>
            {/if}
            <span class={loading ? 'opacity-0' : ''}>Create Account</span>
          </button>
        </form>

        <!-- Sign In Link -->
        <div class="text-center text-sm">
          <span class="text-gray-500">Already have an account?</span>
          <a href="/login" class="text-purple-600 hover:text-purple-500 font-medium"> Sign in</a>
        </div>
      </div>
    </div>
  </div>

  <style>
    @keyframes float {
      0%, 100% {
        transform: translateY(0);
      }
      50% {
        transform: translateY(-20px);
      }
    }

    :global(body) {
      background-color: rgb(249, 250, 251);
    }

    /* Custom scrollbar styles */
    :global(::-webkit-scrollbar) {
      width: 8px;
    }

    :global(::-webkit-scrollbar-track) {
      background: #f1f1f1;
      border-radius: 4px;
    }

    :global(::-webkit-scrollbar-thumb) {
      background: #888;
      border-radius: 4px;
    }

    :global(::-webkit-scrollbar-thumb:hover) {
      background: #555;
    }
  </style>
