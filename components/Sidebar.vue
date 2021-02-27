<template>
  <div>
    <v-navigation-drawer
      :value="true"
      :mini-variant="!drawer"
      :clipped="clipped"
      :absolute="!drawer"
      app
    >
      <perfect-scrollbar v-if="drawer">
        <v-list dense>
          <div v-for="item in menuItems" :key="item.title">
            <v-list-group
              v-if="item.hasOwnProperty('subItems')"
              v-model="item.active"
              :prepend-icon="item.icon"
              no-action
            >
              <template #activator>
                <v-list-item-content>
                  <v-list-item-title
                    v-text="$t(item.label)"
                  ></v-list-item-title>
                </v-list-item-content>
              </template>

              <v-list-item
                v-for="child in item.subItems"
                :key="child.title"
                :to="child.link"
              >
                <v-list-item-content>
                  <v-list-item-title
                    v-text="$t(child.label)"
                  ></v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-list-group>
            <v-subheader v-else-if="item.isTitle">{{
              $t(item.label)
            }}</v-subheader>
            <v-list-item v-else-if="!item.isTitle" :to="item.link">
              <v-list-item-icon>
                <v-icon v-text="item.icon"></v-icon>
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title v-text="$t(item.label)"></v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </div>
        </v-list>
      </perfect-scrollbar>
      <perfect-scrollbar v-else>
        <v-menu
          v-for="(category, index) in $options.filters.handleItems(menuItems)"
          :key="index"
          :open-on-click="category.hasOwnProperty('subItems') ? true : false"
          offset-x
        >
          <template #activator="{ attrs, on }">
            <v-btn v-bind="attrs" :to="category.link" v-on="on">
              <v-icon> {{ category.icon }}</v-icon>
            </v-btn>
          </template>

          <v-list>
            <v-list-item
              v-for="(item, index) in category.subItems"
              :key="index"
              :to="item.link"
            >
              <v-list-item-title v-text="$t(item.label)"></v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
      </perfect-scrollbar>
    </v-navigation-drawer>
  </div>
</template>

<script>
import { menuItems } from '@/api/menu'

export default {
  name: 'Sidebar',
  filters: {
    handleItems(items) {
      return items.filter((item) => {
        return (
          // eslint-disable-next-line no-prototype-builtins
          item.hasOwnProperty('isTitle') === false ||
          // eslint-disable-next-line no-prototype-builtins
          item.hasOwnProperty('subItems') === true
        )
      })
    },
  },
  data() {
    return {
      menuItems,
      clipped: true,
      items: [
        {
          action: 'mdi-ticket',
          items: [{ title: 'List Item' }],
          title: 'Attractions',
        },
        {
          action: 'mdi-silverware-fork-knife',
          active: true,
          items: [
            { title: 'Breakfast & brunch' },
            { title: 'New American' },
            { title: 'Sushi' },
          ],
          title: 'Dining',
        },
        {
          action: 'mdi-school',
          items: [{ title: 'List Item' }],
          title: 'Education',
        },
        {
          action: 'mdi-run',
          items: [{ title: 'List Item' }],
          title: 'Family',
        },
        {
          action: 'mdi-bottle-tonic-plus',
          items: [{ title: 'List Item' }],
          title: 'Health',
        },
        {
          action: 'mdi-content-cut',
          items: [{ title: 'List Item' }],
          title: 'Office',
        },
        {
          action: 'mdi-tag',
          items: [{ title: 'List Item' }],
          title: 'Promotions',
        },
      ],
      miniVariant: false,
      rightDrawer: false,
      title: 'Vuetify.js',
      fav: true,
      menu: false,
      message: false,
      hints: true,
    }
  },
  computed: {
    drawer() {
      return this.$store.getters['layout/drawer']
    },
    fixed() {
      return this.$store.getters['layout/fixed']
    },
  },
  methods: {},
}
</script>

<style lang="scss">
.ps {
  height: calc(100% - 1rem);
}
.logo-container {
  display: flex;
  justify-content: center;
  vertical-align: center;
  max-width: 240px;
}
.logo-img {
  width: 60%;
}
.logo-img__mini {
  width: 50%;
}

.flag {
  color: #fff;
  margin: 0 10px 0 10px;
}

.drawer-height {
  height: 100%;
}
</style>
