<template>
  <q-layout>
    <q-page-container>
      <q-page class="q-pa-md" id="q-pa-md-pages">
        <!-- Logo and Registration Text -->
        <div class="header-container">
          <div class="logo-box">
            <h3>LOGO</h3>
            <span class="register-text">Free Registration</span>
          </div>
        </div>

        <!-- Stepper -->
        <div class="stepper-wrapper">
          <div class="stepper-item completed">
            <div class="step-counter">1</div>
          </div>
          <div class="stepper-item completed">
            <div class="step-counter">2</div>
          </div>
          <div class="stepper-item completed custom-margin">
            <div class="step-counter">3</div>
          </div>
        </div>

        <!-- Registration Form -->
        <div class="form-container">
          <!-- Social icon -->
          <div class="social-login">
            <div class="form-header-container">
              <p class="continue-text">Continue With</p>
              <div class="social-icons">
                <a
                  href="https://www.facebook.com"
                  target="_blank"
                  aria-label="Login with Facebook"
                >
                  <img
                    src="~/assets/photos/facebook.png"
                    alt="Facebook"
                    class="social-icon"
                  />
                </a>
                <a
                  href="https://www.google.com"
                  target="_blank"
                  aria-label="Login with Google"
                >
                  <img
                    src="~/assets/photos/google.svg"
                    alt="Google"
                    class="social-icon"
                  />
                </a>
              </div>
              <div class="separator">
                <hr />
                <span>or</span>
                <hr />
              </div>
            </div>
            <ValidationObserver ref="observer" v-slot="{ invalid }">
              <q-form @submit.prevent="handleSubmit">
                <div class="row form-inputs-container q-col-gutter-md">
                  <div class="col-12 col-sm-6">
                    <label class="label">Username</label>
                    <ValidationProvider
                      name="Username"
                      rules="required"
                      v-slot="{ errors }"
                    >
                      <q-input
                        filled
                        dark
                        v-model="username"
                        placeholder="Please enter username."
                        :error="errors[0]"
                      />
                    </ValidationProvider>
                  </div>
                  <div class="col-12 col-sm-6">
                    <label class="label">Password</label>
                    <ValidationProvider
                      name="Password"
                      rules="required"
                      v-slot="{ errors }"
                    >
                      <q-input
                        filled
                        dark
                        v-model="password"
                        type="password"
                        placeholder="Please enter password."
                        :error="errors[0]"
                      />
                    </ValidationProvider>
                  </div>
                  <div class="col-12 col-sm-6">
                    <label class="label">Confirm Password</label>
                    <ValidationProvider
                      name="Confirm Password"
                      rules="required"
                      v-slot="{ errors }"
                    >
                      <q-input
                        filled
                        dark
                        v-model="confirmPassword"
                        type="password"
                        placeholder="Please confirm your password."
                        :error="errors[0]"
                      />
                    </ValidationProvider>
                  </div>
                  <div class="col-12 col-sm-6">
                    <label class="label">Mobile Number</label>
                    <ValidationProvider
                      name="Mobile Number"
                      rules="required|numeric"
                      v-slot="{ errors }"
                    >
                      <q-input
                        filled
                        dark
                        v-model="mobile"
                        type="tel"
                        placeholder="Please enter mobile number."
                        :error="errors[0]"
                        @input="validateMobile"
                      />
                    </ValidationProvider>
                  </div>

                  <div class="col-12 col-sm-6">
                    <label class="label">E-mail Address</label>
                    <ValidationProvider
                      name="E-mail Address"
                      rules="required|email"
                      v-slot="{ errors }"
                    >
                      <q-input
                        filled
                        dark
                        v-model="email"
                        placeholder="Please enter e-mail address."
                        :error="errors[0]"
                      />
                    </ValidationProvider>
                  </div>
                  <div class="col-12 col-sm-6">
                    <label class="label">Identity No</label>
                    <ValidationProvider
                      name="Identity No"
                      rules="required"
                      v-slot="{ errors }"
                    >
                      <q-input
                        filled
                        dark
                        v-model="identity"
                        placeholder="Please enter correct ID number."
                        :error="errors[0]"
                      />
                    </ValidationProvider>
                  </div>
                  <div class="col-12 col-sm-6">
                    <label class="label">Referral</label>
                    <ValidationProvider
                      name="Referral"
                      rules="required"
                      v-slot="{ errors }"
                    >
                      <q-input
                        filled
                        dark
                        v-model="referral"
                        placeholder="Please enter referral."
                        :error="errors[0]"
                      />
                    </ValidationProvider>
                  </div>
                  <div class="col-12 col-sm-6">
                    <div class="flex justify-end items-end">
                      <div style="width: 65%">
                        <label
                          for=""
                          class="input-title text-white"
                          style="white-space: nowrap"
                          >Verification Code</label
                        >
                        <ValidationProvider
                          name="Verification Code"
                          rules="required"
                          v-slot="{ errors }"
                        >
                          <q-input
                            class="input-fields"
                            filled
                            placeholder="Verification Code."
                            style="
                              color: white !important;
                              border-radius: 5px 0 0 5px;
                              background: #262626;
                            "
                            v-model="verificationCode"
                            :error="errors[0]"
                          />
                        </ValidationProvider>
                      </div>

                      <div
                        style="
                          width: 35%;
                          height: 60px;
                          background: #ffff;
                          border-radius: 0 5px 5px 0;
                          display: flex;
                          align-items: center;
                          justify-content: center;
                        "
                      >
                        <span class="text-red" style="font-size: 1.3rem"
                          >9999</span
                        >
                      </div>
                    </div>
                  </div>
                  <div class="col-12 flex justify-center items-center">
                    <ValidationProvider
                      name="Agreement"
                      rules="required|accepted"
                      v-slot="{ errors }"
                    >
                      <q-checkbox v-model="val" style="color: white" />
                      <span style="color: aliceblue">I agree.</span>
                      <a style="color: rgba(216, 158, 48, 1)"
                        >OCMS Terms & Condition</a
                      >
                    </ValidationProvider>
                  </div>
                  <div class="col-12 flex justify-center items-center">
                    <q-btn type="submit" label="Register" />
                  </div>
                </div>
              </q-form>
            </ValidationObserver>
          </div>
        </div>
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  data() {
    return {
      step: "1",
      username: "",
      password: "",
      confirmPassword: "",
      mobile: "",
      email: "",
      identity: "",
      referral: "",
      verificationCode: "",
      val: false,
    };
  },
  methods: {
    nextStep() {
      console.log(`Current step: ${this.step}`);
      if (this.step === "1") {
        this.step = "2";
      } else {
        this.step = "1";
      }
    },
    handleSubmit() {
      // Perform form validation here
      if (
        !this.username ||
        !this.password ||
        !this.confirmPassword ||
        !this.mobile ||
        !this.email ||
        !this.identity ||
        !this.verificationCode ||
        !this.val
      ) {
        alert("Please fill all the required fields and agree to the terms.");
        return;
      }

      if (this.password !== this.confirmPassword) {
        alert("Passwords do not match.");
        return;
      }

      // If validation passes, proceed with the registration
      console.log("Form submitted with data:", {
        username: this.username,
        password: this.password,
        mobile: this.mobile,
        email: this.email,
        identity: this.identity,
        referral: this.referral,
        verificationCode: this.verificationCode,
      });
      // Example: Proceed to the next step
      this.nextStep();
    },
  },
};
</script>

<style>
html,
body {
  background: linear-gradient(
    0deg,
    rgba(151, 42, 177, 1) 0%,
    rgba(28, 58, 112, 1) 80%,
    rgba(8, 24, 50, 1) 100%
  );
}

/* LOGO BOX */
.header-container .logo-box h3 {
  font-weight: 700;
  background-color: rgb(27, 26, 26);
  width: 144px;
  height: 50px;
}

/* LOGO TEXT */
.logo-box {
  color: rgba(255, 255, 0, 1);
  font-family: Inter;
  display: flex;
  justify-content: center;
  width: 100%;
  flex-direction: column;
  align-items: center;
}

/* FORM FIELD */
.form-container {
  width: 760px;
  height: 831px;
  background: black;
  border: solid 2px #ffcc00;
  border-radius: 15px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: column;
  padding: 42px 47px 42px 47px;
}

/* Text for free register */
.register-text {
  font-family: Inter;
  font-size: 40px;
  font-weight: 700;
  line-height: 60px;
  text-align: center;
  color: rgba(255, 255, 255, 1);
}

/* INPUT ALL FIELD WIDTH */
.q-form {
  width: 735px;
}

/* INPUT ALL BACKGROUND */
.q-field__inner {
  background: rgb(48, 47, 47);
  border-radius: 5px;
}

/* STEPPER */
.stepper-wrapper {
  margin-top: 20px;
  width: 50%;
  width: 800px;
  height: 70px;
  gap: 0px;
  opacity: 0px;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
}

.stepper-item {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  flex: 1;
}

.stepper-item .step-counter {
  position: relative;
  z-index: 3;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: #ccc;
  margin-bottom: 5px;
  color: black;
}

.stepper-item.active {
  font-weight: bold;
}

.stepper-item.completed .step-counter {
  background-color: black;
  color: white;
}

.stepper-item.completed::after {
  position: absolute;
  content: "";
  border-bottom: 3px solid #859184;
  width: 100%;
  top: 20px;
  left: 50%;
  z-index: 2;
}

.stepper-item:first-child::before {
  content: none;
}

.stepper-item:last-child::after {
  content: none;
}

.stepper-item:hover .step-counter {
  background: rgba(235, 160, 19, 1);
  transform: scale(1.5);
  /* Zoom in effect */
  transition: background-color 0.3s, transform 0.3s;
  /* Smooth transition */
}

.stepper-item:hover::before,
.stepper-item:hover::after {
  background: rgba(235, 160, 19, 1);
}

.q-stepper {
  background: none !important;
  border: none !important;
  box-shadow: none !important;
  width: 600px;
}

.q-stepper__header {
  border-bottom: none !important;
}

.q-stepper__header .q-stepper__step {
  box-shadow: none !important;
  border: none !important;
}

.q-page-container {
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: center;
}

.label {
  color: aliceblue;
}

.q-btn {
  display: flex;
  justify-content: center;
  background: rgba(187, 127, 15, 1);
  border-radius: 50px;
}
.q-input {
  width: 100%;
  height: 60px;
}

/* Social Login Section */
.social-login {
  font-size: 15px;
}
.continue-text {
  text-align: center;
}
.social-login {
  color: rgb(255, 255, 255);
}

.social-icons {
  display: flex;
  gap: 30px;
  display: flex;
  justify-content: center;
}

.social-icons a img {
  width: 50px;
  height: 50px;
}

.separator {
  display: flex;
  align-items: center;
  text-align: center;
}

.separator hr {
  flex: 1;
  border: 0;
  border-top: 1px solid rgb(133, 130, 130);
  margin: 10px;
}

.separator span {
  margin: 0 20px;
  color: white;
}

/* checkbox */
.custom-position {
  position: relative;
  top: 50px;
  width: 160px;
  height: 54px;
}

.form-header-container {
  height: 152px;
}
.form-inputs-container {
  padding-left: 20px;
  padding-right: 20px;
}

.q-checkbox__bg {
  background: white;
}

#q-pa-md-pages {
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: center;
}

.q-field__native,
.q-field__input {
  color: white;
}

@media only screen and (max-width: 767px) {
  .stepper-wrapper {
    width: 95%;
  }
  .q-form {
    width: 355px;
  }
  .form-container {
    width: 355px !important;
    height: 1327px;
  }
  .example {
    font-size: 14px;
    padding: 10px;
  }

  .sidebar {
    display: none;
  }

  .container {
    flex-direction: column;
  }
}
</style>
