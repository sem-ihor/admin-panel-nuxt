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
              <!--              <img src="@/static/Logo.png" alt="Vue Vuetify Admin Logo" />-->
              <p>
                Enter your email address and password to access admin panel.
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
                autocomplete="current-password"
              />
            </v-form>
          </v-card-text>
          <v-card-actions>
            <Localization :option="'grey'" />
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
            <v-btn color="primary" outlined to="/account/register">
              {{ $t('account.register.text') }}
            </v-btn>
            <v-btn color="primary" :loading="loading" @click="login">
              {{ $t('account.login.text') }}
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Localization from '../../components/widgets/Localization'
export default {
  name: 'Login',
  components: { Localization },
  layout: 'auth',
  data: () => ({
    loading: false,
    model: {
      email: 'admin@vvadmin.io',
      password: '123456',
    },
  }),
  methods: {
    async login() {
      /* await this.$store.dispatch('LoginByEmail', {
        email: this.model.email,
        password: this.model.password,
      }) */
      await this.$router.push(this.$route.query.redirect || '/')
    },
    setUserToLogin(id) {
      /*  if (id) {
        this.model.email = userAdmin.email
        this.model.password = userAdmin.password
      } else {
        this.model.email = userEditor.email
        this.model.password = userEditor.password
      } */
    },
  },
}
</script>
