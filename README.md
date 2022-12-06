# Nuxt3-Matomo
Tutorial and code to add Matomo to a nuxt 3 project

##1 add Vue Matomo
in your terminal enter the following command
```
npm install --save vue-matomo
```

##2 add Nuxt plugin
Add file your-project/**plugin/super-matomo-plugin.js** to the project with this :
```
import { defineNuxtPlugin } from '#app'
import VueMatomo from 'vue-matomo'

export default defineNuxtPlugin((nuxtApp) => {
  nuxtApp.vueApp.use(VueMatomo, {
    host: 'https://your-matomo-domain-address.com',
    siteId: 1, 
    // Enables automatically registering pageviews on the router
    router: nuxtApp.$router,
    enableLinkTracking: true,
    requireConsent: false,
    trackInitialView: true,
    disableCookies: true,
    requireCookieConsent: false,
  })
})
```

##3 register your plugin to your Nuxt app 
file **nuxt.config.ts**
```
export default ({
    app: {
   head: {
      title: 'Bonjour', 
      htmlAttrs: {
          lang: 'fr'
      },
      meta: [
          { charset: 'utf-8' }
      ]
    }}, 

  plugins: [
    { src: '~/plugins/matomo-ana.js', ssr: false }
  ],

})
```

That it

