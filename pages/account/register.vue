<template>
  <v-container class="container--fluid fill-height grey lighten-5">
    <v-row no-gutters align="center" justify="center">
      <v-col cols="12" sm="8" md="4" lg="4">
        <v-card class="elevation-5 pa-3">
          <v-card-text>
            <div class="layout column align-center">
              <v-img
                :src="require('@/static/Logo.png')"
                alt="Онлайн школа"
                class="mb-10"
              />
              <p class="text-center my-4">
                Don't have an account? Create your own account, it takes less
                than a minute
              </p>
            </div>
            <v-form>
              <v-text-field
                v-model="model.email"
                append-icon="mdi-account"
                name="email"
                :label="$t('login.email')"
                type="email"
                required
                autocomplete="username"
              />
              <v-text-field
                v-model="model.password"
                append-icon="mdi-lock"
                name="password"
                :label="$t('login.password')"
                type="password"
                required
                autocomplete="new-password"
              />
              <v-text-field
                v-model="model.confirm"
                append-icon="mdi-lock"
                name="confirm"
                :label="$t('login.confirm')"
                type="password"
                required
                autocomplete="new-password"
              />
            </v-form>
          </v-card-text>
          <v-card-actions>
            <localization />
            <v-btn icon>
              <v-icon color="blue"> mdi-facebook </v-icon>
            </v-btn>
            <v-btn icon>
              <v-icon color="red"> mdi-google </v-icon>
            </v-btn>
            <v-btn icon>
              <v-icon color="light-blue"> mdi-twitter </v-icon>
            </v-btn>
            <v-spacer />
            <v-btn color="primary" outlined to="/account/login">
              {{ $t('account.login.text') }}
            </v-btn>
            <v-btn color="primary" :loading="loading" @click="login">
              {{ $t('account.register.text') }}
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'Register',
  layout: 'auth',
  data: () => ({
    loading: false,
    model: {
      email: 'admin@vvadmin.io',
      password: 'password',
      confirm: 'password',
    },
  }),
  methods: {
    login() {
      this.loading = true
      setTimeout(() => {
        this.$router.push('/')
      }, 1000)
    },
  },
}
</script>
