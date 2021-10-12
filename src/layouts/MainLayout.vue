<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="bg-primary">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          Theme Switcher
        </q-toolbar-title>

        <div></div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      bordered
    >
      <q-list>
        <!-- <q-item-label
          header
          class="text-grey-8"
        >
          Essential Links
        </q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        /> -->
    <q-select
        v-model="theme"
        filled
        label="Theme Switcher"
        :options="options"
      >
        <template #option="scope">
          <q-item v-bind="scope.itemProps">
            <q-item-section avatar>
              <q-icon :name="scope.opt.icon" />
            </q-item-section>
            <q-item-section>
              <q-item-label v-text="scope.opt.label" />
              <q-item-label caption>{{ scope.opt.description }}</q-item-label>
            </q-item-section>
          </q-item>
        </template>
      </q-select>
      <q-toggle
        v-model="$q.dark.mode"
        label="Dark Mode"
        @update:model-value="$q.dark.toggle()"
      />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script lang="ts">
// import EssentialLink from 'components/EssentialLink.vue';
import { defineComponent, ref, watch } from 'vue';

interface ThemeOption {
  label?: string
  value?: string
  description?: string
  icon?: string
  color?: string
}

const linksList = [
  {
    title: 'Docs',
    caption: 'quasar.dev',
    icon: 'school',
    link: 'https://quasar.dev'
  },
  {
    title: 'Github',
    caption: 'github.com/quasarframework',
    icon: 'code',
    link: 'https://github.com/quasarframework'
  },
  {
    title: 'Discord Chat Channel',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: 'https://chat.quasar.dev'
  },
  {
    title: 'Forum',
    caption: 'forum.quasar.dev',
    icon: 'record_voice_over',
    link: 'https://forum.quasar.dev'
  },
  {
    title: 'Twitter',
    caption: '@quasarframework',
    icon: 'rss_feed',
    link: 'https://twitter.quasar.dev'
  },
  {
    title: 'Facebook',
    caption: '@QuasarFramework',
    icon: 'public',
    link: 'https://facebook.quasar.dev'
  },
  {
    title: 'Quasar Awesome',
    caption: 'Community Quasar projects',
    icon: 'favorite',
    link: 'https://awesome.quasar.dev'
  }
];

export default defineComponent({
  name: 'MainLayout',

  components: {
  },

  setup () {
    const leftDrawerOpen = ref(false)
    const theme = ref<ThemeOption>({});

    watch(theme, (newOption: ThemeOption) => {
      if (newOption) {
        document.body.setAttribute('data-theme', newOption.value || 'blue')
      }
    });

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      options: [
        {
          label: 'Bootstrap 5',
          value: 'bootstrap',
          description: 'Bootstrap v5 theme',
          icon: 'palette',
          color: 'primary'
        },
        {
          label: 'Cape Palliser',
          value: 'cape-palliser',
          description: 'Cape Palliser is a saturated light warm orange theme',
          icon: 'palette',
          color: 'primary'
        },
        {
          label: 'Polo Blue',
          value: 'polo-blue',
          description: 'Polo blue is a unsaturated very light cold azure theme',
          icon: 'palette',
          color: 'primary'
        },
        {
          label: 'Quasar',
          value: 'quasar',
          description: 'Quasar default theme',
          icon: 'palette',
          color: 'primary'
        }
      ],
      theme,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  },

  created() {
    this.theme = {
      label: 'Bootstrap',
      value: 'bootstrap',
      icon: 'las la-square',
      color: 'primary'
    }
  }
})
</script>
