<template>
  <div>
    <v-layout column>
      <v-flex xs6 offset-xs3>
        <div class="white elevation-2">
          <v-toolbar flat dense class="cyan" dark>
            <v-toolbar-title>Register</v-toolbar-title>
          </v-toolbar>
          <div class="pl-4 pr-4 pt-2 pb-2">
            <form
              name="tab-tracker-form"
              autocomplete="off">
              <v-text-field
                label="email"
                v-model="email"
              ></v-text-field>
             <br/>
              <v-text-field
                label="password"
                type="password"
                v-model="password"
                autocomplete="new-password"
              ></v-text-field>
              <br/>
              <div class="error" v-html="error"/>
              <br/>
              <v-btn
                class="cyan"
                dark
                @click="register"
              >Register</v-btn>
            </form>
          </div>
        </div>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import AuthentificationService from '@/services/AuthentificationService'
export default {
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async register () {
      try {
        await AuthentificationService.register({
          email: this.email,
          password: this.password
        })
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>

<style scoped>
.error {
  color: white;
}

</style>
