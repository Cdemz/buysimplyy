<template>
  <div class="w-full h-lvh flex">
    <div class="side w-1/2 bg-[#F8EAFF] shrink-0 flex-col px-10 hidden lg:flex">
      <!-- lg:flex hidden -->
      <header class="h-16 w-full mb-auto mt-4">
        <img src="~@/assets/logo.png" alt="Team Achieve Logo" 
        class="h-full w-auto"
        srcset="">
      </header>
      <div class="body w-full h-auto grow-1 flex bg-transparent overflow-hidden rounded-xl my-5 justify-center">
        <img src="~@/assets/people.png" alt="Happy People" class="rounded-xl">
      </div>
      <div class="w-full flex flex-col mt-auto shrink-0 items-center py-4">
        <b class="font-bold text-[#622081]">Team Achieve</b>
        <span class="text-[#555]">Your perfect solution for funding your desires</span>
      </div>
  </div>
    <div class="side flex flex-col lg:w-1/2 w-full shrink-0 bg-white">
      <header class="h-24 mt-11 mb-3 lg:hidden mx-auto">
        <img src="~@/assets/logo.png" alt="Team Achieve Logo" 
        class="h-full w-auto"
        srcset="">
      </header>
      <div class="content mt-4 w-full flex flex-col items-center px-4">
        <!-- header texts -->
        <h3 class="text-[#622081] font-bold text-2xl md:text-2xl">Welcome Back</h3>
        <small class="text-[#555] text-center">Enter your email address and password to access your account.</small>
        <!-- inputs -->
        <div class="inputWrapper flex w-full flex-col relative pt-4">
          <span class="relative">Email Address <small class="text-lg text-[#FF0000]">*</small></span>
          <input class="border hover:border-2 border-gray-300 outline-none rounded-md p-2 my-1" type="email" name="" id="" placeholder="Enter your email" v-model="email">
          <span class="error text-xs text-red-500" v-if="emailError">{{ emailError }}</span>
        </div>
        <div class="inputWrapper flex w-full flex-col relative pt-4">
          <span class="relative">Password  <small class="text-lg text-[#FF0000]">*</small></span>
          <div class="input-line flex w-full h-10 border-gray-300 border hover:border-2 rounded-md overflow-hidden">
            <input class="outline-none w-full h-full px-2 " :type="showPassword? 'text' : 'password'" name="" id="" placeholder="Enter your password" v-model="password">
            <div class="h-10 w-10 flex pb-10 shrink-0 border-l border-gray-300 relative active:bg-gray-300" @click="showPassword = !showPassword">
              <img class="h-4 w-4 m-auto mt-3" src="~@/assets/open.png" alt="eyes open" v-if="showPassword">
              <img class="h-4 w-4 m-auto mt-3" src="~@/assets/closed.png" alt="eyes open" v-else>
            </div>
          </div>
          <span class="error text-xs text-red-500" v-if="passwordError">{{ passwordError }}</span>
        </div>
        <!-- remember and forget -->
        <div class="w-full mt-1 flex justify-between">
          <div class=" flex items-center">
            <input type="checkbox" name="" id="" class=" my-auto mr-2 w-4 h-4"> Remember me
          </div>
          <a href="#" class="text-[#622081]">Forgot Password?</a>
        </div>
        <!-- submission -->
        <button class="button w-full text-center rounded-md py-2 mt-6 font-bold" @click="validate()">Sign In</button>
        <div class="w-full text-center mt-2 text-[#555]">Don't have an account? <a href="#" class="text-[#622081] font-bold">Sign up</a></div>
      </div>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: "BuySimply",
  components: {
    // HelloWorld
  },
  data: () => ({
    email: '',
    emailError: '',
    password: '',
    passwordError: '',
    showPassword: false,
  }),
  methods: {
    validate(){
      const { email, password } = this;
      // validate with regex:
      if(!/^.+@.+\..+$/gi.test(email)){
        this.emailError = 'Please enter a valid email address.';
      }
      const hasSpecialChars = /[^A-z]/gi.test(password);
      const hasUpperCase = /[A-Z]/g.test(password);
      const hasLowerCase = /[a-z]/g.test(password);
      if(!(password.length>=8)){
        this.passwordError = 'Your password must be at least 8 digits long.';
      } else if (!(hasSpecialChars && hasUpperCase && hasLowerCase)){
        this.passwordError = 'Your password must contain uppercase, lowercase and special characters.'
      }
    }
  },
  watch: {
    password(){
      this.passwordError = '';
    },
    email(){
      this.emailError = '';
    }
  }
};
</script>

<style scoped>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.input-line:hover div{
  border-width: 0px 0px 0px 2px;
}
</style>
