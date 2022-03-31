# Achievement 8 - Async Fetch Nuxt 
## [Live Netlify Site](https://extraordinary-sunshine-e41cf0.netlify.app/)
 - Using the [Hyrule Compendium API](https://gadhagod.github.io/Hyrule-Compendium-API/#/) 

Troubleshooting:
 - Had trouble navigating through the API since it comes out as a jumbled mess when fetched and visualized on the template.
    - Used Postman API = Amazing
 - Tried to wrap the `usefetch` command in a function. Vue did not like that very much.
    - Ran across the `refreshNuxtData` on the the [Data fetching page](https://v3.nuxtjs.org/docs/usage/data-fetching/#useasyncdata)
      - Tried using the `refreshNuxtData` command but I had trouble making the **fetching data refresh** 
```
const { data: zelda } = await useFetch('https://botw-compendium.herokuapp.com/api/v2')
console.log (zelda.value.data.monsters[0].name)
const refresh = () => refreshNuxtData(‘zelda’)
```

  - Nothing happened. probably since there was no `key:id` assigned to **“data: zelda”**
  - I realized that the instructions said that *(When it's not specified, all useAsyncData and useFetch will be refetched.)*
  - Finished with:
```
const { data: zelda } = await useFetch('https://botw-compendium.herokuapp.com/api/v2')
console.log (zelda.value.data.monsters[0].name)
const refresh = () => refreshNuxtData() // leave this blank if your fetch has no key:id or else it won't work
```

