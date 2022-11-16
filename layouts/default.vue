<template lang="pug">
v-app
  v-row
    v-col(cols="1")
      v-row.text-center.mt-7
        v-col(cols="12")
          v-app-bar-nav-icon.text-center.d-md-none(@click="drawer = true")
          

      v-row.text-center.d-none.d-md-flex
        v-col(cols="12")
          v-hover(v-for="(item, i) in dataButton" :key="i" v-slot="{ hover }")
            v-avatar.mx-2(:color="item.color" elevation="2" :elevation="hover ? 12 : 2" size="24")
              v-icon(v-if="hover" color="white") {{item.icon}}
              v-icon(v-else color="white")
        v-col(cols="12")    
          v-list(flat)
            v-list-item-group( color="primary")
              v-list-item(v-for="(item, i) in items" :key="i")
                v-icon.mx-auto.my-8(color="primary" size="30") {{item.icon}}

    v-col(cols="11" height="64px")

      v-row.mt-6
        v-col(cols="11")
          v-text-field.boxInput.mx-auto(label="Search" prepend-inner-icon="mdi-magnify" filled rounded dense)
        v-col.text-center(cols="1")
          v-avatar( color="primary" size="56")
            img(src="https://cdn.vuetifyjs.com/images/john.jpg" alt="John")

      v-row
        v-col(cols="12")
          v-main
            v-container
              Nuxt

  v-navigation-drawer(v-model="drawer" absolute temporary)
    v-list(nav dense) 
      v-list-item-group(v-model="group" active-class="deep-purple--text text--accent-4")

        v-row.mt-6
          v-col.text-center(cols="12")
            v-hover(v-for="(item, i) in dataButton" :key="i" v-slot="{ hover }")
              v-avatar.mx-2(:color="item.color" elevation="2" :elevation="hover ? 12 : 2" size="24")
                v-icon(v-if="hover" color="white") {{item.icon}}
                v-icon(v-else color="white")
              
        v-row.mx-auto    
          v-col.mx-auto(cols="12")
            v-list(flat)
              v-list-item-group( color="primary")
                v-list-item(v-for="(item, i) in items" :key="i")
                  v-icon.mx-auto.my-8(color="primary" size="30") {{item.icon}}

</template>

<script>
export default {
  name: 'DefaultLayout',
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      dataButton: [
        {
          icon: 'mdi-close',
          color: 'red',
        },
        {
          icon: 'mdi-minus',
          color: 'yellow',
        },
        {
          icon: 'mdi-garage-open-variant',
          color: 'green',
        }
      ],
      items: [
        {
          icon: 'mdi-home',
          title: ' ',
          to: '/'
        },
        {
          icon: 'mdi-chat-outline',
          title: ' ',
          to: '/inspire'
        },
        {
          icon: 'mdi-clock-outline',
          title: ' ',
          to: '/'
        },
        {
          icon: 'mdi-account-outline',
          title: ' ',
          to: '/'
        },
        {
          icon: 'mdi-cog-outline',
          title: ' ',
          to: '/'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  }
}
</script>

<style>
.boxInput{
  width: 400px;
}
.boxList {
  width: 200px;
}
</style>
