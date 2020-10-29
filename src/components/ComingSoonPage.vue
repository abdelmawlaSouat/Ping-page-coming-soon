<template>
  <div
    class="coming-page d-flex flex-column align-center"
  >
    <v-img
      :src="require('@/assets/logo.svg')"
      alt="Logo"
      width="100"
    ></v-img>
    <h1 class="font-weight-regular grey-color text-xs-h5 text-sm-h3 mt-10">
      We are launching <strong class="dark-blue-color">soon!</strong>
    </h1>
    <h2 class="font-weight-regular text-subtitle-1 mt-2 mb-4">Subscribe and get notified</h2>
    <v-form
      class="d-flex flex-column flex-sm-row mt-4"
      ref="form"
      v-model="valid"
    >
      <v-text-field
        placeholder="Your email adress"
        :rules="[rules.required, rules.email]"
        v-model="email"
        :success-messages="valid ? successMsg : ''"
        type="email"
        outlined rounded
      ></v-text-field>
      <v-btn
        class="blue-bg-color ml-2 px-10 py-6 mb-5 mb-sm-0"
        @click="sendEmail()"
        dark
        rounded
      >
        <span v-if="!loading" >Notify Me</span>
        <v-progress-circular
          v-else
          color="white"
          indeterminate
        ></v-progress-circular>
      </v-btn>
    </v-form>
    <v-img
      :src="require('@/assets/illustration-dashboard.png')"
      alt="Dashboard"
      width="600"
    ></v-img>
    <div class="social-medias mt-10">
      <v-btn fab small text class="blue-color mx-2">
        <v-icon>mdi-facebook</v-icon>
      </v-btn>
      <v-btn fab small text class="blue-color mx-2">
        <v-icon>mdi-twitter</v-icon>
      </v-btn>
      <v-btn fab small text class="blue-color mx-2">
        <v-icon>mdi-instagram</v-icon>
      </v-btn>
    </div>
    <v-footer class="text-center grey-color mt-5">
        © Copyright Ping. All rights reserved
    </v-footer>
  </div>
</template>

<script>
export default {
  name: 'ComingSoonPage',
  data () {
    return {
      email: '',
      valid: false,
      successMsg: 'Email valid',
      loader: null,
      loading: false,
      rules: {
        required: (value) => !!value || 'Email Required !',
        email: (value) => {
          const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
          return pattern.test(value) || 'Please provide a valid email address'
        }
      }
    }
  },
  methods: {
    sendEmail () {
      this.$refs.form.validate()
      if (this.valid && this.email) {
        this.loader = 'loading'
        this.successMsg = 'Mail Sent !'
      }
    }
  },
  watch: {
    loader () {
      const l = this.loader
      this[l] = !this[l]
      setTimeout(() => (this[l] = false), 500)
      this.loader = null
    }
  }
}
</script>

<style scoped>
.blue-color {
  color: hsl(223, 87%, 63%) !important;
}
.grey-color {
  color: hsl(0, 0%, 59%) !important;
}
.dark-blue-color {
  color: hsl(209, 33%, 12%) !important;
}
.blue-bg-color {
  background-color: hsl(223, 87%, 63%) !important;
}
</style>
