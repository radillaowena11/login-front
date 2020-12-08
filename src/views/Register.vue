<template>
  <div class="main">
    <!-- Sign up form -->
    <section class="signup">
      <div class="container">
        <div class="signup-content">
          <div class="signup-form">
            <h2 class="form-title">Sign up</h2>
            <form
              class="register-form"
              id="register-form"
              v-on:submit.prevent="Register"
            >
              <div class="form-group">
                <label for="name"
                  ><i class="zmdi zmdi-account material-icons-name"></i
                ></label>
                <input
                  type="text"
                  name="name"
                  id="name"
                  v-model="name"
                  placeholder="Your Name"
                />
              </div>
              <div class="form-group">
                <label for="email"><i class="zmdi zmdi-email"></i></label>
                <input
                  type="email"
                  name="email"
                  id="email"
                  v-model="email"
                  placeholder="Your Email"
                />
              </div>
              <div class="form-group">
                <label for="pass"><i class="zmdi zmdi-lock"></i></label>
                <input
                  type="password"
                  name="pass"
                  id="pass"
                  v-model="password"
                  placeholder="Password"
                />
              </div>
              <div class="form-group">
                <label for="re-pass"
                  ><i class="zmdi zmdi-lock-outline"></i
                ></label>
                <input
                  type="password"
                  name="re_pass"
                  id="re_pass"
                  v-model="password_verify"
                  placeholder="Repeat your password"
                />
              </div>
              <div class="form-group">
                <input
                  type="checkbox"
                  name="agree-term"
                  id="agree-term"
                  v-model="agree"
                  class="agree-term"
                />
                <label for="agree-term" class="label-agree-term"
                  ><span><span></span></span>I agree all statements in
                  <a href="#" class="term-service">Terms of service</a></label
                >
              </div>
              <div class="form-group form-button">
                <input
                  type="submit"
                  name="signup"
                  id="signup"
                  class="form-submit"
                  value="Register"
                />
              </div>
            </form>
          </div>
          <div class="signup-image">
            <figure>
              <img
                v-bind:src="'assets/img/signup-image.jpg'"
                alt="sing up image"
              />
            </figure>
            <!--<a href="Login.vue" class="signup-image-link">I am already member</a>-->
            <router-link to="/login">Already have account? Signin</router-link>
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
      name: "",
      email: "",
      password: "",
      password_verify: "",
    };
  },
  methods: {
    Register: function () {
      let conf = { headers: { Authorization: "Bearer " + this.key } };
      this.$bvToast.show("loadingToast");
      let form = new FormData();
      form.append("id", this.id);
      form.append("name", this.name);
      form.append("email", this.email);
      form.append("password", this.password);
      form.append("password_confirmation", this.password_verify);
      this.axios
        .post("http://localhost:8000/api/register", form, conf)
        .then(() => this.$router.push("/login"))
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>