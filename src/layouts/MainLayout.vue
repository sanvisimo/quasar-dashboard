<template>
  <q-layout view="lHh Lpr lFf" class="bg-grey-3">
    <q-header class="bg-transparent text-dark">
      <q-toolbar id="app-bar" style="height: 75px;">
        <q-btn
          dense
          rounded
          class="bg-white q-pa-xs"
          icon="mdi-dots-vertical"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title v-text="$route.name" />

        <q-space />

        <router-link to="/">
          <template v-slot="props">
            <q-btn v-bind="buttonProps(props)">
              <q-icon name="mdi-view-dashboard" size="20px" />
            </q-btn>
          </template>
        </router-link>

        <q-btn class="q-ml-sm" unelevated>
          <q-icon name="mdi-bell" size="20px">
            <q-badge
              color="red"
              floating
              :label="5"
              class="q-badge__notifications"
            />
          </q-icon>
          <q-menu
            anchor="bottom right"
            self="top right"
            transition="scale-transition"
          >
            <q-list :tile="false" nav>
              <q-item
                clickable
                v-for="(n, i) in notifications"
                :key="`item-${i}`"
              >
                <q-item-label v-text="n" />
              </q-item>
            </q-list>
          </q-menu>
        </q-btn>

        <router-link to="/users">
          <template v-slot="props">
            <q-btn v-bind="buttonProps(props)">
              <q-icon name="mdi-account" size="20px" />
            </q-btn>
          </template>
        </router-link>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      elevated
      content-class="drawer__admin text-white"
    >
      <q-list class="q-px-md">
        <q-item-label header class="text-white">
          <q-avatar size="40px" class="q-mr-md">
            <img src="https://cdn.quasar.dev/app-icons/icon-128x128.png" />
          </q-avatar>
          Admin
        </q-item-label>

        <q-separator color="grey-6" />
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from "components/EssentialLink";

export default {
  name: "MainLayout",

  components: {
    EssentialLink
  },

  data() {
    return {
      leftDrawerOpen: false,
      essentialLinks: [
        {
          title: "Barche",
          icon: "mdi-sailing",
          link: "/"
        },
        {
          title: "Utenti",
          icon: "mdi-account-supervisor",
          link: "/b"
        },
        {
          title: "Prenotazioni",
          icon: "mdi-calendar",
          link: "/c"
        }
      ],
      notifications: [
        "Mike John Responded to your email",
        "You have 5 new tasks",
        "You're now friends with Andrew",
        "Another Notification",
        "Another one"
      ]
    };
  },

  methods: {
    buttonProps({ href, route, isActive, isExactActive }) {
      const props = {
        class: "q-ml-md",
        type: "a",
        textColor: "grey-10",
        to: href,
        unelevated: true
      };

      if (isExactActive) {
        props.color = "grey-4";
      }

      return props;
    }
  }
};
</script>

<style lang="sass">
.drawer__admin
  background-image: url('/statics/login_background.jpg')
  background-size: cover

.q-badge__notifications
  border-radius: 50%
  width: 24px
  height: 24px
  border: 2px solid #fff
  padding: 0 6px
  font-size: 12px
  line-height: 24px
  top: -10px
  right: -12px
</style>
