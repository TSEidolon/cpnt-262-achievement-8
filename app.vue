<template>
  <div>
    <header>
      <h1> The Legend of Zelda: Breath of The Wild - Random Monster Generator</h1>
    </header>
    <body>
      <button  @click="refresh"> Generate New Monster</button>
      <div class="card-item">
        <h1> {{ zelda.data.monsters[0].name }} </h1>
        <img :src ="zelda.data.monsters[0].image" alt="">
        <p> {{ zelda.data.monsters[0].description }} </p>
        
        <p> Drops: </p>
        <ul>
          <li v-for="x in zelda.data.monsters[0].drops" :key="x">
            {{x}}
          </li>
        </ul>

        <p> Common Locations: </p>
        <ul>
          <li v-for="x in zelda.data.monsters[0].common_locations" :key="x">
            {{x}}
          </li>
        </ul>
      </div>
    </body>
  </div>
</template>

<script setup>


const { data: zelda } = await useFetch('https://botw-compendium.herokuapp.com/api/v2')
console.log (zelda.value.data.monsters[0].name)

const refresh = () => refreshNuxtData() // leave this blank if your fetch has no key:id or else it won't work

</script>