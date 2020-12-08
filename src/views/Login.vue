<template>
  <div class="main">
    <!-- Sing in  Form -->
    <section class="sign-in">
      <div class="container">
        <div class="signin-content">
          <div class="signin-image">
            <figure>
              <img
                v-bind:src="'assets/img/signin-image.jpg'"
                alt="sing up image"
              />
            </figure>
            <!--<a href="Register.vue" class="signup-image-link">Create an account</a>-->
            <router-link to="/">Create an Account</router-link>
          </div>

          <div class="signin-form">
            <h2 class="form-title">Sign up</h2>
            <form
              class="login-form"
              id="login-form"
              v-on:submit.prevent="Login"
            >
              <div class="form-group">
                <label for="email"
                  ><i class="zmdi zmdi-account material-icons-name"></i
                ></label>
                <input
                  type="email"
                  name="email"
                  id="email"
                  v-model="email"
                  placeholder="Your Email"
                />
              </div>
              <div class="form-group">
                <label for="your_pass"><i class="zmdi zmdi-lock"></i></label>
                <input
                  type="password"
                  name="your_pass"
                  id="your_pass"
                  v-model="password"
                  placeholder="Password"
                />
              </div>
              <div class="form-group">
                <input
                  type="checkbox"
                  name="remember-me"
                  id="remember-me"
                  class="agree-term"
                />
                <label for="remember-me" class="label-agree-term"
                  ><span><span></span></span>Remember me</label
                >
              </div>
              <div class="form-group form-button">
                <input
                  type="submit"
                  name="signin"
                  id="signin"
                  class="form-submit"
                  value="Log in"
                />
              </div>
            </form>
            <!-- <div class="social-login">
              <span class="social-label">Or login with</span>
              <ul class="socials">
                <li>
                  <a href="#"
                    ><i class="display-flex-center zmdi zmdi-facebook"></i
                  ></a>
                </li>
                <li>
                  <a href="#"
                    ><i class="display-flex-center zmdi zmdi-twitter"></i
                  ></a>
                </li>
                <li>
                  <a href="#"
                    ><i class="display-flex-center zmdi zmdi-google"></i
                  ></a>
                </li>
              </ul>
            </div> -->
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    Login: function () {
      let email = this.email; //let itu variabel baru
      let password = this.password;
      this.$store
        .dispatch("login", { email, password })
        .then(() => this.$router.push("/home"))
        .catch((err) => console.log(err));
    },
  },
};
</script>
